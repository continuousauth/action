# Continuous Auth GitHub Action

> CFA via Semantic Release in a simple action

## Example

```yaml
name: Publish

on: [push]

permissions:
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    environment: npm
    steps:
      # For security please pin this to the SHA of the latest release
      #  - https://github.com/actions/checkout/releases/latest
      - uses: actions/checkout@{sha}
        with:
          # This is key, ensure that you set this on your checkout
          persist-credentials: false
      # For security please pin this to the SHA of the latest release
      #  - https://github.com/continuousauth/action/releases/latest
      - uses: continuousauth/action@{sha}
        with:
          project-id: ${{ secrets.CFA_PROJECT_ID }}
          secret: ${{ secrets.CFA_SECRET }}
          npm-token: ${{ secrets.NPM_TOKEN }}


```