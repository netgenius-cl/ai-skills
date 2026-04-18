---
name: automation-builder
description: Automatizacion de procesos, workflows e integraciones entre herramientas. Usar cuando Codex necesite disenar, explicar, estructurar o implementar automatizaciones con n8n, Make, Zapier, Power Automate o codigo; elegir tecnologia para un flujo; ordenar triggers, webhooks y datos; o adaptar una automatizacion a una plataforma concreta.
---

# Automation Builder

Resolver automatizaciones de forma clara, modular y lista para bajar a tecnologia.

## Objetivo

- elegir o usar la tecnologia correcta
- convertir una necesidad en flujo claro
- separar diseno, integraciones y riesgos
- dejar salida lista para construir o explicar

## Regla de entrada

Si falta la tecnologia, hacer una sola pregunta corta:

- "Que tecnologia quieres usar para esto: n8n, Make, Zapier, Power Automate o codigo?"

Si la tecnologia ya esta clara, no volver a preguntar.

## Limite con el orquestador

- el orquestador debe preguntar integraciones especificas cuando sean necesarias
- esta skill debe asumir que idealmente ya llegan aclaradas
- si faltan y bloquean el diseno, pedir una sola aclaracion simple

Ejemplo de integraciones que deberian venir claras:

- origen y destino
- app o servicio inicial
- app o servicio final
- evento disparador

## Flujo base

1. confirmar tecnologia si falta
2. identificar trigger, pasos, condicion y salida
3. adaptar el nivel de detalle a la tecnologia elegida
4. entregar flujo claro, ordenado y accionable
5. si conviene, marcar un riesgo o dato faltante

## Tecnologias

- `n8n`: orquestacion visual flexible, buen equilibrio entre personalizacion y control
- `Make`: flujos visuales rapidos para apps conectadas
- `Zapier`: automatizaciones simples y muy orientadas a integraciones listas
- `Power Automate`: automatizacion dentro de ecosistemas Microsoft
- `codigo`: cuando hace falta logica propia, control fino o integraciones especiales

Para detalles por tecnologia, leer solo la referencia necesaria:

- [references/n8n.md](references/n8n.md)
- [references/platforms.md](references/platforms.md)
- [references/integration-discovery.md](references/integration-discovery.md)

## Salidas tipicas

- mapa del flujo
- propuesta de tecnologia
- pasos de automatizacion
- campos o datos que deben viajar
- riesgos y validaciones
- version simple para usuario final

## Cuando usar apoyo

- usar `software-engineering` si la automatizacion requiere codigo real, APIs propias o infraestructura
- usar `critical-info-auditor` si el flujo toca datos sensibles, permisos o dinero

## Evitar

- asumir integraciones no mencionadas
- mezclar varias tecnologias sin motivo claro
- bajar a codigo si una plataforma resuelve mejor
- cargar referencias de todas las tecnologias a la vez
