# Changelog

All notable changes to this job will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

[![Pipeline](https://gitlab.com/swepy/cicd-templates/ruff/badges/trunk/pipeline.svg)](https://gitlab.com/swepy/cicd-templates/ruff/-/pipelines)

### Added

* inputs:
  * `image` used by the job, default to `ghcr.io/astral-sh/ruff:0.12.2-alpine3.21`
  * `check-options` for check command, default to `--output-format gitlab`
  * `format-options` for format command, default to `--diff`

### Changed

* inputs:
  * `target_paths` renamed `target-paths`
  * `ruff_global_options` renamed `options`
* variables:
  * `TARGET_PATHS` renamed `RUFF_TARGET_PATHS`
  * `RUFF_CHECK_DEFAULT_OPTIONS` changed default to `$[[ inputs.check-options ]]`
  * `RUFF_FORMAT_DEFAULT_OPTIONS` changed default to `$[[ inputs.format-options ]]`
* `ruff_check`:
  * renamed `ruff:check`
  * now create an artefact `code-quality-report.json` used by gitlab
* `ruff_format` renamed `ruff:format`

### Removed

* inputs:
  * `ruff_version`
* variables:
  * `RUFF_VERSION`

## [4.0.0] - 2025-04-17

[![Pipeline](https://gitlab.com/swepy/cicd-templates/ruff/badges/4.0.0/pipeline.svg)](https://gitlab.com/swepy/cicd-templates/ruff/-/pipelines)

### Changed

* ruff_version default now to "0.11"
* image now point to official ghcr.io/astral-sh/ruff:{$RUFF_VERSION}-alpine
* Copyright now range up to 2025

## [3.0.0] - 2024-10-09

[![Pipeline](https://gitlab.com/swepy/cicd-templates/ruff/badges/3.0.0/pipeline.svg)](https://gitlab.com/swepy/cicd-templates/ruff/-/pipelines)

### Changed

* `ruff` job split into `ruff_check` and `ruff_format` jobs

### Removed

* No more action, now redirect to the official GitHub Action from Astral-sh

## [2.0.0] - 2024-10-07

[![Pipeline](https://gitlab.com/swepy/cicd-templates/ruff/badges/2.0.0/pipeline.svg)](https://gitlab.com/swepy/cicd-templates/ruff/-/pipelines)

* A new test that ensure that the job fails on miss-formated projects

### Added

* GitHub Action support

### Changed

* Move command `cd $PROJECT_PATH` from `before_script` to `script` section of the component
* `project_path` has been renamed `target_paths` and can contain multiple path i.e. "src tests dev/scripts"

## [1.0.2] - 2024-04-09

[![Pipeline](https://gitlab.com/swepy/cicd-templates/ruff/badges/ruff@1.0.2/pipeline.svg)](https://gitlab.com/swepy/cicd-templates/ruff/-/pipelines)

### Fixed

* README.me, formatting and variables

## [1.0.1] - 2024-04-06

[![Pipeline](https://gitlab.com/swepy/cicd-templates/ruff/badges/ruff@1.0.1/pipeline.svg)](https://gitlab.com/swepy/cicd-templates/ruff/-/pipelines)

### Changed

* Upgrade dependencies
  to [venv template](https://r2devops.io/marketplace/gitlab/swepy/cicd-templates/venv/venv)

## [1.0.0] - 2024-04-06

[![Pipeline](https://gitlab.com/swepy/cicd-templates/ruff/badges/ruff@1.0.0/pipeline.svg)](https://gitlab.com/swepy/cicd-templates/ruff/-/pipelines)

### Changed

* Template CICD validation include. It now includes the job from the current host and
  project path to handle forks

## [0.2.0] - 2024-04-06

[![Pipeline](https://gitlab.com/swepy/cicd-templates/ruff/badges/ruff@0.2.0/pipeline.svg)](https://gitlab.com/swepy/cicd-templates/ruff/-/pipelines)

### Added

* Ruff configuration to run ruff formatter
* MIT license attached to the template

## [0.1.0] - 2024-04-05

[![Pipeline](https://gitlab.com/swepy/cicd-templates/ruff/badges/ruff@0.1.0/pipeline.svg)](https://gitlab.com/swepy/cicd-templates/ruff/-/pipelines)

* Initial version
