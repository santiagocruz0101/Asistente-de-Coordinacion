# 02 - Diseño

## Herramienta

Microsoft Power BI Desktop.

## Arquitectura

Excel
→ Power Query
→ Limpieza y transformación
→ Modelo dimensional
→ Medidas DAX
→ Dashboard
→ Exportación PDF

## Modelo

Se recomienda separar dimensiones y tablas de relación:

- DimProyecto
- DimPublicacion
- DimInvestigador
- DimGrupo
- FactProyectosPublicaciones
- FactInvestigadoresProyectos
- FactPublicacionesAutores
- ProyectoLineas
- FactInvestigadoresGrupos

## Relaciones principales

- `DimProyecto[Codigo del proyecto]` 1:* `FactInvestigadoresProyectos[Codigo del proyecto]`
- `DimProyecto[Codigo del proyecto]` 1:* `FactProyectosPublicaciones[Codigo del proyecto]`
- `DimPublicacion[Codigo]` 1:* `FactPublicacionesAutores[Codigo]`
- `DimPublicacion[Codigo]` 1:* `FactProyectosPublicaciones[Codigo]`
- `DimInvestigador[Cédula del investigador]` 1:* `FactInvestigadoresProyectos[Cédula del investigador]`
- `DimInvestigador[Cédula del investigador]` 1:* `FactInvestigadoresGrupos[Cédula del investigador]`
- `DimGrupo[Codigo del grupo]` 1:* `FactInvestigadoresGrupos[Codigo del grupo]`
- `DimGrupo[Codigo del grupo]` 1:* `FactInvestigadoresProyectos[Codigo del grupo]`

Dirección de filtro recomendada: unidireccional, de dimensión hacia hecho.

## Medidas DAX

```DAX
Total Proyectos =
DISTINCTCOUNT(DimProyecto[Codigo del proyecto])

Total Publicaciones =
DISTINCTCOUNT(DimPublicacion[Codigo])

Total Investigadores =
DISTINCTCOUNT(FactInvestigadoresProyectos[Cédula del investigador])

Total Grupos =
DISTINCTCOUNT(DimGrupo[Codigo del grupo])

Proyectos En Ejecución =
CALCULATE(
    [Total Proyectos],
    DimProyecto[Estado del proyecto] = "En ejecución"
)

Publicaciones Vinculadas =
DISTINCTCOUNT(FactProyectosPublicaciones[Codigo])
```

## Dashboard

Fila superior:
- Total Proyectos
- Total Publicaciones
- Total Investigadores
- Proyectos En Ejecución

Zona central:
- Proyectos por estado
- Publicaciones por año

Zona inferior:
- Publicaciones por tipo
- Tabla de detalle de proyectos

Filtros:
- Estado del proyecto
- Grupo administrador del proyecto

La tabla debe mostrar:
- Código del proyecto
- Proyecto
- Grupo
- Año de inicio
- Estado
- Publicaciones vinculadas

No mostrar cédulas.

## Exportación

Antes de exportar a PDF, aplicar filtros y verificar que:
- KPIs cambien.
- Gráficos cambien.
- Tabla cambie.
- El PDF represente el estado filtrado actual.
