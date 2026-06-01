# AGENTS.md — Cómo usar y mantener esta base de conocimiento

> Si eres un agente de IA (Claude, Copilot, Cursor, etc.) o un LLM trabajando en este repositorio, **lee este archivo antes de crear, editar o enlazar documentación**. Define la taxonomía, el esquema de metadatos, el enlazado a código y las reglas de Pull Request.

## 1. Qué es este repositorio

La documentación vive **junto al código**, en el mismo repo Git, y se trata **como código**: texto plano (Markdown), versionada, revisada en PRs. El directorio `docs/` es un **Vault de Obsidian**. El Vault se abre en la **raíz del repositorio** para que Obsidian indexe tanto `docs/` como el código fuente (`src/`, etc.) y se puedan enlazar entre sí.

## 2. Regla de oro (innegociable)

**Todo cambio de lógica en el código se acompaña, en el mismo PR, de la actualización de la documentación correspondiente** (ADR, Spec, guía o referencia). Si un comentario o corrección aparece repetidamente en las revisiones, ese criterio debe documentarse, enseñarse o automatizarse.

## 3. Diátaxis: árbol de decisión para clasificar un documento

Antes de escribir, decide el tipo. Pregúntate **¿el lector quiere APRENDER o TRABAJAR/CONSULTAR?**

- **APRENDER**
  - ¿Paso a paso desde cero, para alguien que aún no sabe nada y necesita una primera victoria? → **Tutorial** · carpeta `docs/30-Guides/` · `diataxis_type: tutorial`
  - ¿Explica el porqué, el contexto, las alternativas, las decisiones? → **Explicación** · `docs/50-Explanations/` · `diataxis_type: explanation`
- **TRABAJAR / CONSULTAR**
  - ¿Pasos para una tarea concreta que el lector ya sabe que necesita hacer? → **How-To** · `docs/30-Guides/` · `diataxis_type: how_to`
  - ¿Datos precisos para consultar (API, esquema, parámetros, eventos)? → **Referencia** · `docs/40-Reference/` · `diataxis_type: reference`
- **CASOS ESPECIALES**
  - ¿Una decisión arquitectónica con consecuencias y alternativas? → **ADR** (formato MADR) · `docs/10-Architecture/` · `diataxis_type: adr`
  - ¿Qué se va a construir y por qué, *antes* de codear? → **Spec** · `docs/20-Specifications/` · `diataxis_type: spec`
  - ¿Un índice/panel de un dominio? → **MOC** · `docs/00-MOCs/` · `diataxis_type: moc`

**Regla que nunca se rompe:** no mezcles tipos en un mismo documento. Una guía de despliegue de emergencia (How-To) no se interrumpe con la filosofía de los contenedores (Explicación). Si necesitas ambos, crea dos documentos y enlázalos.

## 4. Mapa de carpetas

| Carpeta | Contenido |
|---|---|
| `docs/00-MOCs/` | Mapas de contenido (índices dinámicos por dominio, con Dataview) |
| `docs/10-Architecture/` | ADRs, decisiones de diseño, diagramas de topología |
| `docs/20-Specifications/` | Tech Specs, RFCs, requisitos en curso |
| `docs/30-Guides/` | Tutoriales y How-To, onboarding, runbooks |
| `docs/40-Reference/` | Contratos de API, esquemas de BD, diccionarios |
| `docs/50-Explanations/` | Análisis, post-mortems, discusiones de diseño |
| `docs/90-Templates/` | Plantillas maestras |
| `docs/99-Assets/` | Imágenes y diagramas exportados |

## 5. Frontmatter obligatorio (esquema YAML)

**Toda** nota nueva empieza con este bloque. Propiedades en `lower_snake_case`. Detalle completo en [[reference-esquema-de-metadatos]].

```yaml
---
aliases: []                 # nombres/acrónimos alternativos (lista)
tags: []                    # taxonomías menores: [python, refactor, tech-debt]
diataxis_type:              # tutorial | how_to | reference | explanation | adr | spec | moc
domain:                     # backend | frontend | infrastructure | security | database | ui_ux
status: draft               # draft | in_review | active | deprecated | superseded
owner: "[[ ]]"              # enlace interno al responsable: [[Nombre]]
related_code: []            # rutas/símbolos vinculados: ["src/auth/service.py"]
created_date: 2026-01-01    # YYYY-MM-DD (inmutable)
updated_date: 2026-01-01    # YYYY-MM-DD (última revisión sustancial)
---
```

## 6. Cómo crear un documento nuevo

