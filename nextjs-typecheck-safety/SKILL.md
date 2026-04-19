# SKILL: Next.js Type-Check Safety

## Trigger

When a Next.js 14 project uses `tsc --noEmit` or `npx tsc --noEmit` as its type-check command AND has `.next/types/**/*.ts` in the `tsconfig.json` `include` list, any folder rename under `app/` will cause stale route-handler type declarations to fail the next TSC run. Users reflexively clear `.next/` to resolve the error, which silently breaks the running `next dev` server's CSS/JS manifest and produces an unstyled page.

Detect by looking for:

1. `frontend/tsconfig.json` containing `".next/types/**/*.ts"` in `include`
2. Next version < 15 (no `next typegen` CLI command available)
3. No `typecheck` script in `package.json`

## Fix

Apply these two edits:

### tsconfig.json

```json
{
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx"],
  "exclude": ["node_modules", ".next"]
}
```

### package.json → scripts

```json
"typecheck": "tsc --noEmit"
```

## Verify

```bash
cd frontend && npm run typecheck     # should exit 0
git mv app/some-folder app/some-folder-renamed
npm run typecheck                    # should still exit 0
git mv app/some-folder-renamed app/some-folder
```

The bug is gone if step 2 passes without requiring `.next/` to be cleared.

## Rule for future sessions

Add to `~/.claude/CLAUDE.md`:

> Use `npm run typecheck` inside `frontend/` (not bare `npx tsc --noEmit`).
> Never `rm -rf .next` to silence type errors — that nukes the running
> `next dev` server's CSS/JS manifest. If type errors persist after
> `npm run typecheck`, they're real.

## Why this is the right-sized fix

- Not a pre-commit hook — heavyweight for a one-command habit change
- Not a CI gate — bug hits locally during iteration, CI is too late
- Not a filesystem watcher — overengineered
- Just: exclude `.next/` from the TS project + document the canonical command

## Trade-off

Loses `tsc`-time enforcement of Next route-handler type signatures. The Next TS plugin still provides IDE help, and `next build` catches the same errors in CI. Net: tiny loss of one validation layer, zero dev-server breakage.
