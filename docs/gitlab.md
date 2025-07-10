# GitLab guidelines

## Include the component

Add the following to your `.gitlab-ci.yml` file:

```yaml
include:
  - component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@5.0.0
```

[![Supported by GitLab.com](https://img.shields.io/badge/Supported_by-GitLab.com-orange)](https://gitlab.com)
[![Supported by Frogg.it](https://img.shields.io/badge/Supported_by-Frogg.it-green)](https://froggit.fr/)

### Component inputs

| Name                                           | Description                        | Default                                    |
|------------------------------------------------|------------------------------------|--------------------------------------------|
| `image`                                        | Image for the job.                 | `ghcr.io/astral-sh/ruff:0.12.2-alpine3.21` |
| `stage`                                        | Stage of the job.                  | `test`                                     |
| `target-paths`/`TARGET_PATHS`                  | Directories to lint.               | `.`                                        |
| `options`/`RUFF_OPTIONS`                       | For both format and check commands | `""`                                       |
| `check-options`/`RUFF_CHECK_DEFAULT_OPTIONS`   | For all check jobs                 | `""`                                       |
| `format-options`/`RUFF_FORMAT_DEFAULT_OPTIONS` | For all format jobs                | `--check`                                  |
| `RUFF_CHECK_OPTIONS`                           | For specific check job             | `""`                                       |
| `RUFF_FORMAT_OPTIONS`                          | For specific format job            | `""`                                       |

For example:

```yml
include:
  - component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@5.0.0
    inputs:
      target-paths: "src tests dev/scripts"
      stage: lint
```

## Customize with variables

You can customize the variables job by overriding it.

| Name                  | Description                          | Default     |
|-----------------------|--------------------------------------|-------------|
| `RUFF_CHECK_OPTIONS`  | The options for ruff check command.  | `""`        |
| `RUFF_FORMAT_OPTIONS` | The options for ruff format command. | `"--check"` |

For example:

```yaml
include:
  - component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@5.0.0

ruff_check:
  variables:
    RUFF_CHECK_OPTIONS: "--select F401"
```

## Disable one of the two jobs

To disable one job or the other, you can add a rule:

```yml
include:
  - component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@5.0.0

ruff_format:
  rules:
    - when: never  # or `manual`
```
