# 01 - Análisis de datos

## 1. Comprensión del conjunto de datos

El archivo `reporte_quito.xlsx` contiene las siguientes hojas:

| Hoja | Filas | Columnas | Granularidad aproximada |
|---|---:|---:|---|
| `authors_publications` | 8,970 | 20 | Revisar según claves de la hoja |
| `projects_publications` | 735 | 8 | Revisar según claves de la hoja |
| `researchers_projects` | 4,079 | 16 | Revisar según claves de la hoja |
| `projects_metadata` | 223 | 9 | Revisar según claves de la hoja |
| `researchers_groups` | 790 | 14 | Revisar según claves de la hoja |

### Observaciones de granularidad

- `authors_publications`: una fila representa una relación autor-publicación; una publicación puede aparecer varias veces por tener varios autores.
- `projects_publications`: representa relaciones entre publicaciones y proyectos.
- `researchers_projects`: representa relaciones entre investigadores y proyectos; un proyecto puede tener varios investigadores.
- `projects_metadata`: representa proyecto-línea de investigación; un proyecto puede aparecer varias veces si está asociado a varias líneas.
- `researchers_groups`: representa relaciones entre investigadores y grupos.

Por estas diferencias de granularidad, para los KPIs de entidades se recomienda `DISTINCTCOUNT` sobre identificadores, en lugar de contar filas de tablas de relación.

## 2. Problemas de calidad a revisar

1. Valores nulos en diferentes atributos académicos y administrativos.
2. Fechas con formatos/tipos que deben validarse antes del análisis temporal.
3. Registros con año/fecha anómala (por ejemplo, valores de 1900 asociados a una hora sin fecha).
4. Diferencias de granularidad entre hojas que pueden producir sobreconteos.
5. Posibles inconsistencias de integridad referencial entre códigos de proyecto presentes en diferentes hojas.
6. Posibles categorías inconsistentes por mayúsculas, minúsculas o espacios.
7. Información personal identificable, como cédulas, que no debe exponerse en visualizaciones ni repositorios públicos.

## 3. Tratamiento recomendado

- No eliminar NULL automáticamente; evaluar si representan dato faltante o no aplicable.
- Convertir fechas a tipo Fecha en Power Query.
- Validar y excluir/corregir fechas claramente inválidas para visualizaciones temporales, documentando la decisión.
- Normalizar categorías cuando existan variantes equivalentes.
- Construir dimensiones con claves únicas.
- Usar `DISTINCTCOUNT` para entidades cuando las tablas tengan relaciones uno-a-muchos.
- Excluir cédulas de visualizaciones.

## 4. Datos sensibles

Se identifican campos de cédula de investigadores. Estos campos deben utilizarse únicamente cuando sean necesarios como claves técnicas internas y no deben aparecer en el dashboard. El Excel original no debe publicarse en GitHub.

## 5. Requerimientos funcionales

- Visualizar indicadores de investigación.
- Consultar proyectos y publicaciones.
- Filtrar por estado de proyecto.
- Filtrar por grupo.
- Mostrar tendencias de producción científica.
- Mostrar una tabla de detalle.
- Exportar el estado filtrado a PDF.

## 6. KPIs propuestos

1. Total de proyectos.
2. Total de publicaciones.
3. Total de investigadores asociados a proyectos.
4. Proyectos en ejecución.
5. Grupos de investigación.

## 7. Visualizaciones propuestas

- Proyectos por estado: barras.
- Publicaciones por año: líneas.
- Publicaciones por tipo: barras.
- Tabla de proyectos filtrable.
