# Bruno + GitHub: a natural integration

Bruno does not "integrate" with GitHub through plugins or external APIs.
Its integration is structural: it works because the operating model is file-based.

## What GitHub brings to a Bruno project

### Real version control
- Every change to a request is recorded
- Clear history of who changed what and why
- Simple and safe rollbacks

### Test code review
- Tests are reviewed just like code
- PR comments on:
  - Assertions
  - Variables
  - Edge cases
- Improves testing quality

### Frictionless collaboration
- No manual exports/imports
- No workspace conflicts
- No dependency on personal accounts

## Recommended repository structure

```text
bruno/
└── collections/
    └── api/
        ├── bruno.json
        ├── environments/
        │   └── local.bru
        ├── getAll.bru
        ├── getByAbility.bru
        ├── getByName.bru
        └── getByNameNotFound.bru
```

This enables:

- Clear separation of responsibilities
- Project scalability
- Fast onboarding for new members

> Note: run `bru run` inside `bruno/collections/api` (where `bruno.json` lives) or pass that path with `--env environments/local.bru`.

## Advantage over GUI-first tools

Instead of:

- Exporting collections
- Resolving conflicts manually
- Depending on cloud sync

With Bruno:

- GitHub is the collaboration mechanism
- Tests evolve alongside the code
- The repository is self-sufficient
