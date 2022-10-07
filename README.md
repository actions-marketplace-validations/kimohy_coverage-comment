# `coverage-comment` - Github Composite Action

Forked from: https://github.com/pooi/coverage-comment

**This action supports Python 2.x**

This action leave a test coverage comment on pull request.

![example](example.png)

## Input

| Name                   | Description                                                                  |
|------------------------|------------------------------------------------------------------------------|
| `github-token`         | `secrets.GITHUB_TOKEN` value                                                 |
| `xml-test-report-path` | Multiple path of `.xml` type TEST REPORT generated from `jacoco` or `kover`. |

## Example Workflow File

```yaml
jobs:
  pr-check:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v2

      ... // You must generate a test coverage report here. (e.g. ./gradlew check

      - uses: kimohy/coverage-comment@1.0.0
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          xml-test-report-path: ${SOURCE_PATH}/build/reports/kover/report.xml
```
