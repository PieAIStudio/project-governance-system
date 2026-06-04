# Contributing

Project Governance System is intentionally small. The safest contribution is one
that improves the shared governance layer without importing project-local truth.

## Before Changing Rules

Read `AGENTS.md` first. For governance changes, also read:

- `docs/governance/boundary.md`
- `docs/governance/ssot-v0.9.md`
- `docs/policy/design-principles.md`
- `docs/policy/upstreaming-policy.md`

## Local Verification

Run the full local gate before opening a change:

```bash
pnpm install
pnpm typecheck
pnpm test
pnpm build
pnpm doc-gov router-check
pnpm doc-gov check
pnpm doc-gov scan --check
pnpm doc-gov links
pnpm doc-gov audit
pnpm doc-gov doctor
git diff --check
```

## Boundaries

- Put core documentation-governance rules in this repository first.
- Keep product canon, runtime truth, generated media, and project-specific
  prompts in the downstream project.
- Do not vendor external workflow systems here.
- Add a new profile only after at least two real projects need the same shape.