1. Decide el **tipo** (sección 3) y por tanto la **carpeta** y el `diataxis_type`.
2. Crea el archivo en esa carpeta con un nombre descriptivo en `kebab-case` (p. ej. `how-to-rotar-claves-jwt.md`). Para ADRs usa `ADR-NNNN-titulo.md`; para Specs `SPEC-NNNN-titulo.md`.
3. Inserta la plantilla correspondiente de `docs/90-Templates/` (en Obsidian: *Insert template*) y rellena el frontmatter.
4. **Enlázalo a su MOC** de dominio en `docs/00-MOCs/` (o confía en la consulta Dataview del MOC si el frontmatter está bien puesto).
5. Si describe o afecta código, **enlaza al código** (sección 7) y rellena `related_code`.

## 7. Enlazar a código (no pegues bloques de código)

Pegar bloques de código en la doc garantiza que se desincronicen. En su lugar:

- **Code Link** (símbolos): enlaza a un símbolo del código fuente con la sintaxis de barra vertical:
  `[[email_service.py]]|send_email`
  En *vista de lectura*, Obsidian renderiza el fragmento exacto (clase/función) con resaltado, sin duplicar bytes. Requiere `showUnsupportedFiles: true` (ya configurado).
- **@ Symbol Linking** (referencia rápida): al escribir `@` aparece un buscador acotado a directorios/alias para enlazar sin fricción.
- **Enlaces a bloque/línea** (`^`): para una línea concreta que no es un símbolo (p. ej. una línea de un manifiesto de Kubernetes), usa anclas de bloque `^id` y enlázalas.

No crees archivos genéricos sin dueño (`utils.js`, `helpers.py`): rompen el enlazado por bloques y diluyen la responsabilidad del dominio.

## 8. Diagramas como código (Mermaid)

Todo diagrama se escribe en **Mermaid** dentro del Markdown (se renderiza nativo en Obsidian y en GitHub/GitLab). Así, el diff del PR muestra exactamente qué cambió.
- Flujos y procesos con estado (auth, microservicios, ciclos de vida) → `sequenceDiagram`.
- Esquemas de BD y topologías → `erDiagram` (y `architecture-beta` si aplica).
Nunca incrustes imágenes exportadas de Draw.io/Visio para diagramas que cambian con el código.

## 9. Convenciones de nombres y estilo

- Propiedades del frontmatter: `lower_snake_case`. Valores enumerados: en inglés (ver esquema).
- Prosa de la documentación: en **español**.
- Títulos de ADR: frase sustantivada y **enumerada** secuencialmente (`ADR-0042: Adoptar arquitectura orientada a eventos con Kafka`).
- Code-smells / deuda: etiqueta `#tech-debt` para que aparezcan en los dashboards.

## 10. Ciclo de vida (`status`)

`draft` → `in_review` → `active` → (`deprecated` | `superseded`).
**Los ADRs nunca se borran.** Si una decisión se revierte, marca el ADR original como `status: superseded` y enlaza al ADR que lo reemplaza. Se preserva la memoria institucional.

## 11. Checklist antes de abrir un PR

- [ ] ¿El documento tiene un único `diataxis_type` y está en la carpeta correcta?
- [ ] ¿El frontmatter está completo y en `lower_snake_case`?
- [ ] ¿`owner`, `domain` y `status` están puestos?
- [ ] ¿Enlacé al código con Code Link / `@` / bloques en vez de pegar código?
- [ ] ¿Los diagramas están en Mermaid (no imágenes)?
- [ ] ¿El cambio de código y su documentación van en el **mismo** PR?
- [ ] ¿`updated_date` actualizado si fue una revisión sustancial?

## 12. Referencia rápida

| Quiero… | Tipo | Carpeta | `diataxis_type` |
|---|---|---|---|
| Enseñar desde cero | Tutorial | `docs/30-Guides/` | `tutorial` |
| Resolver una tarea | How-To | `docs/30-Guides/` | `how_to` |
| Documentar una API/esquema | Referencia | `docs/40-Reference/` | `reference` |
| Explicar el porqué | Explicación | `docs/50-Explanations/` | `explanation` |
| Registrar una decisión | ADR (MADR) | `docs/10-Architecture/` | `adr` |
| Planear antes de codear | Spec | `docs/20-Specifications/` | `spec` |
| Indexar un dominio | MOC | `docs/00-MOCs/` | `moc` |

Más detalle conceptual: [[explanation-que-es-diataxis]] · sitio oficial: https://diataxis.fr
