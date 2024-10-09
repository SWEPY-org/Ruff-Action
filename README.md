# Ruff CI/CD job

[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
[![Pipeline](https://lab.frogg.it/swepy/cicd-templates/ruff/badges/main/pipeline.svg)](https://lab.frogg.it/swepy/cicd-templates/ruff/-/pipelines)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://lab.frogg.it/swepy/cicd-templates/ruff/-/blob/main/LICENSE)

## Objective

Run [Ruff](https://github.com/astral-sh/ruff), an extremely fast Python linter, on your Python code.

## How to use it

1. [Configure ruff](https://docs.astral.sh/ruff/configuration/) for your project
2. Include the ruff component in your CI/CD pipeline (GitLab/GitHub compatible)

### GitLab

Add the following to your `.gitlab-ci.yml` file:

```yaml
include:
  - component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@3.0.0
```

[![Supported by GitLab.com](https://img.shields.io/badge/Supported_by-GitLab.com-orange)](https://gitlab.com)
[![Supported by Frogg.it](https://img.shields.io/badge/Supported_by-Frogg.it-green)](https://froggit.fr/)

See more for GitLab here: [docs/gitlab.md](docs/gitlab.md).

### GitHub

Add the following jobs to your `.github/workflows` lint file:

```yaml
jobs:
  ruff_check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: ruff check
        uses: astral-sh/ruff-action@v1
  ruff_format:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: ruff format
        uses: astral-sh/ruff-action@v1
        with:
          args: "format --check"
```

See more for GitHub here: [github/marketplace/ruff-action](https://github.com/marketplace/actions/ruff-action).

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
