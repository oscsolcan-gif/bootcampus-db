# Bitácora de pasos

Qué se ha hecho en este repositorio y en qué orden, para que cualquiera del equipo pueda seguirlo y repetirlo. Cada paso tiene su commit.
Marcado con `[x]` lo hecho y con `[ ]` lo pendiente. Quien haga un paso nuevo lo apunta aquí en el mismo commit.

## Montaje del repositorio
1. [x] **Crear el repositorio en GitHub**: público, vacío (sin README, sin `.gitignore`, sin licencia), para que el primer `push` no choque con nada.
2. [x] **Estructura base**: carpetas `docs/`, `sql/`, `data/` y `presentacion/`, cada una con un `README.md` que dice qué va dentro.
3. [x] **`.gitignore` y `.env.example`**: el `.env` con la clave de conexión queda fuera del repo; el `.env.example` es solo la plantilla.
4. [x] **`README.md`**: qué es la práctica y la lista de lo que hay que entregar, sacada del enunciado.
5. [x] **Plantillas de SQL** en `sql/`, numeradas por el orden en que se ejecutan, con un comentario de qué contiene cada una.
6. [x] **Git local**: `git init -b main` y autor con el correo `noreply` de GitHub, para no publicar el correo personal.
7. [x] **Subir el repositorio** (`git remote add origin ...` y `git push -u origin main`).
8. [ ] **Invitar al equipo**: en GitHub, *Settings → Collaborators → Add people*.

## Cómo trabajar todos sobre el mismo repo
```
git clone https://github.com/oscsolcan-gif/bootcampus-db.git
git pull                      antes de empezar a trabajar
git add <ficheros>            solo lo que has tocado
git commit -m "Paso N: qué has hecho"
git push
```
Un commit por paso, con el mensaje en esa forma, y se actualiza esta bitácora.

## Pasos del ejercicio (se rellenan al hacerlos)
9. [x] Diagrama Entidad-Relación → `docs/er.*` (patas de gallo) y `docs/er-chen.*` (rectángulos, óvalos y rombos; propuesta para revisar entre todos; quien lo cambie actualiza las dos cosas)
10. [x] Modelo lógico → `docs/logico.*` y `docs/logico-tablas.*` (cajas de tabla con flechas; propuesta para revisar entre todos; con las claves y las reglas que el diagrama no dibuja)
11. [ ] `sql/01_crear_tablas.sql`
12. [ ] `sql/02_cargar_datos.sql`
13. [ ] `sql/03_consultas_demo.sql`
14. [ ] Base de datos alojada en un servidor externo y consultable desde fuera. Antes de crearla en Render, comprobar cuánto dura la base gratuita (nuestra documentación apunta a que caduca) y probarlo todo primero en un PostgreSQL local.
15. [ ] Presentación técnica → `presentacion/`

## Lista de tareas del equipo y su estado real
La lista de progreso que compartió el equipo (`documentacion-grupo/progreso-proyecto.png`) tiene 15 tareas, y en la captura se ven 14. Este es su estado, actualizado el 25-11-2026. Fecha de entrega según la hoja de ruta: viernes 27-11-2026 a las 09:00 `{A_CONFIRMAR}`.

| Tarea | Estado | Dónde |
|---|---|---|
| Crear la base de datos del proyecto | Marcada como hecha por quien compartió la lista; no se puede comprobar desde este repo | — |
| Cargar los cinco CSV con pandas | Igual: marcada como hecha, sin comprobar | — |
| Explorar los DataFrames | En curso o pendiente, según la hoja de ruta | `documentacion-grupo/` |
| Unificar los datos de las cuatro clases | En curso o pendiente, según la hoja de ruta | — |
| Limpiar los datos | Pendiente | — |
| Identificar entidades y relaciones | Hecho (propuesta) | `docs/er-chen.md` |
| Diseñar el modelo E/R | Hecho (propuesta, dos notaciones) | `docs/er.*`, `docs/er-chen.*` |
| Diseñar el modelo lógico | Hecho (propuesta, dos formatos) | `docs/logico.*`, `docs/logico-tablas.*` |
| Crear los DataFrames normalizados | Pendiente | — |
| Crear las tablas en PostgreSQL con PK y FK | Pendiente | `sql/01_crear_tablas.sql` |
| Conectar Python con PostgreSQL | Pendiente | — |
| Importar con `df.to_sql()` | Pendiente (si se carga por SQL, va en `sql/02_cargar_datos.sql`) | — |
| Validar con consultas SQL | Pendiente | `sql/03_consultas_demo.sql` |
| Desplegar en un servidor | Pendiente | — |
| Documentar y presentar | Pendiente | `presentacion/` |
