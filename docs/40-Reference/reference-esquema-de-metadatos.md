---
aliases: [Esquema YAML, Frontmatter, Propiedades]
tags: [referencia, metadatos, frontmatter]
diataxis_type: reference
domain:
status: active
owner: "[[ ]]"
related_code: [".obsidian/types.json"]
created_date: 2026-05-31
updated_date: 2026-05-31
---

# Referencia: esquema de metadatos (frontmatter YAML)

Toda nota empieza con un bloque de propiedades en `lower_snake_case`. Este esquema permite que los MOCs, dashboards y la matriz de trazabilidad funcionen.

## Propiedades

| Clave | Tipo | Obligatoria | Propósito y reglas |
|---|---|---|---|
| `aliases` | lista | no | Nombres/acrónimos alternativos para enlazar la nota desde otros nombres. |
| `tags` | lista | no | Taxonomías menores: `[python, refactor, tech-debt]`. |
| `diataxis_type` | enum | **sí** | `tutorial` · `how_to` · `reference` · `explanation` · `adr` · `spec` · `moc`. |
| `domain` | enum | **sí** | `backend` · `frontend` · `infrastructure` · `security` · `database` · `ui_ux`. |
| `status` | enum | **sí** | `draft` · `in_review` · `active` · `deprecated` · `superseded`. |
| `owner` | enlace | **sí** | Responsable del mantenimiento: `[[Nombre]]`. |
| `related_code` | lista | no | Rutas/símbolos vinculados: `["src/auth/service.py"]`. |
| `created_date` | fecha | **sí** | `YYYY-MM-DD`. Inmutable (génesis del documento). |
| `updated_date` | fecha | **sí** | `YYYY-MM-DD`. Última revisión sustancial. |

## Bloque para copiar y pegar

```yaml
---
aliases: []
tags: []
diataxis_type:
domain:
status: draft
owner: "[[ ]]"
related_code: []
created_date: 2026-01-01
updated_date: 2026-01-01
---
```

## Valores enumerados (referencia rápida)

- **diataxis_type:** `tutorial`, `how_to`, `reference`, `explanation`, `adr`, `spec`, `moc`
- **domain:** `backend`, `frontend`, `infrastructure`, `security`, `database`, `ui_ux`
- **status:** `draft`, `in_review`, `active`, `deprecated`, `superseded`

## Notas de implementación

- Las claves nunca llevan espacios ni mayúsculas (`lower_snake_case`) para no romper scripts de CI ni consultas.
- Los tipos de cada propiedad se versionan en `.obsidian/types.json` para que se rendericen igual en todo el equipo.
