![brew](brew.png)

# Brewfile

## Installation

```sh
cd ~
git clone git@github.com:degete/brewfile.git ~/.brew

# Install all packages in `Brewfile` (required taps and packages)
brew bundle

# Selective packages by categories

# Fonts
brew bundle --file Brewfile.fonts

# CLI
brew bundle --file Brewfile.cli
brew bundle --file Brewfile.cli.git
brew bundle --file Brewfile.cli.terminals
brew bundle --file Brewfile.cli.shells
brew bundle --file Brewfile.cli.search
brew bundle --file Brewfile.cli.editors
brew bundle --file Brewfile.cli.media
brew bundle --file Brewfile.cli.monitoring
brew bundle --file Brewfile.cli.network

# Development
brew bundle --file Brewfile.dev.languages
brew bundle --file Brewfile.dev.db
brew bundle --file Brewfile.dev.ides
brew bundle --file Brewfile.dev.devops
brew bundle --file Brewfile.dev.ios
brew bundle --file Brewfile.dev.android
brew bundle --file Brewfile.dev.api
brew bundle --file Brewfile.dev.forensic
brew bundle --file Brewfile.dev.virtualization

# Apps
brew bundle --file Brewfile.apps.macos
brew bundle --file Brewfile.apps.browsers
brew bundle --file Brewfile.apps.design
brew bundle --file Brewfile.apps.office
brew bundle --file Brewfile.apps.sns
brew bundle --file Brewfile.apps.git
brew bundle --file Brewfile.apps.media

# Games
brew bundle --file Brewfile.games
```

### Avoiding dependencies

In order to avoid to install some dependencies (`mas` needs to have a valid `Apple ID account` in order to install from the `Mac App Store`), you can use the following environment variables separated by space before the commands:

- HOMEBREW_BUNDLE_TAP_SKIP
- HOMEBREW_BUNDLE_BREW_SKIP
- HOMEBREW_BUNDLE_CASK_SKIP
- HOMEBREW_BUNDLE_MAS_SKIP
- HOMEBREW_BUNDLE_WHALEBREW_SKIP

```sh
HOMEBREW_BUNDLE_MAS_SKIP brew bundle --file Brewfile.apps
```

## Packages dependencies

```sh
# Requires graphviz (dot, fdp)
brew install graphviz

brew graph --installed | dot -T png -o graph.png
brew graph --installed --highlight-leaves | fdp -T png -o graph.png
open graph.png
```

### Upstream dependencies

```sh
brew deps --installed | grep ':.*FORMULA' | awk -F':' '{print $1}'
```