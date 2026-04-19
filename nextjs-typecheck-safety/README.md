# Next.js Type-Check Safety

**A Claude skill that keeps `tsc --noEmit` from bricking the running `next dev` server.**

---

## The problem this solves

On Next.js 14 (and 15 without care), a simple workflow breaks the dev server:

1. You rename a folder under `app/` (e.g. `organizations/` → `clients/`) and `git mv` it.
2. You run `npx tsc --noEmit`. It fails because `.next/types/app/**/*.ts` still contains auto-generated declarations referencing the old folder path.
3. You reach for `rm -rf .next` to clear the stale types. TSC passes.
4. **Your browser now shows an unstyled page.** The running `next dev` process is serving 404s for `_next/static/css/*` because the compiled CSS manifest also lived in `.next/`.

Typical symptoms:
- Tailwind styles disappear entirely, page renders as black Times-New-Roman text on white
- `HTTP 200` on the route but no CSS
- Requires a full `next dev` restart to recover

## The fix (takes 30 seconds)

Stop asking `tsc` to type-check files it can't regenerate. Two tiny changes:

### `frontend/tsconfig.json`

```diff
-  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
-  "exclude": ["node_modules"]
+  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx"],
+  "exclude": ["node_modules", ".next"]
```

### `frontend/package.json`

```diff
   "scripts": {
     "dev": "next dev",
     "build": "next build",
     "start": "next start",
     "lint": "next lint",
+    "typecheck": "tsc --noEmit",
     "test:e2e": "playwright test"
   }
```

From now on run **`npm run typecheck`**. It's immune to `.next/` state because `.next/` is excluded from the TS project.

## What you lose and what you keep

| | Before | After |
|---|---|---|
| IDE type help on route params / searchParams | Yes (via Next TS plugin) | **Yes** (plugin still works) |
| `tsc --noEmit` catches wrong route-handler signatures | Yes, but flaky | No |
| `next build` catches route-handler type errors in CI | Yes | Yes (unchanged) |
| `tsc --noEmit` breaks after a folder rename | **Yes** | No |
| Temptation to `rm -rf .next` | High | Zero |

Net: a small loss of `tsc`-time route-handler type checking in exchange for never breaking the dev server again. `next build` in CI still catches the same errors.

## Global rule for Claude sessions

Add this block to your `~/.claude/CLAUDE.md` (or the project-local `CLAUDE.md`):

```markdown
## Next.js frontend type checks

- Use `npm run typecheck` inside `frontend/` (not bare `npx tsc --noEmit`).
- Never `rm -rf .next` to make type errors go away. That nukes the
  running `next dev` server's CSS/JS manifest and you get an unstyled
  page. If `npm run typecheck` fails after a rename, restart `next dev`
  (which regenerates `.next/types/**` cleanly) — don't delete the cache.
- If `.next/` genuinely needs purging (Next version bump, corrupted
  cache), kill `next dev` first, then `rm -rf .next`, then start
  `next dev` fresh. The three steps go together, never the middle
  step alone.
```

## How to apply

1. Edit the two files above.
2. Run `npm run typecheck` to confirm it exits 0.
3. Simulate the failure mode: rename any folder under `app/`, `git mv` it, run `npm run typecheck` — should pass without clearing `.next`.
4. Revert the rename.

The bug class is gone.

## When NOT to use this

- You're on **Next.js 15+** and have `next typegen` available. Then `"typecheck": "next typegen && tsc --noEmit"` is the correct fix (keeps the route-handler type safety and regenerates declarations deterministically). Use this skill for Next 14 only.

## Pattern this instance-of

A more general pattern: **don't ask tool A to depend on artifacts tool B generates unless tool A can regenerate them itself**. The TS compiler can't run Next's type generation. So excluding `.next/` is the clean seam.

---

**License:** MIT — use freely in your own projects and skill libraries.
