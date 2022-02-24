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

### Work in progress

The playbook is under heavy development and there is certainly stuff missing or
incomplete. Be warned, you may run into unexpected issues. I am trying to
maintain a simple ToDo list.

### Features

The Ansible playbook is meant to be used via
[ansible-pull](https://docs.ansible.com/ansible/latest/cli/ansible-pull.html).
This also indicates, that reboots will not be triggered automatically. Most of
these settings, configurations and installations can be toggled or changed with
some parameters.

The below software and configurations are included:

- [Ansible](./ansible/roles/ansible/)
- [Bash](./ansible/roles/bash/)
- [Cirrus CLI](./ansible/roles/cirrus_cli/)
- [dnf](./ansible/roles/dnf/)
- [fedora specifics](./ansible/roles/fedora/)
- [firewalld](./ansible/roles/firewalld/)
- [flathub](./ansible/roles/flathub/)
- [git](./ansible/roles/git/)
- [GitHub Clients](./ansible/roles/github_client/)
- [GNOME applications](./ansible/roles/gnome_applications/)
- [GNOME Shell](./ansible/roles/gnome_shell/)
- [Kubernetes Clients](./ansible/roles/kubernetes_client/)
- [Misc Tasks](./ansible/roles/misc/)
- [nodejs](./ansible/roles/nodejs/)
- [Podman](./ansible/roles/podman/)
- [SELinux](./ansible/roles/selinux/)
- [Updates](./ansible/roles/update/)
- [Users](./ansible/roles/user/)
- [VSCode](./ansible/roles/vscode/)

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

This section describes how to install and get the playbook going.

#### Ansible

Before starting to use the playbook, you need to ensure that Ansible is
installed in a recent version. To do, you can use PyPi (`pip`) as described
below.

```shell
# Create a new python virtual environment (venv)
$ python3 -m venv ~/.venv-ansible

# Jump into the new environment
$ source ~/.venv-ansible/bin/activate

# Install Ansible
$ pip install ansible psutil selinux
```

Since Fedora 35, you can also install Ansible 2.12.

```shell
# Install ansible via dnf
$ sudo dnf install ansible-core -y
```

#### Playbook

Afterwards, you can download the desired release from the
[release page](https://github.com/whiletruedoio/container-template/tags) and
store it in a location, that suits you.

```shell
# Download a tag/release
$ https://github.com/dschier-wtd/fedora-workstation/archive/refs/tags/<tag_name>.zip

```

If you want to use git instead, help to develop or change to a tag/branch on
the fly, you can clone the repository instead.

```shell
# Clone the repository with a given tag
$ git clone https://github.com/dschier-wtd/fedora-workstation.git

# Checkout the desired tag
$ git checkout <tag_name>
```

#### Roles and Collections

Before running the actual playboook, it is needed to install required roles
and collections. This can be done in two simple commands.

```shell
# Install collections
$ ansible-galaxy collection install -r ansible/requirements.yml

# Install roles
$ ansible-galaxy role install -r ansible/requirements.yml
```

#### Tuning variables

You can find lots of default variables in the roles and used codes. Most of
the behaviour can be tuned by adjusting these variables in the playbook.

For example, to adjust the GNOME applications that are installed during the
playbook run, you can:

1. look up the variables in the
   [defaults/main.yml](./ansible/roles/gnome_applications/defaults/main.yml)
   of the role
2. Pick the variable, you want to change and edit the
   [playbook workstation.yml](./ansible/workstation.yml) like the below example

```yaml
---
# ansible playbook for github.com/dschier-wtd/fedora-workstation

- name: "Configure Fedora Workstation"
  hosts: "localhost"
  connection: "local"

  vars:

    misc_hostname: "greentea.local"
    misc_timezone: "Europe/Berlin"
    gnome_app_gaming_package_state: "present"

...SNIP...
```

Since it is planned to move all roles in a proper collection, there is not much
documentation for the roles, for now.

#### The first run

Now you are ready to execute the playbook. Be aware, that this will run for
quite some time, remove packages, download packages and configure a couple of
services.

```shell
# Execute the playbook
$ ansible-playbook -K ansible/workstation.yml
```

It is a good idea to restart your machine afterwards to ensure that everything
is working and configured as expected.

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
