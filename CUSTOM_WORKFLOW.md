# Custom branch workflow

This repo is on the **`custom`** branch for local changes. Upstream is `origin/main`.

## First-time: set Git identity (if needed)

If commits fail with "Yazar kimliği bilinmiyor" / "your identity", run once:

```bash
git config --global user.name "Adınız"
git config --global user.email "siz@e-posta.com"
```

Then commit this file: `git add CUSTOM_WORKFLOW.md && git commit -m "docs: add custom branch workflow"`.

## Bringing in upstream updates (without losing your changes)

From the repo root, with your changes committed or stashed:

```bash
git fetch origin
git merge origin/main
```

Resolve any conflicts, then:

```bash
pnpm install
pnpm build
pnpm ui:build   # if UI was updated
openclaw doctor
```

Alternative (linear history, but rewrites your branch):

```bash
git fetch origin
git rebase origin/main
```

Then same install/build/doctor steps.

## Do not use `openclaw update` on this branch

`openclaw update` (and Control UI “Update & Restart”) assumes a clean checkout on `main` and will rebase/checkout there. On `custom`, use the manual merge/rebase above instead.

## Quick reference

| Goal             | Command                                      |
| ---------------- | -------------------------------------------- |
| Update from main | `git fetch origin && git merge origin/main`  |
| Rebase on main   | `git fetch origin && git rebase origin/main` |
| See branch       | `git branch`                                 |
| Switch to main   | `git checkout main` (no local changes there) |
