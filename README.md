<!--
reference: https://www.makeareadme.com/
reference: https://commonmark.org/
-->

[![Cirrus CI - Base Branch Build Status](https://img.shields.io/cirrus/github/dschier-wtd/fedora-workstation?logo=Cirrus-ci)](https://cirrus-ci.com/github/dschier-wtd/fedora-workstation)
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/dschier-wtd/fedora-workstation?logo=GitHub&label=Release&sort=semver)](https://github.com/dschier-wtd/fedora-workstation/releases)
[![GitHub issues](https://img.shields.io/github/issues/dschier-wtd/fedora-workstation)](https://github.com/dschier-wtd/fedora-workstation/issues)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/dschier-wtd/fedora-workstation)](https://github.com/dschier-wtd/fedora-workstation/pulls)
[![GitHub license](https://img.shields.io/github/license/dschier-wtd/fedora-workstation)](https://github.com/dschier-wtd/fedora-workstation/blob/main/LICENSE)

# Fedora Workstation

Ansible setup of my workstation.

## Motivation

I am using Fedora for my workstation. I am have some customizations applied and
software installed, that I rely on. To ensure that everything works after a
re-installation and document my setup, I wanted to provide some more code.

## Description

The playbook will install and configure various software. Most of the automation
can be configured very easily and should be self-explanatory. Nevertheless,
the following section will provide a feature overview.

### Features

The Ansible playbook is meant to be used via
[ansible-pull](https://docs.ansible.com/ansible/latest/cli/ansible-pull.html).
This also indicates, that reboots will not be triggered automatically. Most of
these settings, configurations and installations can be toggled or changed with
some parameters.

The below software and configurations are included:

- [Ansible](./roles/ansible/)
- [Bash](./roles/bash/)
- [cpupowerd](./roles/misc/)
- [dnf](./roles/dnf/)
- [firewalld](./roles/firewalld/)
- [flathub](./roles/flathub/)
- [git](./roles/git/)
- [GNOME Shell](./roles/gnome_shell/)
- [GNOME applications](./roles/gnome_applications/)
- [nodejs](.roles/nodejs/)
- [Podman](./roles/podman/)
- [SELinux](./roles/selinux/)
- [thermald](./roles/thermald/)
- [VSCode](./roles/vscode/)

In addition, there are some configurations and package removals for unwanted
software. I try to use flatpak packages as much as possible to avoid a system
with hundreds of packages installed. Furthermore, the packages on flathub are
often more up-to-date, can be updated without affecting the system and can be
removed/reset with a single command.

<!--
Lastly, the playbook is pulling in the configurations from my
[.dotfiles](https://github.com/dschier-wtd/.dotfiles) repository and configure
the system accordingly.
-->

### Support

There is basically no support except my own setup. I am using the current
release of [Fedora Workstation](https://getfedora.org/en/workstation/) on a
[Dell XPS 13 9310](https://en.wikipedia.org/wiki/Dell_XPS) notebook. The
combination provides an excellent package of usability, power efficiency and is
very mobile.

For my home desktop, I also rely on a
[Logitech MX Master](https://www.logitech.com/en-us/mx/master-series.html) mouse
and a [CODE Keyboard](https://codekeyboards.com/). Both are attached to a
[Dell USB-C Monitor](https://www.dell.com/en-us/work/lp/usb-c-monitor), which
is also functioning as the docking station/charger for this setup.

Please don't expect me to implement NVidia Support or other weird hardware, that
only works with lots of tuning.

## Usage

The playbook is designed to be used on a localhost via `ansible-playbook` or
`ansible-pull`. This section describes which steps are needed to work with the
same tools, I do.

### Requirements

You will need a Fedora Workstation installation with installed Ansible. I don't
do any partitioning or network configuration in the playbook, so this is up to
you. Nevertheless, for me it works best, when using a simple Fedora Workstation
setup with btrfs. One may say... default. :heart:

### Install

TBD

### Documentation

TBD

## Contribute

The dotfiles are intended to be used by me (Daniel Schier), but please feel free
to use/fork/enhance them or opening issues to give me an idea what may be added
in future versions.

## License

Except otherwise noted, all work is [licensed](LICENSE) under a
[BSD-3-Clause License](https://opensource.org/licenses/BSD-3-Clause).

## Contact

Please feel free to reach out to me to provide feedback or get in touch.

- Site: <https://while-true-do.io>
- Blog: <https://blog.while-true-do.io>
- Code: <https://github.com/dschier-wtd>
- Mail: [dschier@while-true-do.io](mailto:dschier@while-true-do.io)
