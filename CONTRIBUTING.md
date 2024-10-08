# Contributing to CICD Ruff

## Useful Commands for Development

This project relies on several commands to manage dependencies and versioning
effectively. Here's a breakdown of the most important commands you should be familiar
with.

### Installation

To set up your environment and install all necessary dependencies:

```sh
pip install --upgrade pip bump-my-version pre-commit
```

### Bump version

To bump the version of the project, use the following command:

```sh
bump-my-version bump major
```

```sh
bump-my-version bump minor
```

```sh
bump-my-version bump patch
```

## Pre-commit

### install

```shell
pre-commit install
```

### test on all files

```shell
pre-commit run --all-files
```
