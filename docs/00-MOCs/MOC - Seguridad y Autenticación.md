---
aliases: [MOC Seguridad, Auth MOC]
tags: [moc, security]
diataxis_type: moc
domain: security
status: active
owner: "[[ ]]"
related_code: []
created_date: 2026-05-31
updated_date: 2026-05-31
---

# 🔐 MOC — Seguridad y Autenticación

Puerto de entrada al dominio de seguridad. Centraliza decisiones, especificaciones, guías y referencia.

## Todo lo del dominio (automático)
```dataview
TABLE WITHOUT ID file.link AS "Documento", diataxis_type AS "Tipo", status AS "Estado", updated_date AS "Actualizado"
FROM "docs"
WHERE domain = "security" AND file.name != this.file.name
SORT diataxis_type ASC, updated_date DESC
```

## Enlaces destacados (manuales)
- Decisiones: ver ADRs con `domain: security` arriba.
- Specs en curso: ver tabla.
- Guía de onboarding de seguridad: *(añadir cuando exista)*.
