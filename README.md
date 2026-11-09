# rsbx

Interactive launcher for Claude Code in [Docker Sandboxes](https://docs.docker.com/ai/sandboxes/). Opens, creates, stops and removes sandboxes via `gum` menus.

## Install

Requires macOS 14+ on Apple silicon.

```sh
brew trust docker/tap
brew bundle
sbx login
ln -s "$PWD/rsbx" ~/.local/bin/rsbx
```

## Usage

```sh
rsbx            # interactive
rsbx --dry-run  # print the sbx command instead of running it
```

Projects are listed from `$GIT_PROJECTS_ROOT` (default: `~`).
