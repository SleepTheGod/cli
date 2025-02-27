# Installing gh on Linux and BSD

Packages downloaded from https://cli.github.com or from https://github.com/cli/cli/releases
are considered official binaries. We focus on popular Linux distros and
the following CPU architectures: `i386`, `amd64`, `arm64`, `armhf`.

Other sources for installation are community-maintained and thus might lag behind
our release schedule.

## Official sources

### Debian, Ubuntu Linux, Raspberry Pi OS (apt)

:warning: :warning: :warning: :warning: This method is currently broken. Consumers of the .deb release are advised to either install the version of `gh` supplied by the official Debian/Ubuntu repositories or download the appropraite binary from https://github.com/cli/cli/releases/latest . :warning: :warning: :warning: :warning:

Install:

```bash
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

Upgrade:

```bash
sudo apt update
sudo apt install gh
```

### Fedora, CentOS, Red Hat Enterprise Linux (dnf)

Install from our package repository for immediate access to latest releases:

```bash
sudo dnf install 'dnf-command(config-manager)'
sudo dnf config-manager --add-repo https://cli.github.com/packages/rpm/gh-cli.repo
sudo dnf install gh
```

Alternatively, install from the [community repository](https://packages.fedoraproject.org/pkgs/gh/gh/):

```bash
sudo dnf install gh
```

Upgrade:

```bash
sudo dnf update gh
```

### openSUSE/SUSE Linux (zypper)

Install:

```bash
sudo zypper addrepo https://cli.github.com/packages/rpm/gh-cli.repo
sudo zypper ref
sudo zypper install gh
```

Upgrade:

```bash
sudo zypper ref
sudo zypper update gh
```

## Manual installation

* [Download release binaries][releases page] that match your platform; or
* [Build from source](./source.md).

## Unofficial, community-supported methods

The GitHub CLI team does not maintain the following packages or repositories and thus we are unable to provide support for those installation methods.

### Snap (do not use)

There are [so many issues with Snap](https://github.com/casperdcl/cli/issues/7) as a runtime mechanism for apps like GitHub CLI that our team suggests _never installing gh as a snap_.

### Arch Linux

Arch Linux users can install from the [community repo][arch linux repo]:

```bash
sudo pacman -S github-cli
```

Alternatively, use the [unofficial AUR package][arch linux aur] to build GitHub CLI from source.

### Android

Android 7+ users can install via [Termux](https://wiki.termux.com/wiki/Main_Page):

```bash
pkg install gh
```

### FreeBSD

FreeBSD users can install from the [ports collection](https://www.freshports.org/devel/gh/):

```bash
cd /usr/ports/devel/gh/ && make install clean
```

Or via [pkg(8)](https://www.freebsd.org/cgi/man.cgi?pkg(8)):

```bash
pkg install gh
```

### NetBSD/pkgsrc

NetBSD users and those on [platforms supported by pkgsrc](https://pkgsrc.org/#index4h1) can install the [gh package](https://pkgsrc.se/net/gh):

```bash
pkgin install gh
```

To install from source:

```bash
cd /usr/pkgsrc/net/gh && make package-install
```

### OpenBSD

In -current, or in releases starting from 7.0, OpenBSD users can install from packages:

```
pkg_add github-cli
```

### Funtoo

Funtoo Linux has an autogenerated github-cli package, located in [dev-kit](https://github.com/funtoo/dev-kit/tree/1.4-release/dev-util/github-cli), which can be installed in the following way:

``` bash
emerge -av github-cli
```

Upgrading can be done by syncing the repos and then requesting an upgrade:

``` bash
ego sync
emerge -u github-cli
```

### Gentoo

Gentoo Linux users can install from the [main portage tree](https://packages.gentoo.org/packages/dev-util/github-cli):

``` bash
emerge -av github-cli
```

Upgrading can be done by updating the portage tree and then requesting an upgrade:

``` bash
emerge --sync
emerge -u github-cli
```

### Kiss Linux

Kiss Linux users can install from the [community repos](https://github.com/kisslinux/community):

```bash
kiss b github-cli && kiss i github-cli
```

### Nix/NixOS

Nix/NixOS users can install from [nixpkgs](https://search.nixos.org/packages?show=gitAndTools.gh&query=gh&from=0&size=30&sort=relevance&channel=20.03#disabled):

```bash
nix-env -iA nixos.gitAndTools.gh
```

### openSUSE Tumbleweed

openSUSE Tumbleweed users can install from the [official distribution repo](https://software.opensuse.org/package/gh):
```bash
sudo zypper in gh
```

### Alpine Linux

Alpine Linux users can install from the [stable releases' community package repository](https://pkgs.alpinelinux.org/packages?name=github-cli&branch=v3.15).

```bash
apk add github-cli
```

Users wanting the latest version of the CLI without waiting to be backported into the stable release they're using should use the edge release's
community repo through this method below, without mixing packages from stable and unstable repos.[^1]

```bash
echo "@community http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories
apk add github-cli@community
```

### Void Linux
Void Linux users can install from the [official distribution repo](https://voidlinux.org/packages/?arch=x86_64&q=github-cli):

```bash
sudo xbps-install github-cli
```

[releases page]: https://github.com/cli/cli/releases/latest
[arch linux repo]: https://www.archlinux.org/packages/community/x86_64/github-cli
[arch linux aur]: https://aur.archlinux.org/packages/github-cli-git
[^1]: https://wiki.alpinelinux.org/wiki/Package_management#Repository_pinning
