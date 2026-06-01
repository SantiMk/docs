# Base de documentación — Docs-as-Code · Diátaxis · Obsidian

Plantilla reutilizable para documentar proyectos de software con documentación que **vive junto al código**, se versiona con Git y se navega/edita con **Obsidian**. La organización del contenido sigue el framework **[Diátaxis](https://diataxis.fr)**.

## Por qué

El código es un pasivo, no un activo. La documentación es un mecanismo de diseño que reduce fricción y evita repetir errores arquitectónicos. Por eso vive en el mismo repo, se revisa en los mismos PRs y usa los mismos flujos que el código.

## Estructura

```
docs/
  00-MOCs/          Índices dinámicos por dominio (Dataview)
  10-Architecture/  ADRs y decisiones de diseño
  20-Specifications/ Tech Specs y RFCs
  30-Guides/        Tutoriales y How-To (Diátaxis: práctica)
  40-Reference/     APIs, esquemas, diccionarios (Diátaxis: teoría/trabajo)
  50-Explanations/  Análisis y porqués (Diátaxis: teoría/estudio)
  90-Templates/     Plantillas maestras
  99-Assets/        Imágenes y diagramas
```

## Diátaxis en 20 segundos

| | Aprender | Trabajar |
|---|---|---|
| **Práctica** | Tutorial | How-To |
| **Teoría** | Explicación | Referencia |

Detalle: [`docs/50-Explanations/explanation-que-es-diataxis.md`](docs/50-Explanations/explanation-que-es-diataxis.md).

## Empezar

### Opción A — Iniciar un proyecto nuevo con esta base
1. Clona o descarga este repositorio (o úsalo como *template* de GitHub).
2. Abre **la carpeta raíz** del repo como Vault en Obsidian.
3. Sigue el tutorial: [`docs/30-Guides/tutorial-configurar-el-vault.md`](docs/30-Guides/tutorial-configurar-el-vault.md) (instala los plugins y verifica la configuración).

### Opción B — Añadir documentación a un proyecto existente
Copia al proyecto: la carpeta `docs/`, la carpeta `.obsidian/`, `.gitignore` (fusiona reglas), `AGENTS.md`, `CLAUDE.md` y `CONTRIBUTING.md`. Abre la raíz del proyecto como Vault.

## Plugins necesarios

| Plugin | ID | Para qué |
|---|---|---|
| Dataview | `dataview` | MOCs, dashboards, barras de progreso, matriz de trazabilidad |
| Obsidian Git | `obsidian-git` | Commit/push/pull desde Obsidian |
| Code Link | `code-link` | Enlazar a símbolos del código fuente (TreeSitter) |
| @ Symbol Linking | `at-symbol-linking` | Referencia rápida con `@` |
| Bases (núcleo) | — | Tableros/tablas nativas (complemento) |

## Para agentes / LLMs

Lee **[`AGENTS.md`](./AGENTS.md)**: es la fuente de verdad sobre cómo usar y mantener el sistema.

## Licencia

MIT — ver [`LICENSE`](./LICENSE).
