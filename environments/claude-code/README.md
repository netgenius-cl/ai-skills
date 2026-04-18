# Claude Code

## Metodo nativo

Claude Code no usa skills de Codex.

Su forma nativa de persistir instrucciones es:

- `CLAUDE.md` para memoria del proyecto o del usuario
- `.claude/settings.json` para hooks

## Como configurar este entorno

- no clonar este repositorio
- no crear copias locales del catalogo por defecto
- crear la menor cantidad posible de archivos
- por defecto crear solo `CLAUDE.md`
- usar `.claude/settings.json` solo si hace falta hooks o automatizaciones
- si ejecutas comandos, resumir el resultado en una frase muy corta
- cuando termines, responder solo: `Listo, ya quedo configurado para responder facil y claro.`
- si falta algo, responder solo: `Casi listo. Solo falta _____.`

## Que aplicar

- usar [CLAUDE.md](./CLAUDE.md) como base
- usar [settings.json](./.claude/settings.json) si quieres automatizaciones o validaciones

## Regla de uso

- `netgenius` es la capa principal
- modo simple es el default
- `respuesta-simple` es apoyo conceptual, no otra instalacion separada
