# Talisman and detect-secrets comparison

## Steps for using this repository for a demonstration:

1. Make a copy this directory
2. Remove the `.git` directory
3. Follow the rest of this README's instructions
4. Feel free to add some information about the basic usage, pros and cons etc.

## Prerequisites

- Install pre-commit:
  https://pre-commit.com/#install
- Install Talisman:
  https://thoughtworks.github.io/talisman/docs/installation
- Install detect-secrets:
  https://github.com/Yelp/detect-secrets/#installation

## What to do

```shell
# Initialize Git:
git init
```

```shell
# Install pre-commit hooks:
pre-commmit install -f
```

```shell
# Try doing the initial commit (both Talisman and detect-secrets
# pre-commit hooks should make it fail):
git add .
git commit -m "Initial commit"
```

```shell
# Resolve by:
# 1. Adjusting and configure Talisman's `.talismanrc` file (see CLI output)
# 2. Creating baseline file for detect-secrets using this command:
detect-secrets scan --all-files > .secrets.baseline
```

```shell
# Try doing the initial commit (should be successful now):
git add .
git commit -m "Initial commit"
```

## Example CLI commands

In case you want to use the tools outside of git hooks.

```shell
# Talisman:
talisman -p "./**/*.{java}"
```

```shell
# detect-secrets
detect-secrets scan src --all-files
```

```shell
# detect-secrets for specific file while using the baseline file
detect-secrets-hook --baseline .secrets.baseline src/main/java/org/example/Main.java
```

## Links

- Talisman
    - https://github.com/thoughtworks/talisman/
    - https://thoughtworks.github.io/talisman/
- detect-secrets
    - https://github.com/Yelp/detect-secrets/
- pre-commit
    - https://github.com/pre-commit/pre-commit/
    - https://pre-commit.com/
