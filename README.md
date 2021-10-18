# actions-node

Composite Github Action to provides opinionated NodeJS steps

## Usage

See [action.yml](action.yml)

```yaml
steps:
  - uses: escemi-tech/actions-node@v1.0.0
```

## Inputs

### `package-manager`:

Used to specify a package managerµ. Supported values: 'yarn'.

Default: "yarn"

### `build`:

Build parameters.
Default: "build"

It can be a string to specify the script to run. Example:

```yml
steps:
  - uses: escemi-tech/actions-node@v1.0.0
    with:
      build: "build:prod"
```

It can be a json object to specify the script and / or the env variables. Example:

```yml
steps:
  - uses: escemi-tech/actions-node@v1.0.0
    with:
      build: |
        ${{ toJson(fromJson('{
          "env": {
            "NODE_ENV": "production"
          }
        }')) }}
```

It can be disabled:

```yml
steps:
  - uses: escemi-tech/actions-node@v1.0.0
    with:
      build: ""
```

### `test`:

Optional flag to enable tests steps.
Default: false

```yaml
steps:
  - uses: escemi-tech/actions-node@v1.0.0
    with:
      test: true
```

### `coverage`:

Optional flag to enable coverage report. See https://github.com/codecov/codecov-action
Deplaut false

## Steps

- Checkout
  See: https://github.com/actions/checkout

- Setup Node.js:
  See: https://github.com/actions/setup-node
  Use given package manager and version retrieve from `.nvmrc`.

- Install Dependencies
  If cache hit is not reached

- CodeQL Analysis:
  See https://github.com/github/codeql-action

- Build:
  if `build` is enabled.
  Handle gatsby cache if gastby is installed.

- Lint:
  If `test` is enabled.

- Test:
  If `test` is enabled.
  Handle Jest cache.

- Code coverage reporting:
  See https://github.com/codecov/codecov-action
  If `test` and `coverage` are enabled.

## Helping Project

❤️ If this project helps you reduce time to develop and/or you want to help the maintainer of this project. You can [sponsor](https://github.com/sponsors/neilime) him. Thank you !

## Contributing

👍 If you wish to contribute to **actions-node**, please read the [CONTRIBUTING.md](https://github.com/escemi-tech/actions-node/blob/master/CONTRIBUTING.md) file, PRs are Welcome !

## Author

🏢 **ESCEMI <contact@escemi.com>**

- Website: https://www.escemi.com
- Sponsor: [@neilime](https://github.com/sponsors/)
- Github: [@escemi-tech](https://github.com/escemi-tech)
- LinkedIn: [@escemi](https://www.linkedin.com/company/escemi)

## License

📝 Copyright © 2021 [ESCEMI <contact@escemi.com>](https://www.escemi.com).<br />
This project is [MIT](https://github.com/escemi-tech/actions-node/blob/master/LICENSE) licensed.
