# expo-workflows

Reusable GitHub Actions workflows for Expo projects. Handles Bun setup and dependency installation, while each project specifies its own commands.

## Workflows

### Lint

Checkout + Bun setup + install, then runs the given commands.

```yaml
name: Lint
on: [push]
jobs:
  lint:
    uses: tzwzx/expo-workflows/.github/workflows/lint.yml@main
    with:
      commands: |
        bun lint
        bun tsc
        bun syncpack:lint
        bun knip
```

### Test

Checkout + Bun setup + install + Playwright browsers, then runs the given commands.

```yaml
name: Test
on: [push]
jobs:
  test:
    uses: tzwzx/expo-workflows/.github/workflows/test.yml@main
    with:
      commands: |
        bun test:unit
        bun test:e2e:web
```

## Inputs

| Workflow | Input | Required | Description |
|----------|-------|----------|-------------|
| lint | `commands` | Yes | Commands to run (newline-separated) |
| test | `commands` | Yes | Commands to run (newline-separated) |

## What's shared

- `actions/checkout@v6`
- `oven-sh/setup-bun@v2` (latest)
- `bun install --frozen-lockfile`
- Playwright browser install (test only)

## License

MIT
