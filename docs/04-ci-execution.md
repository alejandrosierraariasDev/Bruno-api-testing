# Running Bruno tests in CI/CD

One of Bruno's strengths is its simple and predictable CLI, designed to run frictionlessly in automated pipelines.

## Local execution

```bash
bru run bruno/collections/api --env bruno/collections/api/environments/local.bru
```

- Exit code 0 → tests OK
- Exit code ≠ 0 → pipeline failure

This allows integrating Bruno into any CI system without extra adapters.

> Note: run `bru run` inside the collection folder that contains `bruno.json`, or pass the path to that folder. That file defines which collection to load.

## Example with GitHub Actions

```yaml
name: Bruno API Tests

on:
  push:
    branches: [ main ]
  pull_request:

jobs:
  api-tests:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Install Bruno CLI
        run: npm install -g @usebruno/cli

      - name: Run API tests
        run: bru run bruno/collections/api --env bruno/collections/api/environments/local.bru
```

## Benefits in CI/CD

- No UI required
- No accounts required
- No personal tokens required
- Easy to parallelize
- Easy to extend (reports, artifacts, notifications)

## Comparison with traditional approaches

| Aspect | Bruno | Postman (Newman) |
| --- | --- | --- |
| CI setup | Very simple | More steps |
| Dependencies | Minimal | Newman + exports |
| Test format | Git-tracked files | Exported JSON |
| Maintainability | High | Medium |

## Conclusion

Bruno is designed to:

- Fail fast
- Integrate easily
- Be part of the pipeline, not an afterthought

In CI/CD, fewer layers mean fewer problems.
