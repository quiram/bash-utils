# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A collection of Bash utility scripts organized by category (git, build, docker, java, os, etc.). Scripts are made available on `$PATH` by sourcing `add-to-path`, which adds every subdirectory to `PATH`.

## Setup

```bash
./make-available        # Appends `source <repo>/add-to-path` to ~/.bashrc or ~/.bash_profile
source ~/.bashrc        # Reload shell to activate
```

## Architecture

- **`add-to-path`** — Sourced at shell startup; adds all subdirectories to `$PATH`.
- **`make-available`** — One-time setup script that registers `add-to-path` in the user's shell profile.
- **`common/utils`** — Shared library sourced by most scripts. Provides `log()`, `fail()`, and `silentExec()` helpers. `fail()` terminates the top-level script (not just a subshell) via a `TERM` trap.
- **`git/utils`** — Git-specific shared library. Detects whether the default branch is `main` or `master` and exports it as `$main`.

## Before pushing to GitHub

Use `pushcode` instead of `git push`. It pulls latest changes, runs the build, and then pushes. If the build fails because there are no defined tests, re-run with `pushcode --skip-build`.

## Script conventions

- Every script resolves its own directory via `BUILD_SCRIPTS_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"` to allow sourcing sibling files reliably.
- Scripts source `common/utils` or `git/utils` (never both directly — `git/utils` already sources `common/utils`).
- Usage is documented in a comment block at the top of each script.
- Many scripts support configuration via environment variables (check the comment header of each script).
- Scripts that depend on `$main` (the default branch name) must source `git/utils`, which sets that variable.
