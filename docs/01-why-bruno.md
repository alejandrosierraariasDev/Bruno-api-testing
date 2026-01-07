# ¿Por qué Bruno?

Bruno es una herramienta de testing de APIs diseñada bajo un principio claro:
las pruebas deben vivir en el repositorio, no en una herramienta externa.
En entornos modernos —donde Git, CI/CD y automatización son la base— Bruno encaja de forma natural como alternativa ligera y eficiente a soluciones GUI-first.

## Principios clave de Bruno

### Git como fuente de la verdad
- Cada request es un archivo `.bru`
- Versionable, revisable y auditable
- Cambios visibles en PRs (diffs reales, no binarios)

### Simplicidad por diseño
- Sin cuentas
- Sin workspaces en la nube
- Sin sincronización opaca
- Sin dependencias innecesarias

### Enfoque developer & QA-friendly
- JavaScript estándar para scripting
- Curva de aprendizaje baja para perfiles técnicos
- Integración natural con flujos DevOps

## Cuándo Bruno es una buena elección

Bruno es especialmente adecuado cuando:
- Las pruebas de API forman parte del pipeline de CI/CD
- El equipo ya trabaja con Git de forma intensiva
- Se busca trazabilidad y control de cambios
- Se quiere evitar vendor lock-in
- QA y Dev comparten el mismo repositorio

## Cuándo puede no ser la mejor opción

- Exploración manual intensiva para usuarios no técnicos
- Equipos que dependen fuertemente de visualizadores o UI avanzada
- Contextos donde el testing no está integrado en el ciclo de desarrollo

## Resumen

Bruno no pretende reemplazar todas las herramientas existentes, sino resolver muy bien un problema concreto:
testing de APIs versionable, automatizable y alineado con Git y CI/CD.

> TL;DR: pruebas de API como código, en Git, listas para CI/CD.
