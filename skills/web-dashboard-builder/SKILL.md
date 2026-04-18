---
name: web-dashboard-builder
description: Construccion de dashboards web interactivos para metricas, filtros, tablas, graficos y vistas operativas o ejecutivas. Usar cuando Codex necesite diseñar o implementar paneles web claros, accionables y faciles de usar.
---

# Web Dashboard Builder

Construir dashboards web que ayuden a entender y actuar.

## Objetivo

- mostrar pocas metricas importantes primero
- dejar filtros utiles
- priorizar claridad y accion
- evitar dashboards recargados
- no asumir React, npm o un framework especifico si no esta claro
- si el usuario no es tecnico, priorizar opciones faciles de usar antes que stacks de desarrollo

## Flujo

1. definir audiencia y decisiones
2. elegir metricas
3. definir componentes y filtros
4. construir la vista
5. validar claridad

Si falta contexto minimo, preguntar una sola cosa simple antes de elegir tecnologia.

Ejemplos:

- "Lo quieres como pagina web simple o integrado en un sistema que ya existe?"
- "Quieres algo para usar directo o una base tecnica para que alguien la siga?"

## Evitar

- responder con React, Vite o `npm run dev` como primera salida para una persona no tecnica
- asumir que la persona puede instalar dependencias o correr terminal
- entregar una solucion tecnica sin explicar primero la opcion mas simple

## Dependencias sugeridas

- usar `data-analysis` para validar metricas
- usar `report-generation` si tambien se necesita narrativa

## Referencias

- Ver [references/dashboard-principles.md](references/dashboard-principles.md)
