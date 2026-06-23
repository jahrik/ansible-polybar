# AGENTS.md

This file provides guidance to AI coding agents when working with code in this repository.

## Role Overview

Installs and configures [Polybar](https://github.com/polybar/polybar), a fast and easy-to-use status bar. On Arch Linux, installs from AUR via `jahrik.yay`. On Debian/Ubuntu, builds or installs from apt. Deploys `~/.config/polybar/config` and `~/.config/polybar/launch.sh` from templates.

## Key Variables

| Variable | Default | Description |
|---|---|---|
| `install` | `true` | Set to `false` to uninstall polybar. |
| `polybar.version` | `3.5.7` | Source version to build on Debian/Ubuntu (Arch always gets latest from AUR) |

## Task Flow

- `tasks/main.yml` — includes `install.yml` or `uninstall.yml`
- `tasks/install.yml` — includes `debian.yml` or `archlinux.yml` based on OS family, then deploys config templates
- `tasks/archlinux.yml` — installs via `jahrik.yay` (AUR)
- `tasks/debian.yml` — updates apt cache, installs build dependencies, downloads and compiles from source
- `tasks/uninstall.yml` — uninstalls polybar and removes config files

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
- **Molecule**: Ubuntu via Docker
- **Release**: publishes to Ansible Galaxy on merge to `main`
