---
name: google-drive
description: Acceso y trabajo con archivos de Google Drive para rutas sincronizadas en Windows, carpetas montadas, Shared Drives, Mi unidad y enlaces compartidos. Usar cuando Codex necesite abrir, ubicar, leer, organizar o preparar archivos que viven en Google Drive sin asumir APIs, Python, Git o setup tecnico innecesario.
---

# Google Drive

Resolver acceso y trabajo con archivos de Google Drive de la forma mas simple posible.

## Objetivo

- encontrar la forma mas directa de acceder a los archivos
- preferir rutas locales sincronizadas o montadas cuando existan
- evitar setup tecnico o APIs si no hacen falta
- dejar los archivos listos para que otra skill pueda analizarlos o transformarlos

## Orden de acceso

Usar este orden:

1. ruta local sincronizada o montada en el sistema
2. carpeta compartida visible en el explorador
3. enlace de Drive si el entorno realmente puede abrirlo
4. pedir una alternativa simple si no hay acceso suficiente

## Regla principal

- No asumir API de Google Drive.
- No asumir que la persona tiene Python, Node, Git o credenciales de Google Cloud.
- No pedir `git clone`, SDKs ni OAuth salvo que la persona quiera una integracion tecnica de verdad.
- Si el usuario solo necesita leer una carpeta de Drive conectada a Windows, pedir la ruta local exacta y trabajar desde ahi.

## Casos

- Drive para escritorio sincronizado
- unidad montada en Windows
- `Mi unidad`
- Shared Drives
- enlaces compartidos
- preparar archivos para analisis, informes o dashboards

## Estilo

- hablar simple
- pedir una sola cosa a la vez
- si hace falta una ruta, pedirla en una sola frase corta
- no listar tecnicismos de autenticacion salvo que de verdad hagan falta

## Handoffs

- usar `data-analysis` si ya hay archivos y toca analizarlos
- usar `report-generation` si hay que convertir archivos en informe
- usar `software-engineering` solo si la persona realmente pide una integracion o automatizacion tecnica

## Evitar

- convertir acceso a Drive en proyecto de desarrollo
- pedir instalar librerias como primer paso
- asumir que un enlace web se puede abrir en cualquier entorno
- copiar archivos a carpetas raras por defecto

## Referencias

- Ver [references/access-modes.md](references/access-modes.md)
