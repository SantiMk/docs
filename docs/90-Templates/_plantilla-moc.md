---
aliases: []
tags: [moc]
diataxis_type: moc
domain:
status: active
owner: "[[ ]]"
related_code: []
created_date: {{date:YYYY-MM-DD}}
updated_date: {{date:YYYY-MM-DD}}
---

# MOC — {{title}}

Puerto de entrada al dominio. Centraliza enlaces a decisiones, specs, guías y referencia.

## Todo lo del dominio (automático)
```dataview
TABLE WITHOUT ID file.link AS "Documento", diataxis_type AS "Tipo", status AS "Estado", updated_date AS "Actualizado"
FROM "docs"
WHERE domain = this.domain AND file.name != this.file.name
SORT diataxis_type ASC, updated_date DESC
```

## Enlaces destacados (manuales)
- …
