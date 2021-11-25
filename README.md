# python-template

## Setup Environment Once

1. Install system deps (Debian):

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

1. Add to `.bashrc`:

    ```sh
    export PYENV_ROOT="$HOME/.pyenv"
    export PATH="$PYENV_ROOT/bin:$PATH"

    eval "$(pyenv init --path)"
    eval "$(pyenv init -)"
    eval "$(pyenv virtualenv-init -)"
    ```

1. Install project python version as specified in `.python-version`:

    ```sh
    pyenv install
    ```

1. Install `poetry`:

    ```sh
    curl -sSL https://install.python-poetry.org | python -
    ```

1. Add to `.bashrc`:

    ```sh
    export PATH="$HOME/.poetry/bin:$PATH"
    ```

1. Install app dependancies:

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
