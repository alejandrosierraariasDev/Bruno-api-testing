# Why Bruno?

Bruno is an API testing tool designed with a clear principle:
tests should live in the repository, not in an external tool.
In modern environments—where Git, CI/CD, and automation are the foundation—Bruno is a lightweight, efficient alternative to GUI-first solutions.

## Key principles of Bruno

### Git as the source of truth
- Each request is a `.bru` file
- Versionable, reviewable, and auditable
- Real diffs in PRs (no binaries)

### Simplicity by design
- No accounts
- No cloud workspaces
- No opaque sync
- No unnecessary dependencies

### Developer & QA-friendly
- Standard JavaScript for scripting
- Low learning curve for technical profiles
- Natural integration with DevOps workflows

## When Bruno is a good fit

Bruno is especially suitable when:
- API tests are part of the CI/CD pipeline
- The team already works heavily with Git
- Traceability and change control are required
- You want to avoid vendor lock-in
- QA and Dev share the same repository

## When it may not be the best option

- Heavy manual exploration for non-technical users
- Teams that rely heavily on visualizers or advanced UI
- Contexts where testing is not integrated into the dev cycle

## Summary

Bruno does not aim to replace every tool, but to do one thing exceptionally well:
versionable, automatable API testing aligned with Git and CI/CD.

> TL;DR: API tests as code, in Git, ready for CI/CD.
