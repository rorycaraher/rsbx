# rsbx

Interactive launcher for running Claude Code in [Docker Sandboxes](https://docs.docker.com/ai/sandboxes/).

`rsbx` opens an existing sandbox, or walks you through creating one: which
projects to mount, the primary workspace, read-only mounts, the sandbox name,
clone mode and resource limits. It can also stop and remove sandboxes.

## Install

Requires macOS 14+ on Apple silicon for local sandboxes.

```sh
brew install gum
brew trust docker/tap
brew install docker/tap/sbx
sbx login
ln -s "$PWD/rsbx" ~/.local/bin/rsbx
```

## Usage

```sh
rsbx            # interactive
rsbx --dry-run  # print the launch command instead of running it
```

Projects are the subdirectories of `~/workspace`; set `RSBX_PROJECTS_DIR` to
list a different directory. Pick `+ other path...` to mount anything else. If
you run `rsbx` from inside a project, that project starts selected.

The primary workspace is always writable, and Claude starts there. Clone mode
is offered only when the primary workspace is a Git repository, and it can't be
changed after creation.

Each workspace appears in the sandbox at the same absolute path as on the host.
