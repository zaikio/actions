# push-schema GitHub action

Build an OpenAPI schema from a local .yml file, and push it to
[zai-docs](https://github.com/zaikio/zai-docs).

## Usage

You'll need an API token with permissions to write to the zai-docs repo, it must be passed as the `token` parameter.

```yml
# .github/workflows/main.yml
---
name: Compile & push schema

on:
  push:
    branches: [main]

jobs:
  main:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - uses: zaikio/actions/push-schema@main
        with:
          schema_path: public/consumers/docs/procurement.yml
          name: procurement_consumer
          token: ${{ secrets.ZAI_DOCS_WRITE_TOKEN }}
```

For details about the other arguments, please look at the `inputs` section in the [action.yml](action.yml) file.
