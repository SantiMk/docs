# Cómo contribuir a la documentación

La documentación es **código**. Sigue el mismo rigor que el software.

## Flujo Docs-as-Code

1. Crea una rama desde `main`.
2. Escribe/edita Markdown en `docs/` (usa las plantillas de `docs/90-Templates/`).
3. Si cambias lógica del código, **incluye la documentación en el mismo PR**.
4. Abre un Pull Request. La doc se revisa igual que el código.

## Reglas de revisión (bloqueantes)

- Un documento = un único `diataxis_type`, en la carpeta correcta (ver `AGENTS.md`).
- Frontmatter completo, en `lower_snake_case`, con `owner`, `domain` y `status`.
- Enlaces a código con **Code Link / `@` / bloques `^`**, nunca bloques de código pegados.
- Diagramas en **Mermaid**, no imágenes exportadas.
- ADRs: nunca se borran; si se revierten, `status: superseded` + enlace al reemplazo.
- Deuda técnica: etiqueta `#tech-debt`.

## Estilo

- Prosa en español; claves/rutas/valores enumerados en inglés `lower_snake_case`.
- Documentos cortos, analíticos y focalizados. Evita archivos genéricos sin dueño (`utils.md`, `helpers.md`).

## Commits

Mensajes claros e imperativos. Si el PR cambia código + doc, descríbelo en conjunto, p. ej.:
`feat(notificaciones): envío por email + SPEC-0001 y ADR-0003`.
