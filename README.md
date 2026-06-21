# POLYBAR

[![CICD](https://github.com/jahrik/ansible-polybar/actions/workflows/cicd.yml/badge.svg)](https://github.com/jahrik/ansible-polybar/actions/workflows/cicd.yml)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-jahrik.polybar-blue?logo=ansible)](https://galaxy.ansible.com/ui/standalone/roles/jahrik/polybar/)

Installs [Polybar](https://polybar.github.io/) — a fast and easy-to-use status bar ([GitHub](https://github.com/polybar/polybar)) — and deploys config and launch script to `~/.config/polybar/`. Depends on `jahrik.yay` for AUR installation on Arch.

## OS Support

| Platform | Install method |
|---|---|
| Arch Linux | AUR via `jahrik.yay` |
| Debian / Ubuntu | `apt install polybar` |

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `polybar.version` | `3.5.7` | Polybar version (informational; Arch gets latest from AUR, Debian/Ubuntu uses apt) |

## Example Playbook

```yaml
---
- hosts: all
  roles:
    - role: jahrik.polybar
```

## Testing

```bash
uv sync
source .venv/bin/activate
yamllint .
ansible-lint
molecule test
```

Step by step:

```bash
molecule converge
molecule verify
molecule destroy
```

## License

GPLv2

## Author Information

jahrik@gmail.com
