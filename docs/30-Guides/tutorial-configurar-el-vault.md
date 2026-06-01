---
aliases: [Configurar Obsidian, Setup del vault]
tags: [tutorial, onboarding, obsidian]
diataxis_type: tutorial
domain: infrastructure
status: active
owner: "[[ ]]"
related_code: [".obsidian/community-plugins.json"]
created_date: 2026-05-31
updated_date: 2026-05-31
---

# Tutorial: configurar el Vault de Obsidian para este repositorio

Al terminar, tendrás Obsidian abierto sobre este repo, con todos los plugins funcionando y la documentación enlazada al código. Sigue los pasos en orden.

## 1. Instala Obsidian
Descarga Obsidian desde https://obsidian.md e instálalo.

## 2. Abre el repositorio como Vault
En Obsidian: *Open folder as vault* → selecciona la **carpeta raíz de este repositorio** (la que contiene `docs/` y `.obsidian/`). Confía en el Vault si te lo pregunta.

## 3. Activa "Detectar todas las extensiones de archivo"
Ve a *Settings → Files and Links* y activa **Detect all file extensions** (ya viene preconfigurado, pero verifícalo). Esto permite enlazar a `.py`, `.ts`, `.go`, etc.

## 4. Instala los plugins obligatorios
*Settings → Community plugins → Browse* e instala (luego *Enable*):
- **Dataview**
- **Obsidian Git**
- **Code Link**
- **@ Symbol Linking** (busca "@ symbol linking")

Si un plugin no aparece en la lista de instalados tras habilitarlo, cierra y reabre Obsidian.

## 5. Verifica el plugin de plantillas
*Settings → Core plugins* → asegúrate de que **Templates** está activo y de que su carpeta apunta a `docs/90-Templates`.

## 6. Comprueba que todo funciona
1. Abre `docs/50-Explanations/explanation-que-es-diataxis.md`: el diagrama Mermaid debe renderizar.
2. Abre `docs/00-MOCs/MOC - Inicio.md` en **vista de lectura**: las tablas de Dataview deben mostrar datos.
3. Abre `docs/20-Specifications/SPEC-0001-notificaciones-por-email.md` en vista de lectura: el enlace `[[email_service.py]]|send_email` mostrará el fragmento de código (cuando exista `src/notifications/email_service.py`).

## ¡Listo!
Ya puedes crear documentación. Continúa con [[how-to-crear-un-documento-nuevo]].
