# python-template

## Setup

This project uses [pyenv](https://github.com/pyenv/pyenv) and [poetry](https://github.com/python-poetry/poetry) to manage python virtual environment and dependencies. If you have a working `python` system with those tools installed then you can skip environment setup and go straight to `Install Project`. If you know what you are doing, then you can skip using `pyenv` as long as you have the version of python installed that is specified in `.python-version`.

### Setup Environment for VSCode Devcontainer/Github Codespace

1. Create a Codespace or open in VS Code locally

    Follow Github instructions to [Create a Codespace](https://docs.github.com/en/codespaces/developing-in-codespaces/creating-a-codespace) for this project, or VS Code instructions to [open repo in container](https://code.visualstudio.com/docs/remote/containers-tutorial)


### Setup Environment for Ubuntu/Debian

1. Install system deps:

    ```sh
    sudo apt-get -y install --no-install-recommends \
        build-essential \
        curl \
        libbz2-dev \
        libffi-dev \
        liblzma-dev \
        libncursesw5-dev \
        libreadline-dev \
        libsqlite3-dev \
        libssl-dev \
        libxml2-dev \
        libxmlsec1-dev \
        llvm \
        make \
        shellcheck \
        tk-dev \
        wget \
        xz-utils \
        zlib1g-dev
    ```

1. Install [pyenv](https://github.com/pyenv/pyenv) (if you haven't already):

    ```sh
    curl https://pyenv.run | bash
    ```

    Add `pyenv` paths for `bash`:

    ```sh
    {
        echo ''
        echo 'export PYENV_ROOT="$HOME/.pyenv"'
        echo 'export PATH="$PYENV_ROOT/bin:$PATH"'
        echo 'eval "$(pyenv init --path)"'
        echo 'eval "$(pyenv init -)"'
        echo 'eval "$(pyenv virtualenv-init -)"'
    } >> ~/.bashrc
    ```

    Refresh current shell with updated paths:

    ```sh
    source ~/.bashrc
    ```

    Check `pyenv` was installed correctly by verifying `python` points to `~/.pyenv/shims/python`:

    ```sh
    which python
    ```

    If you have an issue, see pyenv's [instructions](https://github.com/pyenv/pyenv#basic-github-checkout).

1. Install project python version specified in `.python-version`:

    ```sh
    pyenv install
    ```

    Check correct `python`  version was installed by verifying it matchings `.python-version`:

    ```sh
    python --version
    cat .python-version
    ```

1. Install [poetry](https://github.com/python-poetry/poetry) (if you haven't already):

    ```sh
    curl -sSL https://install.python-poetry.org | python3 -
    ```

    Add `poetry` paths for `bash`:

    ```sh
    echo 'export PATH="$HOME/.poetry/bin:$PATH"' >> ~/.bashrc
    ```

    Refresh current shell with updated paths:

    ```sh
    source ~/.bashrc
    ```

### Setup Environment for Mac

1. Install homebrew (if you don't already have it):

    ```sh
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

1. Install system deps:

    ```sh
    brew update
    brew install openssl readline xz zlib
    ```

1. Install [pyenv](https://github.com/pyenv/pyenv) (if you haven't already):

    ```sh
    brew update
    brew install pyenv
    ```

    Add `pyenv` path for `zsh` (or `~/.bashrc` if using `bash`):

    ```sh
    echo 'eval "$(pyenv init --path)"' >> ~/.zprofile
    echo 'eval "$(pyenv init -)"' >> ~/.zshrc
    ```

    Refresh current shell with updated paths:

    ```sh
    source ~/.zprofile
    source ~/.zshrc
    ```

    Check `pyenv` was installed correctly by verifying `python` points to `~/.pyenv/shims/python`:

    ```sh
    which python
    ```

    If you have an issue, see pyenv's [instructions](https://github.com/pyenv/pyenv#basic-github-checkout).

1. Install project python version specified in `.python-version`:

    ```sh
    pyenv install
    ```

    Check correct `python`  version was installed by verifying it matchings `.python-version`:

    ```sh
    python --version
    cat .python-version
    ```

1. Install [poetry](https://github.com/python-poetry/poetry) (if you haven't already):

    ```sh
    curl -sSL https://install.python-poetry.org | python3 -
    ```

    Add `poetry` path for `zsh` (or `~/.bashrc` if using `bash`):

    ```sh
    echo 'export PATH="$HOME/.poetry/bin:$PATH"' >> ~/.zshrc
    ```

    Refresh current shell with updated paths:

    ```sh
    source ~/.zshrc
    ```

### Install Project

1. Install project python version specified in `.python-version`:

    ```sh
    pyenv install
    ```

    Check correct `python`  version was installed by verifying it matchings `.python-version`:

    ```sh
    python --version
    cat .python-version
    ```

1. Install project and dependancies into local poetry managed `.venv`:

    ```sh
    poetry env use "$(cat .python-version)"
    poetry install
    ```

1. Test your installation!

    ```sh
    poetry run template-cli --help
    ```

    *or*

    ```sh
    poetry shell
    template-cli --help
    ```


1. (optional) Enable pre-commit hooks:

    ```sh
    poetry run tox -e install-hooks
    ```

# Usage

## Commands

1. Output project version

    ```python
    poetry run template-cli version
    ```

## Development

1. Run tests and linting

    ```python
    poetry run tox
    ```

1. Run tests

    ```python
    poetry run tox -qe test
    ```

1. Run linting

    ```python
    poetry run tox -qe lint
    ```
