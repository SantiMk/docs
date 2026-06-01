---
aliases: [Inicio, Home, Panel]
tags: [moc, dashboard]
diataxis_type: moc
domain:
status: active
owner: "[[ ]]"
related_code: []
created_date: 2026-05-31
updated_date: 2026-05-31
---

# 🏠 MOC de Inicio

Panel global de la base de conocimiento. Ábrelo en **vista de lectura** para que Dataview renderice.

## Documentos por tipo
```dataview
TABLE WITHOUT ID file.link AS "Documento", diataxis_type AS "Tipo", domain AS "Dominio", status AS "Estado", updated_date AS "Actualizado"
FROM "docs"
WHERE diataxis_type
SORT updated_date DESC
```

## En revisión (cola)
```dataview
TABLE WITHOUT ID file.link AS "Documento", diataxis_type AS "Tipo", owner AS "Responsable"
FROM "docs"
WHERE status = "in_review"
SORT updated_date ASC
```

## Deuda técnica
```dataview
TABLE WITHOUT ID file.link AS "Nota", domain AS "Dominio", status AS "Estado"
FROM #tech-debt
SORT file.mtime DESC
```

## Progreso de las Specs
```dataviewjs
const specs = dv.pages('"docs/20-Specifications"').where(p => p.diataxis_type === "spec");
if (!specs.length) { dv.paragraph("No hay specs todavía."); }
for (const page of specs) {
  const tasks = page.file.tasks;
  const total = tasks.length;
  const done = tasks.where(t => t.completed).length;
  const pct = total ? Math.round((100 * done) / total) : 0;
  dv.el(
    "div",
    `<strong>${page.file.link}</strong> — ${pct}% (${done}/${total})
     <progress value="${done}" max="${total || 1}" style="width:100%"></progress>`
  );
}
```

## Mapas de contenido por dominio
```dataview
LIST
FROM "docs/00-MOCs"
WHERE diataxis_type = "moc" AND file.name != this.file.name
SORT file.name ASC
```
