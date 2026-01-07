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

Starter profesional para testing de APIs con Bruno: colecciones versionables en Git, entornos por JSON, scripting sencillo y ejecución en CI con GitHub Actions. Incluye guía de migración desde Postman.

## Características clave

- Archivos `.bru` versionables, revisables y fáciles de mantener.
- Entornos `local/staging/prod` en JSON.
- Scripts de `pre-request` y `assertions` en JavaScript estándar.
- Ejecución por CLI (`bru run`) y en CI (GitHub Actions).

## Índice de documentación

- [¿Por qué Bruno?](./docs/01-why-bruno.md)
- [Bruno vs Postman](./docs/02-bruno-vs-postman.md)
- [Bruno + GitHub](./docs/03-github-integration.md)
- [Ejecución en CI/CD](./docs/04-ci-execution.md)
- [Migración desde Postman](./postman-migration/migration-guide.md)

## Requisitos

- Bruno (app de escritorio) o Bruno CLI
- Node.js 18+
- GitHub Actions (opcional, para CI)

## Verificar Node y npm e instalar Bruno CLI

Comprueba las versiones instaladas y luego instala Bruno CLI de forma global:

```bash
node -v
npm -v

npm install -g @usebruno/cli
```

## Instalación

- Clona el repositorio.
- Abre la carpeta `bruno/collections/api` con Bruno (File → Open Collection). Esa carpeta contiene el `bruno.json` de la colección y el entorno en `environments/local.bru`.

## Uso rápido

- Selecciona el entorno `local` definido en `bruno/collections/api/environments/local.bru`.
- Ejecuta las requests de la colección `api`.

Ejecución por CLI:

```bash
# desde la raíz del repo
bru run bruno/collections/api --env bruno/collections/api/environments/local.bru

# ó situándote dentro de la carpeta de la colección
cd bruno/collections/api && bru run --env environments/local.bru
```

> Nota: ejecuta `bru run` dentro de la carpeta de la colección que contiene `bruno.json`, o pasa la ruta a esa carpeta. Ese archivo define qué colección cargar.

## Estructura del proyecto

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

## Colección `api` (PokeAPI)

- `getAll.bru`: lista de Pokémon (`/pokemon?limit=20&offset=0`).
- `getByName.bru`: detalle de un Pokémon por nombre (`/pokemon/pikachu`).
- `getByAbility.bru`: ejemplo de consulta de habilidad (`/ability`).
- `getByNameNotFound.bru`: caso 404 para nombre inexistente.

## Entornos

- `bruno/collections/api/environments/local.bru` define variables como `baseUrl` y `abilityurl`.

## CI con GitHub Actions

- Workflow en `.github/workflows/bruno-tests.yml` para ejecutar pruebas de colección en CI. Ver [guía de CI/CD](./docs/04-ci-execution.md).

## Migración desde Postman

- `postman-migration/postman-collection.json`: ejemplo de colección exportada.
- `postman-migration/migration-guide.md`: pasos para convertir a Bruno.

## Licencia

Este proyecto se distribuye bajo la licencia MIT.
