# sls-action

Github action for serverless framework

## Inputs

| Input |                         Description |              Example | Required |
| :---- | ----------------------------------: | -------------------: | -------: |
| args  | arguments/options for `sls` command | `--stage dev deploy` |      yes |

## Example usage

```bash
uses: dragonraid/sls-action@v1
with:
  args: '--stage prod deploy'
```

## Full example

```bash
name: deploy lambda functions

on:
  push:
    branches:
      - master

env:
  AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
  AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
  AWS_DEFAULT_REGION: us-east-1

jobs:
  deploy_serverless:
    name: deploy
    runs-on: ubuntu-18.04
    steps:
      - name: clone local repository
        uses: actions/checkout@v2
      - name: npm install
        run: npm install
      - name: deploy
        uses: dragonraid/sls-action@v1
        with:
          args: --stage prod deploy
```
