# rsbx

Interactive launcher for Claude Code in [Docker Sandboxes](https://docs.docker.com/ai/sandboxes/). Opens, creates, stops and removes sandboxes via `gum` menus.

## Install

Requires macOS 14+ on Apple silicon.

```sh
brew trust docker/tap
brew bundle
sbx login
ln -s "$PWD/rsbx" ~/.local/bin/rsbx  # or any other directory on your PATH
```

## Usage

```sh
rsbx            # interactive
rsbx --dry-run  # print the sbx command instead of running it
```

Pick projects from `$GIT_PROJECTS_ROOT` (default: `~`) to mount into the sandbox VM at the same paths as on the host. Claude starts in the one you choose as primary.

Each sandbox is a separate named VM (default `claude-<project>`) with its own mounts, so you can keep one per project and run several at once. Run `rsbx` again to reopen, stop or remove them.

Before each launch, `rsbx` copies your global git `user.name` and `user.email` into the sandbox's `/etc/sandbox-persistent.sh`, so Claude's commits are authored as you rather than `agent@<sandbox>.docker.internal`.

Before each launch, `rsbx` also runs `sbx skills import --force`, copying skills from `~/.agents/skills` (then `~/.claude/skills`, `~/.cursor/skills`, etc.; the first copy of each name wins) into sbx's shared store. Sandboxes see them in `~/.claude/skills` from their next start, so stop a running sandbox (`rsbx` → Stop) to pick up new skills. Skills deleted on the host stay in the store until `sbx skills rm <name>`.
