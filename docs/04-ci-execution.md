# Ejecución de pruebas Bruno en CI/CD

Uno de los puntos fuertes de Bruno es su CLI simple y predecible, diseñada para ejecutarse sin fricción en pipelines automatizados.

## Ejecución local

```bash
bru run bruno/collections/api --env bruno/collections/api/environments/local.bru
```

- Exit code 0 → tests OK
- Exit code ≠ 0 → fallo en pipeline

Esto permite integrar Bruno en cualquier sistema CI sin adaptadores adicionales.

> Nota: ejecuta `bru run` dentro de la carpeta de la colección que contiene `bruno.json`, o pasa la ruta a esa carpeta. Ese archivo define qué colección cargar.

## Ejemplo con GitHub Actions

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

## Beneficios en CI/CD

- No requiere UI
- No requiere cuentas
- No requiere tokens personales
- Fácil de paralelizar
- Fácil de extender (reports, artefacts, notificaciones)

## Comparativa con enfoques tradicionales

| Aspecto | Bruno | Postman (Newman) |
| --- | --- | --- |
| Setup en CI | Muy simple | Más pasos |
| Dependencias | Mínimas | Newman + exports |
| Formato tests | Archivos Git | JSON exportado |
| Mantenibilidad | Alta | Media |

## Conclusión

Bruno está pensado para:

- Fallar rápido
- Integrarse fácilmente
- Ser parte del pipeline, no un añadido posterior

En CI/CD, menos capas significa menos problemas.
