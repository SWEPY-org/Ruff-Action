# Ruff template

[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
[![Pipeline](https://lab.frogg.it/swepy/cicd-templates/ruff/badges/main/pipeline.svg)](https://lab.frogg.it/swepy/cicd-templates/ruff/-/pipelines)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://lab.frogg.it/swepy/cicd-templates/ruff/-/blob/main/LICENSE)

## Objective

Run [Ruff](https://github.com/astral-sh/ruff), an extremely fast Python linter, on your
Python code. This tool is written in Rust, and it is designed to quickly analyze your
Python code to detect various syntax and stylistic errors.

!!! warning If you use the venv template, make sure to include it after the ruff
template to reset its configuration to default. Otherwise, you can include this in your
`.gitlab-ci.yml` file to reset the configuration:

```yaml
venv:
rules:
    -   when: null
```

## How to use it

1. Configure the `pyproject.toml` file in your repository's root directory with your
   desired rules.
2. Include the Ruff template in your GitLab CI/CD configuration.
3. If you need to customize the job, refer to
   the [jobs customization](https://docs.r2devops.io/get-started/use-templates/#job-templates-customization)
   documentation.

## Variables

| Name           | Description                             | Default                    |
|----------------|-----------------------------------------|----------------------------|
| `IMAGE_NAME`   | The default name for the docker image.  | `"python"`                 |
| `IMAGE_TAG`    | The default tag for the docker image.   | `"latest"`                 |
| `IMAGE`        | The default docker image name.          | `"$IMAGE_NAME:$IMAGE_TAG"` |
| `PROJECT_PATH` | The path to the project root directory. | `"."`                      |
| `RUFF_CHECK`   | The command to run Ruff check.          | `"ruff check"`             |
| `RUFF_FORMAT`  | The command to run Ruff format.         | `"ruff format --check"`    |

### Global Configuration of Ruff

To add configuration to `ruff` that is shared with any other usage of Ruff (such as
manual run, pre-commit, etc), you can use a `pyproject.toml`, `ruff.toml`,
or `.ruff.toml` configuration file in your project's root directory. Learn more
about [ruff configuration](https://beta.ruff.rs/docs/configuration/) files.

## Add an official [![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff) badge to your project README.md

To display the use of Ruff in your project, you can add the following badge to your
README.md:

```markdown
[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
```

A more "classic" version of the
badge ([![Code style: Ruff](https://img.shields.io/badge/Linter-Ruff-blue)](https://github.com/astral-sh/ruff))
is also available:

```markdown
[![Code style: Ruff](https://img.shields.io/badge/Linter-Ruff-blue)](https://github.com/astral-sh/ruff)
```
