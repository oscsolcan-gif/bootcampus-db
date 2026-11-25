# Modelo lógico

Las tablas con sus columnas, claves primarias (PK), claves foráneas (FK) y valores únicos (UK), a partir del diagrama Entidad-Relación de [er.md](er.md).
GitHub dibuja este diagrama al abrir el fichero. La imagen es `logico.png`.

```mermaid
erDiagram
  CAMPUS ||--o{ EDICION : acoge
  VERTICAL ||--o{ EDICION : tiene
  PROMOCION ||--o{ EDICION : agrupa
  MODALIDAD |o--o{ EDICION : ofrece
  AULA |o--o{ EDICION : usa
  CAMPUS ||--o{ AULA : contiene
  EDICION ||--o{ ALUMNO : matricula
  VERTICAL ||--o{ PROYECTO : define
  ALUMNO ||--o{ RESULTADO : obtiene
  PROYECTO ||--o{ RESULTADO : evalua
  ROL ||--o{ PROFESOR : clasifica
  PROFESOR ||--o{ DOCENCIA : imparte
  EDICION ||--o{ DOCENCIA : recibe
  MODALIDAD ||--o{ DOCENCIA : modo

  CAMPUS {
    int id PK
    string nombre UK
  }
  VERTICAL {
    int id PK
    string codigo UK
    string nombre
  }
  PROMOCION {
    int id PK
    string nombre
    date fecha_inicio
  }
  MODALIDAD {
    int id PK
    string nombre UK
  }
  ROL {
    int id PK
    string nombre UK
  }
  AULA {
    int id PK
    int campus_id FK
    string nombre
  }
  EDICION {
    int id PK
    int vertical_id FK
    int promocion_id FK
    int campus_id FK
    int modalidad_id FK
    int aula_id FK
  }
  ALUMNO {
    int id PK
    string nombre
    string email UK
    int edicion_id FK
  }
  PROFESOR {
    int id PK
    string nombre
    int rol_id FK
  }
  DOCENCIA {
    int profesor_id PK, FK
    int edicion_id PK, FK
    int modalidad_id FK
  }
  PROYECTO {
    int id PK
    string nombre
    int vertical_id FK
  }
  RESULTADO {
    int alumno_id PK, FK
    int proyecto_id PK, FK
    boolean apto
  }
```

## Reglas que el diagrama no dibuja
| Tabla | Regla |
|---|---|
| `promocion` | único (nombre, fecha_inicio) |
| `edicion` | único (vertical_id, promocion_id, campus_id); `modalidad_id` y `aula_id` admiten nulo |
| `proyecto` | único (vertical_id, nombre) |
| `docencia` | clave primaria compuesta (profesor_id, edicion_id) |
| `resultado` | clave primaria compuesta (alumno_id, proyecto_id) |
| `alumno` | `edicion_id` obligatorio |
| Todas | los campos `nombre` son obligatorios |

## Qué debe salir al cargar los datos
`edicion` 6 · `alumno` 52 · `profesor` 10 · `docencia` 10 · `proyecto` 10 · `resultado` 260 · `campus` 2 · `vertical` 2 · `promocion` 2 · `modalidad` 2 · `rol` 2 · `aula` 0.

## Orden de creación y de carga
Las claves foráneas lo marcan: catálogos (`campus`, `vertical`, `promocion`, `modalidad`, `rol`, `aula`), luego `proyecto` y `edicion`, después `profesor` y `alumno`, y al final `docencia` y `resultado`.

Estado: propuesta para revisar entre todos. Quien cambie el modelo actualiza este fichero y la imagen en el mismo commit.
