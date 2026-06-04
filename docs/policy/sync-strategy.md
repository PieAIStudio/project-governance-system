---
id: POLICY-SYNC-STRATEGY
title: Project Governance System Sync Strategy
type: policy
status: stable
canonical: true
owner: human
created: 2026-05-06
last_reviewed: 2026-06-04
domain: adoption
tags:
  - sync
  - adoption
  - package-install
pinned: true
related:
  - REF-ADOPTION-PLAYBOOK
  - REF-PROJECT-RELATIONSHIP
---

# Sync Strategy

## Stage 0: AI-Assisted Sync

Use this for projects that already have a local `tools/doc-gov` copy and should
not be disturbed mid-flight.

Projects keep local copies. An AI migration task compares the project against this repo and applies only the relevant profile.

Benefits:

- safest while the system is young
- no accidental breakage across Supa, PieFlow, and PieIP
- project-local differences stay visible

Drawback:

- requires explicit migration prompts

## Stage 1: Scripted Copy / Diff

Partially available now as a read-only check:

```bash
doc-gov migrate --profile engineering-runtime --check
```

This does not update files yet. It verifies that the target project structurally
matches the selected profile before a human or AI sync task edits anything.

The future `--apply` mode should update core/starter files while preserving
local profile sections:

```bash
doc-gov migrate --profile engineering-runtime --apply
```

## Stage 2: Package Install

Projects depend on `@pieai/doc-gov` instead of keeping local CLI source:

```bash
pnpm add -D @pieai/doc-gov
pnpm doc-gov check
```

This is now the preferred direction for new adoption work and for projects that
can update scripts, local hooks, and CI in one deliberate change. Do not switch
only the package command while leaving old guardrails behind; that creates a
half-migrated project.

## Stage 3: Published Template / Init

New projects can start with:

```bash
pnpm dlx @pieai/doc-gov init --profile doc-only
pnpm dlx @pieai/doc-gov init --profile engineering-runtime
```

Do not jump here before Stage 1 proves the selected profile is structurally
ready.
