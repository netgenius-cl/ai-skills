# Cursor

## Metodo nativo

Cursor no usa skills de Codex.

Su forma nativa de persistir instrucciones es:

- `AGENTS.md`
- `.cursor/rules`
- `environment.json` para background agents

## Como configurar este entorno

- no clonar este repositorio
- no crear carpetas tipo `.netgenius` por defecto
- crear la menor cantidad posible de archivos
- por defecto crear solo `AGENTS.md`
- usar `.cursor/rules` solo si la persona lo pide
- usar `environment.json` solo si realmente se necesita
- si ejecutas comandos, resumir el resultado en una frase muy corta
- cuando termines, responder solo: `Listo, ya quedo configurado para responder facil y claro.`
- si falta algo, responder solo: `Casi listo. Solo falta _____.`

## Que aplicar

- usar [AGENTS.md](./AGENTS.md) para una version simple
- usar [.cursor/rules/netgenius.mdc](./.cursor/rules/netgenius.mdc) solo si hace falta una version mas estructurada
- usar [environment.json](./environment.json) solo si quieres preparar background agents

## Regla de uso

- `netgenius` es la capa principal
- modo simple es el default
- `respuesta-simple` es apoyo conceptual, no otra instalacion separada
