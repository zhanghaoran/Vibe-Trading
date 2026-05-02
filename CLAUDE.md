# Vibe-Trading Project

## Repository Setup

This is a forked repository with the following remote configuration:

- `origin` → fork (`zhanghaoran/Vibe-Trading`)
- `upstream` → original repo (`HKUDS/Vibe-Trading`)

### Branch Strategy

- `main` → tracks upstream, kept in sync with original repo
- `dev` → development branch for customizations

### Sync Workflow

To merge upstream changes into dev periodically:

```bash
# Fetch latest from both remotes
git fetch upstream
git fetch origin

# Sync main with upstream
git checkout main
git merge upstream/main --ff-only
git push origin main

# Merge upstream changes into dev
git checkout dev
git merge upstream/main
git push origin dev
```