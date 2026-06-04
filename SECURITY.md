# Security Policy

Project Governance System is a small public-preview governance toolkit. Please
report suspected security issues privately instead of opening a public issue.

## Reporting

Email: PIEAI@hotmail.com

Include:

- affected command or file
- reproduction steps
- expected impact
- whether any sensitive information may have been exposed

## Public Release Hygiene

Before making repository or npm releases, maintainers should verify:

```bash
pnpm test
pnpm build
pnpm doc-gov doctor
npm pack --dry-run
```

Also scan for secrets and machine-local paths before changing a repository from
private to public.
