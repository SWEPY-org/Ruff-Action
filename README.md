# Ruff template

[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
[![Pipeline](https://lab.frogg.it/swepy/cicd-templates/ruff/badges/main/pipeline.svg)](https://lab.frogg.it/swepy/cicd-templates/ruff/-/pipelines)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://lab.frogg.it/swepy/cicd-templates/ruff/-/blob/main/LICENSE)

<!-- TOC -->

* [Ruff template](#ruff-template)
  * [Objective](#objective)
  * [How to use it](#how-to-use-it)
  * [Variables](#variables)
    * [Global Configuration of Ruff](#global-configuration-of-ruff)
  * [Add an official ![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json) badge to your project README.md](#add-an-official--badge-to-your-project-readmemd)
  * [FAQ](#faq)
    * [Legacy Projects, logs too long](#legacy-projects-logs-too-long)

<!-- TOC -->

## Objective

Run [Ruff](https://github.com/astral-sh/ruff), an extremely fast Python linter, on your Python code.

## How to use it

1. [Configure ruff](https://docs.astral.sh/ruff/configuration/) for your project
2. Include the ruff component in your `.gitlab-ci.yml`

### Include the component/template

Add the following to your `.gitlab-ci.yml` file.

As a Component (recommended) if the component is supported
or [mirrored](https://docs.gitlab.com/ee/user/project/repository/mirror/pull.html) by
your instance:

```yaml
include:
    -   component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@1.0.2
```

[![Supported by GitLab.com](https://img.shields.io/badge/Supported_by-GitLab.com-orange)](https://gitlab.com)
[![Supported by Frogg.it](https://img.shields.io/badge/Supported_by-Frogg.it-green)](https://froggit.fr/)

As a remote Template if the component is not supported or mirrored by your instance:

```yaml
include:
    -   remote: 'https://gitlab.com/swepy/cicd-templates/ruff/-/raw/1.0.2/templates/ruff.yml'
```

## Variables

| Name           | Description                             | Default                    |
|----------------|-----------------------------------------|----------------------------|
| `IMAGE_NAME`   | The default name for the docker image.  | `"python"`                 |
| `IMAGE_TAG`    | The default tag for the docker image.   | `"latest"`                 |
| `IMAGE`        | The default docker image name.          | `"$IMAGE_NAME:$IMAGE_TAG"` |
| `PROJECT_PATH` | The path to the project root directory. | `"."`                      |
| `RUFF_CHECK`   | The command to run Ruff check.          | `"ruff check"`             |
| `RUFF_FORMAT`  | The command to run Ruff format.         | `"ruff format --check"`    |

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

## FAQ

### Legacy Projects, logs too long

> For projects that already have a lot of code that does not comply with the Ruff, the
> job will fail and the logs might be too long to be useful. How can I handle this?
