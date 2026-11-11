# webkit2gtk 4.0 — prebuilt packages for Arch Linux

Prebuilt `webkit2gtk` (the old **4.0 API**, libsoup2-based) and `libsoup` 2.x
packages for Arch Linux x86_64.

Arch dropped both from the official repositories. They are still available on
the AUR, but `webkit2gtk` takes several hours and well over 10 GB of disk to
compile. Some older applications still need it — for example the Pulse Secure /
Ivanti VPN client UI (`pulseUi`). These packages save you the build.

> **Türkçe özet:** Arch'ın resmi depolarından çıkarılan eski `webkit2gtk` (4.0)
> ve `libsoup` 2 paketlerinin derlenmiş halleri. AUR'dan derlemek saatler
> sürdüğü için buraya koydum. Kurulum için aşağıdaki iki komut yeterli.

## Install

Download both files from the
[latest release](https://github.com/onur-akalan/webkit2gtk-4.0-arch/releases/latest),
then:

```bash
sha256sum -c SHA256SUMS
```

```bash
sudo pacman -U libsoup-2.74.3-4-x86_64.pkg.tar.zst webkit2gtk-2.50.6-8-x86_64.pkg.tar.zst
```

To remove them later:

```bash
sudo pacman -Rns webkit2gtk libsoup
```

## What is in the release

| Package | Version | Built | Source |
|---|---|---|---|
| `webkit2gtk` | 2.50.6-8 | 2026-10-06 | [AUR `webkit2gtk`](https://aur.archlinux.org/packages/webkit2gtk), commit `f20b046` |
| `libsoup` | 2.74.3-4 | 2026-11-11 | [AUR `libsoup`](https://aur.archlinux.org/packages/libsoup), commit `76d9e09` |

Both were built with the unmodified AUR PKGBUILDs and Arch's default
`makepkg.conf` flags (`-march=x86-64 -mtune=generic`), so they run on any
x86_64 Arch system. They are **not signed**.

Verified on 2026-11-11: both packages install in a clean, fully updated
`archlinux:latest` container with no missing shared libraries (icu 78.3,
libxml2 2.15.4, libjxl 0.12.0).

## Read this before installing

- **Security:** this is an end-of-life branch of WebKitGTK and an unmaintained
  libsoup. Neither receives security fixes any more. Use them only for the
  trusted application that needs them; do not browse the web with them.
- **Arch only:** the packages work on Arch and close derivatives that track
  Arch's repositories (EndeavourOS, CachyOS). They do not work on Debian,
  Ubuntu or Fedora.
- **They can break after a system update:** the libraries are linked against
  the versions of `icu` and other libraries Arch shipped at build time. When
  Arch moves one of those to a new major version, these packages stop loading
  until they are rebuilt. If that happens, build from the AUR
  (`yay -S libsoup webkit2gtk`) or check here for a newer release.
- **You are trusting my build.** If that is not acceptable, build from the AUR
  yourself; the result should be equivalent.

## Licences and source

These are unmodified builds of free software. WebKitGTK is licensed under
LGPL-2.1-or-later and BSD-2-Clause (among others); libsoup under
LGPL-2.0-or-later. The full licence texts are installed with each package under
`/usr/share/licenses/`.

Corresponding source:

- WebKitGTK 2.50.6: <https://webkitgtk.org/releases/webkitgtk-2.50.6.tar.xz>
- libsoup 2.74.3: <https://gitlab.gnome.org/GNOME/libsoup/-/tags/2.74.3>
- Build recipes: the AUR links in the table above.

This repository is not affiliated with Arch Linux, the WebKitGTK project or
GNOME.
