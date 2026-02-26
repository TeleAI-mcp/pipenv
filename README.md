# Pipenv: Python Development Workflow for Humans

[![image](https://img.shields.io/pypi/v/pipenv.svg)](https://python.org/pypi/pipenv)
[![image](https://img.shields.io/pypi/l/pipenv.svg)](https://python.org/pypi/pipenv)
[![image](https://img.shields.io/pypi/pyversions/pipenv.svg)](https://python.org/pypi/pipenv)
[![image](https://img.shields.io/badge/Say%20Thanks-!-1EAEDB.svg)](https://saythanks.io/to/kennethreitz)

**Pipenv** is a Python virtualenv management tool that supports a multitude of systems and nicely bridges the gaps between pip, python (using system python, pyenv or asdf) and virtualenv.

Linux/Unix and Windows are both first-class citizens in our world.

It automatically creates and manages a virtualenv for your projects, as well as adds/removes packages from your `Pipfile` as you install/uninstall packages. It also generates the ever-important `Pipfile.lock`, which is used to produce deterministic builds.

![image](https://s3.amazonaws.com/media.kennethreitz.com/pipenv.svg)

The problems that Pipenv seeks to solve are multi-faceted:

- You no longer need to use `pip` and `virtualenv` separately. They work together.
- Managing a `requirements.txt` file [can be problematic](https://kennethreitz.org/essays/a-better-pip-workflow), so Pipenv uses `Pipfile` and `Pipfile.lock` instead.
- Virtualenv location is no longer a concern. In the spirit of XDG Base Directory Specification, on Linux it goes in `~/.local/share/virtualenvs/`, while on Windows it goes in `%LOCALAPPDATA%\\virtualenvs\\`.
- Hashes are used everywhere, always. Security. Automatically expose security vulnerabilities.
- Strongly encourage updating of the lock file as security vulnerabilities are patched in dependencies and subdependencies.
- Give you insight into your dependency graph (e.g. `$ pipenv graph`).
- Streamline development workflow by loading `.env` files automatically.

Install Pipenv Today!
=====================

If you\'re on MacOS, you can install Pipenv easily with Homebrew. Or, if you\'re using Fedora Linux, it\'s as simple as:

```bash
$ sudo dnf install pipenv
```

Or, if you\'re using FreeBSD:

```bash
# pkg install py311-pipenv
```

Or, if you\'re on a system with only python3 and pip3 installed:

```bash
$ pip3 install --user pipenv
```

Otherwise, just use pip:

```bash
$ pip install --user pipenv
```

☤ User Testimonials
===================

**David Gang**---\ *This package is amazing. I wish I had found it sooner.*

**A. Ishikawa**---\ *Thanks for replacing virtualenv and pip with one command, reducing context switching.*

**Justin Myles Holmes**---\ * Pipenv is a production-ready tool that brings the best of all packaging worlds to Python.*

**Lauri J. Talvitie**---\ *Simplifies and unifies Python packaging and environment management; no longer need to separately manage requirements files, virtualenv, and pip.*

☤ Pipenv & Virtual Environments
===============================

This is a convenience for invoking the pipenv run command from any location by utilizing the "--rm" flag to auto-create and auto-destroy a virtual environment around the command.  Additionally it provides a quick way to run your python module or script in an isolated environment:

```bash
$ pipenv run --rm python -m pytest
$ pipenv run --rm python my_script.py
```

This will create a temporary virtualenv, install your Pipfile/Pipfile.lock into it, run your command, and then remove the virtualenv.

☤ Pipenv Features
=================

- Enables truly *deterministic builds*, while easily specifying only the sub-dependencies you actually need.
- Generates and checks file hashes for locked dependencies.
- Automatically install required Python versions (with asdf/pyenv support).
- Automatically finds your project home, recursively, by looking for a `Pipfile`.
- Automatically generates a `Pipfile`, if one doesn\'t exist.
- Automatically creates a virtualenv in a standard location.
- Automatically adds/removes packages to a `Pipfile` when they are uninstalled.
- Automatically loads `.env` files, when they exist.

The main commands are `install`, `uninstall`, and `lock`, which generates a `Pipfile.lock`. These are intended to replace `$ pip install` usage, as well as manual virtualenv management (to activate a virtualenv, run `$ pipenv shell`).

☤ Basic Concepts
================

- A virtualenv will automatically be created, when one doesn\'t exist.
- When no parameters are passed to `install`, all packages specified will be installed.
- To initialize Python 3 (or 2) specifically, use the `--three` (`--two`) flags. This is not needed as of Pipenv 2023.7.11 where we adopted PEP-514 discovery on Windows, making `--three` unnecessary.
- Otherwise, whatever `python` is discovered in your path will be the default.

☤ Other Commands
================

- `shell` will spawn a shell with the virtualenv activated.
- `run` will run a given command from the virtualenv, with any arguments forwarded (e.g. `$ pipenv run python`).
- `check` asserts that PEP 508 markers are provided in Pipfile and asserts security against Pipfile.lock.
- `graph` will show you a dependency graph, of your installed dependencies.

☤ Shell Completion
==================

To enable completion in fish:

```bash
$ eval (env _PIPENV_COMPLETE=source_fish pipenv)
```

To enable completion in bash:

```bash
$ eval "$(_PIPENV_COMPLETE=source_bash pipenv)"
```

To enable completion in zsh:

```bash
$ eval "$(_PIPENV_COMPLETE=source_zsh pipenv)"
```

Alternatively, if you use [dotenv](https://github.com/theskumar/python-dotenv) to manage your environment variables, you can use the following one-liner to add the completion code to your shell config file:

```bash
$ echo 'eval "$(_PIPENV_COMPLETE=source_zsh pipenv)"' >> ~/.zshrc
```

Or, for fish:

```bash
$ echo 'eval (env _PIPENV_COMPLETE=source_fish pipenv)' >> ~/.config/fish/config.fish
```

☤ Usage
=======

```bash
$ pipenv --help
Usage: pipenv [OPTIONS] COMMAND [ARGS]...

Options:
  --python TEXT       Specify which version of Python virtualenv should use.
  --three             Use Python 3 when creating virtualenv.
  --two               Use Python 2 when creating virtualenv.
  -h, --help          Show this message and exit.
  --version           Show the version and exit.

Commands:
  check      Checks for security vulnerabilities and against PEP 508 markers
  graph      Displays currently-installed dependency graph information.
  install    Installs provided packages and adds them to Pipfile, or (if none is given), installs all packages from Pipfile.
  lock       Generates Pipfile.lock.
  open       View a given module in your editor.
  run        Spawns a command installed into the virtualenv.
  shell      Spawns a shell with the virtualenv activated.
  sync       Installs all packages specified in Pipfile.lock.
  uninstall  Un-installs a provided package and removes it from Pipfile.
  update     Uninstalls all packages and re-installs package(s) in Pipfile[.lock] to latest compatible versions.
```

☤ Documentation
===============

Documentation resides over at [pipenv.pypa.io](https://pipenv.pypa.io/).

## Related Projects

1. related project [poetry](https://github.com/python-poetry/poetry)
2. related project [rye](https://github.com/astral-sh/rye)