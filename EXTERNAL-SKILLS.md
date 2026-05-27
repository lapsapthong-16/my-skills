# External Skills

External skills are installed from their original upstream source instead of copied into this repository.

Use this file for skills that:

- Have their own installer.
- Update frequently.
- Are maintained by someone else.
- Are not customized in this repository.

If you want to customize or pin one of these skills, copy the relevant skill folder into `skills/<skill-name>/` and maintain your copy there.

## Caveman

Source: https://github.com/JuliusBrussee/caveman

Install:

```bash
curl -fsSL https://raw.githubusercontent.com/JuliusBrussee/caveman/main/install.sh | bash
```

What this does:

- Downloads and runs Caveman's upstream installer.
- Installs Caveman from `github:JuliusBrussee/caveman`.
- Does not add files to this repository.
- Keeps Caveman managed by its upstream project.

Use this when you want the current upstream Caveman setup. Vendor it into `skills/` only if you want to customize it or keep a pinned local copy.
