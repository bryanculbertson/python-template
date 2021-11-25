# python-template

## Setup Environment for Ubuntu/Debian

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

1. Install `pyenv`:

    ```sh
    curl https://pyenv.run | bash
    ```

1. Add `pyenv` paths for `bash`:

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

1. Install `python`:

    ```sh
    pyenv install
    ```

1. Install `poetry`:

    ```sh
    curl -sSL https://install.python-poetry.org | python3 -
    ```

1. Add `poetry` paths for `bash`:

    ```sh
    echo 'export PATH="$HOME/.poetry/bin:$PATH"' >> ~/.bashrc
    ```

## Setup Environment for Mac

1. Install `brew`:

    ```sh
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

1. Install `pyenv`:

    ```sh
    brew update
    brew install pyenv
    ```

1. Add `pyenv` path for `zsh`:

    ```sh
    echo 'eval "$(pyenv init --path)"' >> ~/.zprofile
    echo 'eval "$(pyenv init -)"' >> ~/.zshrc
    ```

1. Install `python`:

    ```sh
    pyenv install
    ```

1. Install `poetry`:

    ```sh
    curl -sSL https://install.python-poetry.org | python3 -
    ```

1. Add `poetry` path for `zsh`

    ```sh
    echo 'export PATH="$HOME/.poetry/bin:$PATH"' >> ~/.zshrc
    ```

## Setup Project Environment

1. Install project python version specified in `.python-version`:

    ```sh
    pyenv install
    ```

1. Install project dependancies into project virtualenv:

    ```sh
    poetry env use "$(cat .python-version)"
    poetry install
    ```

1. (optional) Enable pre-commit hooks:

    ```sh
    poetry run tox -e install-hooks
    ```

## Run Commands

1. Output code version

    ```python
    poetry run template-cli version
    ```

## Development Commands

1. Run test and linting

    ```python
    poetry run tox
    ```

1. Run tests

    ```python
    poetry run tox -e test
    ```

1. Run linting

    ```python
    poetry run tox -e lint
    ```
