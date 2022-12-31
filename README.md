# GitHub-hosted runners

[![Test](https://github.com/snow-actions/github-hosted-runners/actions/workflows/test.yml/badge.svg?branch=main)](https://github.com/snow-actions/github-hosted-runners/actions/workflows/test.yml)

The list of GitHub-hosted runners.

## Usage

```yml
jobs:
  runners:
    runs-on: ubuntu-latest
    outputs:
      list: ${{ steps.list.outputs.all }}
    steps:
      - id: list
        uses: snow-actions/github-hosted-runners@v1.0.0

  test:
    needs: [ runners ]
    strategy:
      fail-fast: false
      matrix:
        runner: ${{ fromJSON(needs.runners.outputs.list) }}
    runs-on: ${{ matrix.runner }}
```

## Outputs

See [action.yml](action.yml)

| Name | Description |
| - | - |
| `all` | All runners |
| `latest` | Latest runners |
| `ubuntu` | Ubuntu runners |
| `windows` | Windows runners |
| `macos` | macOS runners |

## Supported

### Runners

- `ubuntu-*`
- `windows-*`
- `macos-*`
- `self-hosted`

### Events

- Any

## Dependencies

- Bash
- cURL
- [jq](https://stedolan.github.io/jq/)
- [JSON Schema Store](https://www.schemastore.org/json/)

## Contributing

Welcome.
