# Bruno + GitHub: una integración natural

Bruno no “se integra” con GitHub mediante plugins o APIs externas.
Su integración es estructural: funciona porque el modelo de trabajo está basado en archivos.

## Qué aporta GitHub en un proyecto con Bruno

### Control de versiones real
- Cada cambio en una request queda registrado
- Historial claro de quién cambió qué y por qué
- Rollbacks simples y seguros

### Code Review de pruebas
- Las pruebas se revisan igual que el código
- Comentarios en PR sobre:
  - Assertions
  - Variables
  - Casos borde
- Mejora la calidad del testing

### Colaboración sin fricción
- No hay exports/imports manuales
- No hay conflictos de workspace
- No hay dependencias de cuentas personales

## Estructura recomendada en el repositorio

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

Esto permite:

- Separación clara de responsabilidades
- Escalabilidad del proyecto
- Onboarding rápido de nuevos miembros

> Nota: ejecuta `bru run` dentro de `bruno/collections/api` (donde está `bruno.json`) o pasa esa ruta con `--env environments/local.bru`.

## Ventaja frente a herramientas GUI-first

En lugar de:

- Exportar colecciones
- Resolver conflictos manualmente
- Depender de sincronización cloud

Con Bruno:

- GitHub es el mecanismo de colaboración
- Las pruebas evolucionan junto al código
- El repositorio es autosuficiente
