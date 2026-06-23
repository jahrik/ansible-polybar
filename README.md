# ansible-polybar

[![CICD](https://github.com/jahrik/ansible-polybar/actions/workflows/cicd.yml/badge.svg)](https://github.com/jahrik/ansible-polybar/actions/workflows/cicd.yml)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-jahrik.polybar-blue?logo=ansible)](https://galaxy.ansible.com/ui/standalone/roles/jahrik/polybar/)

Installs and configures [Polybar](https://polybar.github.io/), a fast and easy-to-use status bar. On Arch Linux, it installs from official repos via `pacman`. On Debian/Ubuntu, it installs from source or apt. Deploys `~/.config/polybar/config` and `~/.config/polybar/launch.sh` from templates.

## Supported OS

| Platform | Install method |
|---|---|
| Arch Linux | Official repo via `pacman` |
| Ubuntu / Debian | Source build / `apt` |

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `install` | `true` | Set to `false` to uninstall polybar. |
| `polybar.version` | `3.5.7` | Source version to build on Debian/Ubuntu (Arch always gets latest from pacman) |

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

## License

MIT

## Author Information

jahrik@gmail.com
