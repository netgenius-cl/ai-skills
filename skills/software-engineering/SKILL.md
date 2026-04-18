---
name: software-engineering
description: Ingenieria de software para diseno, implementacion, debugging, refactor, APIs, integraciones, testing y mantenimiento de codigo. Usar cuando Codex necesite trabajar en codigo, arquitectura, bugs, integraciones tecnicas, automatizacion basada en codigo o cambios tecnicos de producto.
---

# Software Engineering

Resolver trabajo de codigo con criterio tecnico y salida clara.

## Objetivo

- entender el problema real
- cambiar lo minimo necesario
- mantener claridad y calidad
- validar cuando sea razonable
- confirmar stack y alcance antes de elegir tecnologia si no estan claros

## Casos

- bugs
- nuevas funciones
- refactors
- APIs e integraciones
- automatizacion basada en codigo
- tests
- mantenimiento tecnico

## Estilo

- preferir cambios pequenos y claros
- no abrir frentes innecesarios
- resumir riesgos reales
- no explicar internals al usuario final salvo que los pida
- no asumir C#, Python, Node, Laravel, React u otra tecnologia si no hay evidencia suficiente
- si el stack no esta claro, hacer una sola pregunta simple antes de escribir codigo
- si el usuario no es tecnico, no entregar comandos de consola como salida por defecto
- si la solucion necesita instalar o correr algo, explicar primero la opcion mas simple y pedir confirmacion antes de dar comandos

## Pregunta de scope

Si falta contexto tecnico minimo, preguntar algo corto como:

- "Quieres que esto quede como web, app o script?"
- "Lo hacemos en el stack que ya usa este proyecto o prefieres otro?"
- "Quieres que solo lo piense o que tambien te deje el codigo?"
- "Quieres algo que puedas usar directo o una base tecnica para que alguien la implemente?"

## Dependencias sugeridas

- usar `critical-info-auditor` si el cambio toca informacion sensible o flujos de alto riesgo
- usar `report-generation` si hay que convertir trabajo tecnico en informe

## Referencias

- Ver [references/working-style.md](references/working-style.md)
