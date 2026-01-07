<h1 align="center">Bruno-api-testing</h1>



<p align="center">
  <a href="https://www.usebruno.com" target="_blank">
    <img alt="Bruno" src="https://img.shields.io/badge/Bruno-API%20Testing-4F46E5?style=for-the-badge" />
  </a>
  <a href="https://nodejs.org" target="_blank">
    <img alt="Node.js" src="https://img.shields.io/badge/Node.js-18%2B-339933?style=for-the-badge&logo=node.js&logoColor=white" />
  </a>
  <a href="https://github.com/features/actions" target="_blank">
    <img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub%20Actions-CI-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" />
  </a>
  <a href="https://git-scm.com/" target="_blank">
    <img alt="Git" src="https://img.shields.io/badge/Git-Versioned-F05032?style=for-the-badge&logo=git&logoColor=white" />
  </a>
  <a href="https://developer.mozilla.org/docs/Web/JavaScript" target="_blank">
    <img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-Scripting-F7DF1E?style=for-the-badge&logo=javascript&logoColor=000" />
  </a>
  <a href="https://www.markdownguide.org/" target="_blank">
    <img alt="Markdown" src="https://img.shields.io/badge/Markdown-Docs-000000?style=for-the-badge&logo=markdown&logoColor=white" />
  </a>
</p>

Professional starter for API testing with Bruno: Git-versioned collections, JSON-based environments, simple scripting, and CI execution with GitHub Actions. Includes a Postman migration guide.

## Key features

- Versionable `.bru` files, easy to review and maintain.
- JSON environments (`local/staging/prod`).
- Standard JavaScript for `pre-request` and `assertions` scripts.
- Run via CLI (`bru run`) and CI (GitHub Actions).

## Documentation index

- [Why Bruno?](./docs/01-why-bruno.md)
- [Bruno vs Postman](./docs/02-bruno-vs-postman.md)
- [Bruno + GitHub](./docs/03-github-integration.md)
- [CI/CD execution](./docs/04-ci-execution.md)
- [Postman migration](./postman-migration/migration-guide.md)

## Requirements

- Bruno (desktop app) or Bruno CLI
- Node.js 18+
- GitHub Actions (optional, for CI)

## Verify Node and npm and install Bruno CLI

Check installed versions, then install Bruno CLI globally:

```bash
node -v
npm -v

npm install -g @usebruno/cli
```

## Installation

- Clone the repository.
- Open `bruno/collections/api` with Bruno (File → Open Collection). That folder contains the collection `bruno.json` and the environment file `environments/local.bru`.

## Quick start

- Select the `local` environment defined in `bruno/collections/api/environments/local.bru`.
- Run the requests from the `api` collection.

CLI execution:

```bash
# from repository root
bru run bruno/collections/api --env bruno/collections/api/environments/local.bru

# or from inside the collection folder
cd bruno/collections/api && bru run --env environments/local.bru
```

> Note: run `bru run` inside the collection folder that contains `bruno.json`, or pass the path to that folder. That file defines which collection to load.

## Project structure

```text
bruno-api-testing/
│
├── bruno/
│   └── collections/
│       └── api/
│           ├── bruno.json
│           ├── environments/
│           │   └── local.bru
│           ├── getAll.bru
│           ├── getByAbility.bru
│           ├── getByName.bru
│           └── getByNameNotFound.bru
│
├── .github/
│   └── workflows/
│       └── bruno-tests.yml
│
├── docs/
│   ├── 01-why-bruno.md
│   ├── 02-bruno-vs-postman.md
│   ├── 03-github-integration.md
│   └── 04-ci-execution.md
│
├── postman-migration/
│   ├── postman-collection.json
│   └── migration-guide.md
│
├── package.json
├── README.md
└── LICENSE
```

## `api` collection (PokeAPI)

- `getAll.bru`: Pokémon list (`/pokemon?limit=20&offset=0`).
- `getByName.bru`: Pokémon detail by name (`/pokemon/pikachu`).
- `getByAbility.bru`: example ability query (`/ability`).
- `getByNameNotFound.bru`: 404 case for non-existing name.

## Environments

- `bruno/collections/api/environments/local.bru` defines variables like `baseUrl` and `abilityurl`.

## CI with GitHub Actions

- Workflow in `.github/workflows/bruno-tests.yml` to run the collection in CI. See the [CI/CD guide](./docs/04-ci-execution.md).

## Postman migration

- `postman-migration/postman-collection.json`: example exported collection.
- `postman-migration/migration-guide.md`: steps to migrate to Bruno.

## License

This project is distributed under the MIT license.
