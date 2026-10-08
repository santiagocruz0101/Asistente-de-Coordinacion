# Dashboard de Investigación - Quito

Prueba técnica desarrollada con Microsoft Power BI.

## Objetivo

Construir un dashboard para analizar proyectos, investigadores, grupos y producción científica.

## Herramienta

Microsoft Power BI Desktop.

## Estructura

```text
prueba-dashboard-investigacion/
├── README.md
├── .gitignore
├── docs/
│   ├── 01_analisis.md
│   ├── 02_diseno.md
│   ├── 03_propuesta.md
│   └── 04_uso_ia.md
└── powerbi/
    └── dashboard_investigacion.pbix
```

El archivo PBIX debe generarse con Power BI Desktop a partir de `reporte_quito.xlsx`.

## Seguridad

El archivo Excel fuente contiene información que puede incluir datos personales. No debe subirse al repositorio.

## KPIs

- Total de proyectos
- Total de publicaciones
- Total de investigadores
- Proyectos en ejecución
- Total de grupos

## Modelo

Se utiliza un enfoque dimensional con dimensiones de proyecto, publicación, investigador y grupo y tablas de relación.

## Validación

Antes de entregar:
- comprobar relaciones 1:*;
- verificar filtros;
- validar KPIs;
- comprobar que no se muestren cédulas;
- exportar el estado filtrado a PDF.
