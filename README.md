<!-- start title -->

# GitHub Action:Node steps

<!-- end title -->

<!-- start description -->

Composite Github Action to provides opinionated NodeJS steps

<!-- end description -->
<!-- start contents -->
<!-- end contents -->

## Usage

<!-- start usage -->

```yaml
- uses: escemi-tech/actions-node@main
  with:
    # Checkout parameters. Must be a json object. See https://github.com/actions/checkout
    # Default: { }
    checkout: ""

    # Used to specify a package manager. Supported values: 'yarn'
    # Default: yarn
    package-manager: ""

    # Build parameters. Must be a string or a json object.
    # Default: build
    build: ""

    # Optional flag to enable check steps.
    checks: ""

    # Optional flag to enable linting
    # Default: true
    lint: ""

    # Code QL analysis language. See https://github.com/github/codeql-action
    # Default: typescript
    code-ql: ""

    # Optional flag to enable test. See https://github.com/github/codeql-action
    # Default: true
    test: ""

    # Optional flag to enable coverage report. See https://github.com/codecov/codecov-action
    # Default: true
    coverage: ""
```

<!-- end usage -->

## Steps

- Checkout:
  if `checkout` is enabled
  See: https://github.com/actions/checkout

- Setup Node.js:
  See: https://github.com/actions/setup-node
  Use given package manager and version retrieve from `.nvmrc`.

- Install Dependencies
  If cache hit is not reached

- CodeQL Analysis:
  If `checks` and `code-ql` are enabled.
  See https://github.com/github/codeql-action

- Build:
  if `build` is enabled. \
  Handle gatsby cache if gastby is installed. \
  Handle storybook cache if storybook is installed.

- Lint:
  If `checks` and `lint` are enabled.

- Test:
  If `checks` and `test` are enabled.
  Handle Jest cache.

- Code coverage reporting:
  See https://github.com/codecov/codecov-action
  If `checks` and `coverage` are enabled.

## Inputs

See [action.yml](action.yml)

<!-- start inputs -->

| **Input**             | **Description**                                                                        | **Default**  | **Required** |
| :-------------------- | :------------------------------------------------------------------------------------- | :----------: | :----------: |
| **`checkout`**        | Checkout parameters. Must be a json object. See https://github.com/actions/checkout    |    `{ }`     |  **false**   |
| **`package-manager`** | Used to specify a package manager. Supported values: 'yarn'                            |    `yarn`    |  **false**   |
| **`build`**           | Build parameters. Must be a string or a json object.                                   |   `build`    |  **false**   |
| **`checks`**          | Optional flag to enable check steps.                                                   |              |  **false**   |
| **`lint`**            | Optional flag to enable linting                                                        |    `true`    |  **false**   |
| **`code-ql`**         | Code QL analysis language. See https://github.com/github/codeql-action                 | `typescript` |  **false**   |
| **`test`**            | Optional flag to enable test. See https://github.com/github/codeql-action              |    `true`    |  **false**   |
| **`coverage`**        | Optional flag to enable coverage report. See https://github.com/codecov/codecov-action |    `true`    |  **false**   |

<!-- end inputs -->

### Examples

### `checkout`:

#### It can be a json object to specify the token to be used. Example:

```yml
steps:
  - uses: escemi-tech/actions-node@main
    with:
      checkout: '{ "token": "${{ secrets.GH_PRIVATE_ACCESS_TOKEN }}" }'
```

#### It can be a false to disabliing checkout. Example:

```yml
steps:
  - uses: escemi-tech/actions-node@main
    with:
      checkout: false
```

### `build`:

#### It can be a string to specify the script to run. Example:

```yml
steps:
  - uses: escemi-tech/actions-node@main
    with:
      build: "build:prod"
```

#### It can be a json object to specify the script and / or the env variables. Example:

```yml
steps:
  - uses: escemi-tech/actions-node@main
    with:
      build: '{ "env": { "NODE_ENV": "production" } }'
```

<!-- start outputs -->
<!-- end outputs -->

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
