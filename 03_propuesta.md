# 03 - Propuesta técnica

## Evolución a producción

El prototipo puede evolucionar desde Excel hacia una arquitectura institucional:

Fuente institucional (PostgreSQL / API REST)
→ ETL / Power Query
→ Modelo semántico Power BI
→ Dashboard
→ Power BI Service

## Actualización

Se recomienda programar actualizaciones periódicas mediante Power BI Service una vez que la fuente se encuentre centralizada.

## Seguridad

- No exponer cédulas ni otros datos personales en visualizaciones.
- Aplicar control de acceso por roles.
- Mantener el archivo fuente fuera del repositorio público.
- Evaluar Row-Level Security cuando diferentes usuarios requieran diferentes niveles de acceso.

## Mantenimiento

- Documentar las claves y relaciones.
- Validar cambios de esquema de las fuentes.
- Mantener medidas DAX documentadas.
- Incorporar controles de calidad de datos.
- Registrar cambios mediante Git.

## Riesgos

- Cambios en nombres o tipos de columnas.
- Datos incompletos.
- Cambios en relaciones.
- Duplicados que provoquen sobreconteos.
- Exposición accidental de información personal.
