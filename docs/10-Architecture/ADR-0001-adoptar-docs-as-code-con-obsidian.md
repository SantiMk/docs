---
aliases: [ADR-0001]
tags: [adr, documentacion, tooling]
diataxis_type: adr
domain: infrastructure
status: accepted
owner: "[[ ]]"
related_code: [".obsidian/community-plugins.json", ".gitignore"]
created_date: 2026-05-31
updated_date: 2026-05-31
---

# ADR-0001: Adoptar Docs-as-Code con Obsidian y Diátaxis

## Estado
Aceptado.

## Contexto
La documentación alojada en wikis externas (Confluence, Notion) se desincroniza del código: el software evoluciona con cada despliegue, pero las páginas externas quedan estáticas y se vuelven artefactos engañosos. Necesitamos que la documentación se mantenga sincronizada con el código, sea revisable y siga siendo legible y recuperable a largo plazo, independiente de cualquier proveedor SaaS.

Además, la documentación tiende a desordenarse cuando mezcla tipos de contenido (pasos urgentes enterrados bajo teoría histórica), lo que dificulta encontrar información durante incidentes y eleva la fricción del onboarding.

## Decisión
Adoptamos **Docs-as-Code**: la documentación se escribe en Markdown dentro del mismo repositorio (`docs/`), se versiona con Git, se revisa en los mismos Pull Requests y se navega con **Obsidian** abierto en la **raíz del repositorio** (para que Obsidian Code Link indexe y enlace el código fuente). El contenido se organiza con el framework **Diátaxis** y se gobierna con un esquema de frontmatter obligatorio.

## Consecuencias

**Positivas**
- La documentación y el código se validan mutuamente en cada PR.
- Acceso offline, búsqueda local rápida y durabilidad (texto plano).
- Diátaxis reduce la fricción de búsqueda y de onboarding.
- MOCs y dashboards con Dataview dan visibilidad del progreso sin herramientas externas.

**Negativas / costos**
- Cada persona debe instalar y configurar Obsidian y un conjunto de plugins (mitigado con un tutorial y configuración versionada).
- Dependencia de plugins comunitarios (Dataview, Code Link, @ Symbol Linking); se monitorea su mantenimiento y se valora migrar consultas simples a **Bases** (nativo) con el tiempo.
- Disciplina requerida: el frontmatter y la clasificación deben mantenerse correctos.

## Opciones consideradas

- **Wiki externa (Confluence/Notion):** descartada por desincronización con el código y dependencia de proveedor.
- **Markdown en `/docs` sin Obsidian:** válido, pero pierde enlazado bidireccional, MOCs dinámicos, enlace a símbolos de código y dashboards.
- **Vault = `/docs` (en vez de la raíz):** descartado como predeterminado porque Code Link no puede enlazar al código fuente fuera del Vault. Alternativa disponible: importar el código como symlinks con *Code Link: Import project*.

> Si en el futuro se revierte esta decisión, **no se borra este ADR**: se marca `status: superseded` y se enlaza al ADR que lo reemplaza.
