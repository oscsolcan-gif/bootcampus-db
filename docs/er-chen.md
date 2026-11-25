# Diagrama Entidad-Relación (notación clásica)

El mismo modelo de [er.md](er.md), dibujado como en clase: **rectángulos** para las entidades, **rombos** para las relaciones y **óvalos** para los atributos. El número junto a cada línea es la cardinalidad (1 = uno, N y M = muchos).
GitHub dibuja este diagrama al abrir el fichero. La imagen es `er-chen.png`.

```mermaid
flowchart TB
  classDef ent fill:#E8EEF9,stroke:#1F3A93,stroke-width:2px,color:#000
  classDef rel fill:#FFF4D6,stroke:#B7791F,stroke-width:2px,color:#000
  classDef att fill:#FFFFFF,stroke:#555555,color:#000

  CAMPUS[CAMPUS]:::ent
  VERTICAL[VERTICAL]:::ent
  PROMOCION[PROMOCIÓN]:::ent
  MODALIDAD[MODALIDAD]:::ent
  ROL[ROL]:::ent
  AULA[AULA]:::ent
  EDICION[EDICIÓN]:::ent
  ALUMNO[ALUMNO]:::ent
  PROFESOR[PROFESOR]:::ent
  PROYECTO[PROYECTO]:::ent

  rAcoge{acoge}:::rel
  rTiene{tiene}:::rel
  rAgrupa{agrupa}:::rel
  rOfrece{"ofrece<br/>(opcional)"}:::rel
  rUsa{"usa<br/>(opcional)"}:::rel
  rContiene{contiene}:::rel
  rMatricula{matricula}:::rel
  rDefine{define}:::rel
  rClasifica{clasifica}:::rel
  rObtiene{obtiene}:::rel
  rImparte{imparte}:::rel

  CAMPUS ---|1| rAcoge ---|N| EDICION
  VERTICAL ---|1| rTiene ---|N| EDICION
  PROMOCION ---|1| rAgrupa ---|N| EDICION
  MODALIDAD ---|1| rOfrece ---|N| EDICION
  AULA ---|1| rUsa ---|N| EDICION
  CAMPUS ---|1| rContiene ---|N| AULA
  EDICION ---|1| rMatricula ---|N| ALUMNO
  VERTICAL ---|1| rDefine ---|N| PROYECTO
  ROL ---|1| rClasifica ---|N| PROFESOR
  ALUMNO ---|N| rObtiene ---|M| PROYECTO
  PROFESOR ---|N| rImparte ---|M| EDICION
  MODALIDAD ---|1| rImparte

  aCampus(["<u>nombre</u>"]):::att --- CAMPUS
  aVerCod(["<u>código</u>"]):::att --- VERTICAL
  aVerNom(["nombre"]):::att --- VERTICAL
  aProNom(["<u>nombre</u>"]):::att --- PROMOCION
  aProFec(["<u>fecha_inicio</u>"]):::att --- PROMOCION
  aMod(["<u>nombre</u>"]):::att --- MODALIDAD
  aRol(["<u>nombre</u>"]):::att --- ROL
  aAula(["<u>nombre</u>"]):::att --- AULA
  aAluNom(["nombre"]):::att --- ALUMNO
  aAluEma(["<u>email</u>"]):::att --- ALUMNO
  aProf(["<u>nombre</u>"]):::att --- PROFESOR
  aProy(["<u>nombre</u>"]):::att --- PROYECTO
  aApto(["apto"]):::att --- rObtiene
```

## Cómo se lee
- **Subrayado** = atributo que identifica la entidad. `PROMOCIÓN` se identifica por nombre y fecha de inicio juntos.
- **Edición** es el centro: una vertical, en una promoción, en un campus. No tiene atributos propios y existe aunque no tenga alumnos o profesores.
- **obtiene** es una relación de muchos a muchos entre alumno y proyecto, y lleva el atributo `apto`.
- **imparte** une tres entidades: un profesor da docencia en una edición con una modalidad.
- Los rombos marcados *(opcional)* admiten que la edición no tenga modalidad o aula.

Estado: propuesta para revisar entre todos. Quien cambie el modelo actualiza este fichero y la imagen en el mismo commit.
