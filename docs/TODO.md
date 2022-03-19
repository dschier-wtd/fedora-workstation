# ToDo

:hammer: Work work work.

## Enhancements

### software

- [x] add distrobox
- [x] add cirrus-cli
- [x] add arm tools for raspberry pi and other soc
- [x] add system update playbook
- [x] add fortune
- [x] add github client / cli
- [x] add thermald role
- [x] add vscode extensions installation
- [x] add ratbagd and piper for logitech devices
- [x] remove hamster app
- [x] add options for:
  - [x] <https://flathub.org/apps/details/com.github.bleakgrey.tootle>
  - [x] <https://flathub.org/apps/details/im.riot.Riot>
  - [x] <https://flathub.org/apps/details/sh.cider.Cider>
- [x] remove background logo extension
- [x] python-psutil missing for dependencies of gnome-shell
      (either requirements.txt or dep package)
- [x] drop github desktop by default
- [x] add dconf editor
- [x] gtk-v4l/v4l for webcams
- [x] replace firefox with flatpak or alternative browser
- [x] add vim-airline
- [x] add options for telegram
- [ ] add checksums for binary downloads
- [ ] add auto-detection of latest releases for binary installs
- [ ] add helm to kubernetes_client
- [ ] add gnome shell extensions
  - blur my shell
  - dock from dash
  - night theme switcher
  - sound input / output switcher
- [ ] add options for ms teams
- [ ] move "not-gnome" software out of gnome_applications role
- [ ] add ignore switches to flatpak/package states if useful
- [ ] add langpacks on demand

### Customization

- [ ] integrate dotfiles repository
- [ ] add aliases
- [ ] adjust language and formats
- [ ] add tmux dotfiles / config
- [ ] add tmux on login shell
- [ ] add way to sort and order application icons

### Installation

- [x] add manifest file for easy, explicit adjustments (vars file)
- [ ] add ansible-pull setup
- [ ] provide kickstart file for initial setup
- [ ] add install script

## Migrations

- [ ] move roles to a proper collection (whiletruedoio.general + desktop)

## Issues

- [ ] kubernetes_client: fix bash completion generation always done
- [ ] fix vscode extension install always done
- [ ] update role behaving weird
- [ ] add retries for failed tasks like download of binaries

## Testing

- [ ] Integration tests for the playbook
- [x] linting
- [x] syntax check

## Documentation

- [ ] variables and options
- [ ] developer docs
- [x] screenshots
- [ ] usage examples

### Later

- [ ] add podman-tui (Fedora 36)
- [ ] add snapper + auto snapshot
- [>] adjust gnome-terminal size and theme
