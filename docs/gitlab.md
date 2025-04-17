# GitLab guidelines

## Include the component

Include the job as a Component if it is supported
or [mirrored](https://docs.gitlab.com/ee/user/project/repository/mirror/pull.html) by
your instance. This will include two jobs, one for `ruff check` and one for `ruff format`.

Add the following to your `.gitlab-ci.yml` file:

```yaml
include:
  - component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@4.0.0
```

[![Supported by GitLab.com](https://img.shields.io/badge/Supported_by-GitLab.com-orange)](https://gitlab.com)
[![Supported by Frogg.it](https://img.shields.io/badge/Supported_by-Frogg.it-green)](https://froggit.fr/)

### Inputs

You can customize the job by overriding specific inputs.

| Name           | Description                    | Default  |
|----------------|--------------------------------|----------|
| `target_paths` | Paths to directories to lint.  | `"."`    |
| `stage`        | The stage of the job.          | `test`   |
| `ruff_version` | The version of ruff to be use. | `"0.11"` |

For example:

```yml
include:
  - component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@4.0.0
    inputs:
      target_paths: "src tests dev/scripts"
      stage: lint
      ruff_version: 0.11.6
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
  - component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@4.0.0

ruff_check:
  variables:
    RUFF_CHECK_OPTIONS: "--select F401"
```

## Disable one of the two jobs

To disable one job or the other, you can add a rule:

```yml
include:
  - component: $CI_SERVER_FQDN/swepy/cicd-templates/ruff/ruff@4.0.0

ruff_format:
  rules:
    - when: never  # or `manual`
```
