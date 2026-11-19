# Fuzzel configuration

Wayland application launcher and shared dmenu frontend for the desktop helpers.

**[Documentation](https://aco-docs.readthedocs.io/en/latest/fuzzel/)** ·
[Guide](https://aco-docs.readthedocs.io/en/latest/fuzzel/guide/) ·
[Design & dependencies](https://aco-docs.readthedocs.io/en/latest/fuzzel/design/) ·
[Installation and updates](https://aco-arch-dotfiles.readthedocs.io/en/latest/arch-package/)

```bash
curl -fsSL https://raw.githubusercontent.com/Akademie-Olympia/aco-arch-dotfiles/main/install.sh | bash -s -- fuzzel
```

Package: `aco-arch-dotfiles-fuzzel`. This standalone repository holds the development sources and the package recipe in
`packaging/arch/PKGBUILD`. The documentation of this component lives in the shared
[aco-docs](https://github.com/Akademie-Olympia/aco-docs) repository (one Read the Docs project for all small components).
Push to `main`; after a successful registry build update with `sudo pacman -Syu`. Details and local builds: [PACKAGING.md](PACKAGING.md).

### Customisation

Font, colours and layout live in `~/.config/fuzzel/fuzzel.ini`. Fuzzel doubles as the menu frontend through `fuzzel --dmenu`; `man fuzzel.ini` describes the options.

Your own changes in the activated user copy survive synchronisation; new differing defaults appear as `.pacnew`.
See [update and recovery](https://aco-arch-dotfiles.readthedocs.io/en/latest/verification/).

[![Package safety](https://github.com/Akademie-Olympia/aco-fuzzel/actions/workflows/package.yml/badge.svg)](https://github.com/Akademie-Olympia/aco-fuzzel/actions/workflows/package.yml)

[MIT licence](LICENSE).
