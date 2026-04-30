# AGENTS.md

## What this repo is

An Ansible role that generates a static homelab dashboard HTML page. No JavaScript at runtime — the page is fully server-rendered by Jinja2 + TailwindCSS.

## Build flow

The build is driven by Ansible, not npm scripts:

1. `tasks/main.yml` validates config, then delegates to `tasks/build.yml`
2. `tasks/build.yml` copies static assets, downloads Font Awesome, runs `npx tailwindcss` to compile CSS, renames the output to include an MD5 checksum, and renders `templates/index.html.j2`

All output lands in `launchertw_build_output_dir` (required, no default).

To build, run the role against localhost — there is no `npm run build` or similar.

## TailwindCSS

- TailwindCSS **v4** (`@tailwindcss/cli` + `tailwindcss` v4): CSS-first config, no `tailwind.config.js`
- CSS source: `files/css/launcher.css` (just `@import "tailwindcss"`)
- Compiled by the Ansible role via `npx tailwindcss -m -i files/css/launcher.css -o <output>/launcher.min.css` (v4 has no `-c` flag; config is CSS-first)
- The template references the checksummed filename: `launcher.min.{{ _css_stat.stat.checksum }}.css`

## Content configuration

Page content is defined via Ansible variables (see `vars.example.yml` for schema): `page_title`, `header_links`, `announcement`, `services`, `footer_links`. Font Awesome v7.x icons are used throughout.

## Linting

Run pre-commit hooks using `prek`: `prek run --all-files`.

CI uses `uvx prek run --all-files`.

Note: Use `prek` not `pre-commit`. When running locally, assume `prek` is already installed. **DO NOT INSTALL PACKAGES.**

### yamllint rules (`.yamllint`)

- Line length max 120
- Double quotes only when needed
- Document-start marker (`---`) required
- Octal values forbidden

### ansible-lint (`.ansible-lint`)

Extra rules enabled: `args`, `empty-string-compare`, `no-same-owner`, `role-name`.

## No test suite

There are no automated tests. Verify changes by running the linters above and optionally running the Ansible role locally.
