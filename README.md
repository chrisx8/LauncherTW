# LauncherTW

Yet another homelab dashboard with ZERO Javascript, powered by TailwindCSS and Ansible.

![Screenshot](.github/screenshot.png)

## Setup

### Ansible

LauncherTW is an Ansible role, which means you need to install Ansible.

You can install Ansible with your OS's package manager, such as `apt`, `dnf`, `pacman`, or `brew`. You can also [install with `pip`](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

### Tailwind CSS

LauncherTW uses [Tailwind CSS](https://tailwindcss.com/), specifically the `tailwindcss` CLI. To install, run:

```sh
npm install
```

## Configuration

The configuration has **two** parts: Ansible role configuration and page content.

### Ansible role configuration

Refer to [`defaults/main/ansible.yml`](defaults/main/ansible.yml) for config references.

| Variable                       | Type                         | Default                            |
| ------------------------------ | ---------------------------- | ---------------------------------- |
| `launchertw_operation`         | string (`build` or `deploy`) | `build`                            |
| `launchertw_build_output_dir`  | string (directory or `TMP`)  | `TMP`                              |
| `launchertw_deploy_target_dir` | string (directory)           | **None**. Must specify explicitly. |

### Page content

Refer to [`defaults/main/LauncherTW.yml`)](defaults/main/LauncherTW.yml) for page content configuration.

## Credits

- [Ansible](https://docs.ansible.com/): an open source software suite that enables Infrastructure as Code (IaC).
- [TailwindCSS](https://tailwindcss.com/): a utility-first CSS framework
- The config layout is *heavily inspired* by [Homer](https://github.com/bastienwirtz/homer)

## License

[Apache License 2.0](LICENSE)

Copyright (c) 2022-2023 Chris Xiao
