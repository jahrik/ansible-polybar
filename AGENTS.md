# AGENTS.md

This file provides guidance to AI coding agents when working with code in this repository.

## Role Overview

Installs and configures [Polybar](https://github.com/polybar/polybar), a fast and easy-to-use status bar. On Arch Linux, installs from AUR via `jahrik.yay`. On Debian/Ubuntu, installs via `apt`. Deploys `~/.config/polybar/config` and `~/.config/polybar/launch.sh` from templates.

## Key Variables

| Variable | Default | Description |
|---|---|---|
| `polybar.version` | `3.5.7` | Polybar version (informational; Arch gets latest from AUR, Debian/Ubuntu uses apt) |

## Task Flow

- `tasks/main.yml` — includes `debian.yml` or `archlinux.yml` based on OS family, then deploys config templates
- `tasks/archlinux.yml` — installs via `jahrik.yay` (AUR)
- `tasks/debian.yml` — installs via `apt`

## Testing

```bash
uv sync
source .venv/bin/activate
yamllint .
ansible-lint
molecule test
```

## CI

- **Lint**: yamllint + ansible-lint
- **Molecule**: Arch Linux via Docker (AUR install path)
- **Release**: publishes to Ansible Galaxy on merge to `main`
