# LauncherTW

Yet another homelab dashboard with ZERO Javascript, powered by TailwindCSS and Ansible.

![Screenshot](.github/screenshot.png)

## Setup

LauncherTW is an Ansible role, which means you need to install Ansible.

You can install Ansible with your OS's package manager, such as `apt`, `dnf`, `pacman`, or `brew`, or you can
[install with `pip`](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

## Configuration

The configuration has **two** parts: Ansible role configuration and page content.

### Ansible role configuration

Refer to [`defaults/main/ansible.yml`](defaults/main/ansible.yml) for config references.

| Variable            | Type                         | Default                            |
| ------------------- | ---------------------------- | ---------------------------------- |
| `operation`         | string (`build` or `deploy`) | `build`                            |
| `build_output_dir`  | string (directory or `TMP`)  | `TMP`                              |
| `deploy_target_dir` | string (directory)           | **None**. Must specify explicitly. |

### Page content

A default/sample page content configuration is provided
[here (`defaults/main/LauncherTW.yml`)](defaults/main/LauncherTW.yml). Refer to this file for config references.

## Credits

- [Ansible](https://docs.ansible.com/): an open source software suite that enables Infrastructure as Code (IaC).
- [TailwindCSS](https://tailwindcss.com/): a utility-first CSS framework
- The config layout is *heavily inspired* by [Homer](https://github.com/bastienwirtz/homer)

## License

[Apache License 2.0](LICENSE)
