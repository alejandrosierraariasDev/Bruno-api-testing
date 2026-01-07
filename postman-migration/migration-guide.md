# Migración de Postman a Bruno – Ejemplo con PokeAPI

Este documento muestra cómo migrar una colección de Postman a Bruno, usando como ejemplo la API pública de Pokémon (PokeAPI). La idea es demostrar el flujo de migración, ajustes necesarios y cómo ejecutar los tests en Bruno CLI.




##  Qué demuestra esta migración

- Cómo exportar una colección desde Postman.
- Cómo importarla en Bruno.
- Cómo adaptar variables y tests.
- Cómo ejecutar la colección con Bruno CLI.
- Ventajas de Bruno frente a Postman: Git-native, CI/CD friendly, scripting en JS nativo, subtests encadenados.


---

## 1. Archivos incluidos en este repositorio

- `postman-migration/Pokemon API.postman_collection.json`  
  Exportación de Postman de ejemplo con requests a la API de Pokémon.  
- `bruno/collections/api`  
  Carpeta donde se encuentra la colección Bruno que usamos para ejecutar los tests.  
- `bruno/collections/api/environments/local.bru`  
  Variables de entorno locales para la ejecución de la colección Bruno.

> Esta estructura permite mostrar cómo importar Postman y adaptarlo a Bruno.

---

## 2. Crear o exportar la colección en Postman

Si quieres reproducir el ejemplo desde cero:

1. Abre Postman.
2. Crea una colección llamada **Pokemon API Example**.
3. Añade algunas peticiones a la API pública de Pokémon, por ejemplo:
   - `GET https://pokeapi.co/api/v2/pokemon?limit=20`
   - `GET https://pokeapi.co/api/v2/pokemon/pikachu`
   - `GET https://pokeapi.co/api/v2/pokemon/this-does-not-exist`
4. Añade tests básicos en Postman usando `pm.test()`.
5. Exporta la colección en formato **Collection v2.1** y guárdala como:

`postman-migration/Pokemon API.postman_collection.json`

> Nota: en este repositorio ya incluimos un ejemplo listo para usar.

---

## 3. Importar la colección en Bruno

1. Abre Bruno Desktop.
2. Menú → **Import → Postman Collection**.
3. Selecciona `postman-migration/Pokemon API.postman_collection.json`.
4. Bruno generará una colección con los endpoints migrados.

> Después de importar, Bruno añade automáticamente un archivo `bruno.json` en la carpeta raíz de la colección. Esto hace que la CLI reconozca la carpeta como colección raíz.

---

## 4. Ajustes necesarios después de la importación

- **Variables de entorno**: Postman usa `{{variable}}` mientras que Bruno requiere archivos `local.bru`, `staging.bru` o `prod.bru`. Asegúrate de mapear las variables.
- **Scripts de test**: Las assertions de Postman (`pm.test`) se deben reescribir en Bruno. Ejemplo de assert mínimo:

```bru
assert {
  res.status: eq 200
}
```

- **Subtests / encadenamiento**: Si tienes flujo de variables entre requests, usa `bru.setEnvVar()` y `bru.getEnvVar()` donde corresponda.

---

## 5. Validación con Bruno CLI

Para ejecutar la colección importada y comprobar que funciona:

```bash
bru run bruno/collections/api --env bruno/collections/api/environments/local.bru
```

Esto ejecuta todos los `.bru` de la colección `api`.

- El output mostrará el estado de cada test y su resultado.
- El exit code permite integrarlo fácilmente en pipelines CI/CD.

> Consejo: también puedes situarte en la carpeta de la colección y ejecutar `bru run --env environments/local.bru`.

---

## 6. Limitaciones de la importación

- Scripts complejos en Postman no siempre se migran automáticamente.
- Variables dinámicas o dependencias externas pueden requerir ajustes.
- La CLI de Bruno solo ejecuta colecciones con `bruno.json`.

Por eso es recomendable siempre crear la colección desde Bruno Desktop o guardar la colección después de importar desde Postman.

---

