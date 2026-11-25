# Modelo lógico (tablas con flechas)

El mismo modelo de [logico.md](logico.md), dibujado como cajas de tabla con flechas desde la clave foránea (FK) hasta la tabla a la que apunta. **PK** = clave primaria, **UK** = valor único.
GitHub dibuja este diagrama al abrir el fichero. La imagen es `logico-tablas.png`.

```mermaid
classDiagram
  direction TB
  class CAMPUS {
    int id PK
    text nombre UK
  }
  class VERTICAL {
    int id PK
    text codigo UK
    text nombre
  }
  class PROMOCION {
    int id PK
    text nombre
    date fecha_inicio
  }
  class MODALIDAD {
    int id PK
    text nombre UK
  }
  class ROL {
    int id PK
    text nombre UK
  }
  class AULA {
    int id PK
    int campus_id FK
    text nombre
  }
  class EDICION {
    int id PK
    int vertical_id FK
    int promocion_id FK
    int campus_id FK
    int modalidad_id FK
    int aula_id FK
  }
  class ALUMNO {
    int id PK
    text nombre
    text email UK
    int edicion_id FK
  }
  class PROFESOR {
    int id PK
    text nombre
    int rol_id FK
  }
  class DOCENCIA {
    int profesor_id PK-FK
    int edicion_id PK-FK
    int modalidad_id FK
  }
  class PROYECTO {
    int id PK
    text nombre
    int vertical_id FK
  }
  class RESULTADO {
    int alumno_id PK-FK
    int proyecto_id PK-FK
    boolean apto
  }

  EDICION --> VERTICAL : vertical_id
  EDICION --> PROMOCION : promocion_id
  EDICION --> CAMPUS : campus_id
  EDICION --> MODALIDAD : modalidad_id
  EDICION --> AULA : aula_id
  AULA --> CAMPUS : campus_id
  ALUMNO --> EDICION : edicion_id
  PROFESOR --> ROL : rol_id
  DOCENCIA --> PROFESOR : profesor_id
  DOCENCIA --> EDICION : edicion_id
  DOCENCIA --> MODALIDAD : modalidad_id
  PROYECTO --> VERTICAL : vertical_id
  RESULTADO --> ALUMNO : alumno_id
  RESULTADO --> PROYECTO : proyecto_id
```

## Reglas que el diagrama no dibuja
Son las mismas de [logico.md](logico.md): `edicion` es única por (vertical, promoción, campus) y admite nulo en `modalidad_id` y `aula_id`; `promocion` es única por (nombre, fecha de inicio); `proyecto` es único por (vertical, nombre); `docencia` y `resultado` tienen clave primaria compuesta.

Estado: propuesta para revisar entre todos. Quien cambie el modelo actualiza este fichero y la imagen en el mismo commit.
