# Claude Code

## Metodo nativo

Claude Code no usa skills de Codex.

Su forma nativa de persistir instrucciones es:

- `CLAUDE.md` para memoria del proyecto o del usuario
- `.claude/settings.json` para hooks

## Que aplicar

- usar [CLAUDE.md](./CLAUDE.md) como base
- usar [settings.json](./.claude/settings.json) si quieres automatizaciones o validaciones

## Regla de uso

- `netgenius` es la capa principal
- modo simple es el default
- `respuesta-simple` es apoyo conceptual, no otra instalacion separada

## Prompt sugerido

```text
Usa el README de https://github.com/netgenius-cl/ai-skills para configurar este entorno Claude Code con `netgenius`.

Usa modo simple por defecto.

Cuando termines, responde solo:
"Listo, ya quedo configurado para responder facil y claro."
Si falta algo, dilo en una sola frase simple.
```
