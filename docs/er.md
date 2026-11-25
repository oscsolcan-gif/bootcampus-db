# Diagrama Entidad-Relación

Modelo conceptual: qué cosas existen y cómo se relacionan, sin claves ni columnas de enlace (eso es el modelo lógico, el paso siguiente).
GitHub dibuja este diagrama directamente al abrir el fichero. La imagen es `er.png`.

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
    string nombre
  }
  VERTICAL {
    string codigo
    string nombre
  }
  PROMOCION {
    string nombre
    date fecha_inicio
  }
  MODALIDAD {
    string nombre
  }
  ROL {
    string nombre
  }
  AULA {
    string nombre
  }
  ALUMNO {
    string nombre
    string email
  }
  PROFESOR {
    string nombre
  }
  PROYECTO {
    string nombre
  }
  RESULTADO {
    boolean apto
  }
```

## Cómo se lee
- **Edición** es el centro: una vertical, en una promoción, en un campus. Existe aunque no tenga alumnos o profesores.
- **Alumno** pertenece a una edición. **Profesor** da docencia en una o varias ediciones.
- **Resultado** une un alumno con un proyecto y guarda si es apto. **Docencia** une un profesor con una edición y guarda la modalidad.
- **Proyecto** pertenece a una vertical: los de Data Science y los de Full Stack son distintos.
- `|o` significa "cero o uno" (modalidad y aula son opcionales en una edición) y `}o` significa "cero o muchos".

Estado: propuesta de diseño para revisar entre todos. Quien cambie el modelo actualiza este fichero y la imagen en el mismo commit.
