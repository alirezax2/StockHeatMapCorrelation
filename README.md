# StockHeatMapCorrelation
A docker based web app to show correlation between stocks and sectors as a heat map


# UV Command Line Tool

The `uv` command line tool is a powerful utility for managing Python projects, virtual environments, and dependencies. Below is a guide to the commands and their functionalities.

## Installation

To install `uv`, run the following command in your terminal:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

After installation, you can verify the installation by checking the version:

```bash
uv --version
```

## Initializing a Project

To initialize a new Python project, navigate to your project directory and run:

```bash
uv init .
```

This command will create a `pyproject.toml` file in the current directory and set up a `.venv` virtual environment folder.

## Adding Dependencies

To add a dependency, such as `requests`, to your project, use the following command:

```bash
uv add requests
```

This will add `requests` to the `pyproject.toml` file and install it in the virtual environment.

## Managing the Virtual Environment

To activate the virtual environment, use:

```bash
source .venv/bin/activate
```

To deactivate the virtual environment, simply run:

```bash
deactivate
```

## Dependency Management

### Listing Installed Packages

To list all installed packages and their versions, use:

```bash
uv pip freeze
```

To list installed packages without versions, use:

```bash
uv pip list
```

### Displaying Dependency Tree

To display a tree of dependencies, use:

```bash
uv pip tree
```

### Syncing Environment with Lockfile

To sync your environment with a lockfile, use:

```bash
uv pip sync
```

### Installing Packages

To install a package, such as `requests`, use:

```bash
uv pip install requests
```

### Showing Package Information

To show detailed information about a package, use:

```bash
uv pip show <package_name>
```

### Compiling Requirements

To compile dependencies from `pyproject.toml` into a `requirements.txt` file, use:

```bash
uv pip compile pyproject.toml -o requirements.txt
```



