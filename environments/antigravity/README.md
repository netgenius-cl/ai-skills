# Antigravity

## Metodo nativo

Para este catalogo, Antigravity debe tratarse como un entorno que puede usar instrucciones persistentes de proyecto.

Prioridad recomendada:

1. `AGENTS.md`
2. `GEMINI.md` solo como compatibilidad si esa version o configuracion todavia lo usa

## Como configurar este entorno

- no clonar este repositorio
- no crear carpetas raras por defecto
- crear la menor cantidad posible de archivos
- por defecto crear solo `AGENTS.md`
- crear `GEMINI.md` solo si hace falta compatibilidad o si ese entorno lo usa como prioridad
- si ejecutas comandos, resumir el resultado en una frase muy corta
- cuando termines, responder solo: `Listo, ya quedo configurado para responder facil y claro.`
- si falta algo, responder solo: `Casi listo. Solo falta _____.`

## Que aplicar

- usar [AGENTS.md](./AGENTS.md) como base compartida
- usar [GEMINI.md](./GEMINI.md) si el entorno todavia lo requiere
- revisar [../../catalog/model-guidance.md](../../catalog/model-guidance.md) para modos y modelos

## Modos

### fast

Usarlo para:

- iteraciones rapidas
- cambios chicos
- exploracion corta
- respuestas simples

### plan

Usarlo para:

- tareas ambiguas
- decisiones de arquitectura
- codigo importante
- analisis de datos profundo
- trabajo con varias skills o agentes

## Regla de uso

- `netgenius` es la capa principal
- modo simple es el default frente al usuario final
- `respuesta-simple` es apoyo conceptual
- `fast` y `plan` se eligen segun el trabajo, no por costumbre
- si hay que recomendar modelo, usar primero `../../catalog/model-guidance.md`
