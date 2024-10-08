# Github guidelines

## Include the component/template

Add the following to your `.github/workflows/lint.yml` file (or any other workflow name).

```yaml
name: Lint

on: [ push ]

jobs:
  ruff:
    runs-on: ubuntu-latest
    container:
      image: swepy/ruff:latest
      options: --user root
    steps:
      - uses: SWEPY-org/ruff@2.0.0
```

### Inputs

You can customize the job by overriding specific inputs.

| Name           | Description                   | Default |
|----------------|-------------------------------|---------|
| `target_paths` | Paths to directories to lint. | `"."`   |

For example:

```yaml
name: Lint

on: [ push ]

jobs:
  ruff:
    runs-on: ubuntu-latest
    container:
      image: swepy/ruff:latest
      options: --user root
    steps:
      - uses: SWEPY-org/ruff@2.0.0
        with:
          target_paths: src tests dev/scripts
```

## Customize with variables

You can customize the variables job by overriding it.

| Name                  | Description                          | Default     |
|-----------------------|--------------------------------------|-------------|
| `RUFF_CHECK_OPTIONS`  | The options for ruff check command.  | `""`        |
| `RUFF_FORMAT_OPTIONS` | The options for ruff format command. | `"--check"` |

For example:

```yaml
name: Lint

on: [ push ]

jobs:
  ruff:
    runs-on: ubuntu-latest
    container:
      image: swepy/ruff:latest
      options: --user root
    steps:
      - uses: SWEPY-org/ruff@2.0.0
        env:
          RUFF_CHECK_OPTIONS: --select F401
```
