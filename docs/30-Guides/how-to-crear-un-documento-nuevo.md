---
aliases: [Crear documento, Nuevo doc]
tags: [how-to, documentacion]
diataxis_type: how_to
domain:
status: active
owner: "[[ ]]"
related_code: []
created_date: 2026-05-31
updated_date: 2026-05-31
---

# Cómo crear un documento nuevo

Pasos para añadir un documento bien clasificado y enlazado.

1. **Elige el tipo** con el árbol de decisión de [[explanation-que-es-diataxis]] o de `AGENTS.md`.
2. **Crea el archivo** en la carpeta correspondiente, con nombre en `kebab-case`:
   - Tutorial/How-To → `docs/30-Guides/` (p. ej. `how-to-rotar-claves-jwt.md`)
   - Referencia → `docs/40-Reference/`
   - Explicación → `docs/50-Explanations/`
   - ADR → `docs/10-Architecture/ADR-NNNN-titulo.md`
   - Spec → `docs/20-Specifications/SPEC-NNNN-titulo.md`
   - MOC → `docs/00-MOCs/`
3. **Inserta la plantilla**: paleta de comandos → *Templates: Insert template* → elige la plantilla de `docs/90-Templates/` que corresponda. (Atajo por defecto: `Ctrl/Cmd+Shift+I`.)
4. **Rellena el frontmatter** según [[reference-esquema-de-metadatos]] (`diataxis_type`, `domain`, `status`, `owner`).
5. **Enlaza al código** si aplica: `[[archivo.py]]|simbolo`, `@` o anclas de bloque `^`. Rellena `related_code`.
6. **Conéctalo al MOC** de su dominio en `docs/00-MOCs/` (o confía en la consulta Dataview si el frontmatter está correcto).
7. **Abre el PR** junto con el cambio de código asociado (regla de oro).
