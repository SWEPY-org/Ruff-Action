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
your instance.
Variables are set with the inputs, in include section.
You can customize the job by overriding specific inputs:

```yaml
include:
  - component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@1.0.2
    inputs:
      project_path: 'path/to/my/project'
```

[![Supported by GitLab.com](https://img.shields.io/badge/Supported_by-GitLab.com-orange)](https://gitlab.com)
[![Supported by Frogg.it](https://img.shields.io/badge/Supported_by-Frogg.it-green)](https://froggit.fr/)

As a local Template (if the template is local to the instance)
Variables are set with the inputs, in include section.
You can customize the job by overriding specific inputs:

```yaml
include:
  - project: 'swepy/cicd-templates/ruff'
    ref: '$CI_COMMIT_BRANCH$CI_COMMIT_TAG'
    file: 'templates/ruff.yml'
    inputs:
      project_path: 'path/to/my/project'
```

### Inputs

| Name           | Description                             | Default    |
|----------------|-----------------------------------------|------------|
| `project_path` | The path to the project root directory. | `"."`      |
| `stage`        | The stage of the job.                   | `test`     |
| `ruff_version` | The version of ruff to be use.          | `"latest"` |

## Customize with variables

You can customize the variables job by overriding it. For example:

```yaml
ruff:
  variables:
    RUFF_CHECK_OPTIONS: "--fix"
```

## Variables

| Name                  | Description                          | Default     |
|-----------------------|--------------------------------------|-------------|
| `RUFF_CHECK_OPTIONS`  | The options for ruff check command.  | `""`        |
| `RUFF_FORMAT_OPTIONS` | The options for ruff format command. | `"--check"` |

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
