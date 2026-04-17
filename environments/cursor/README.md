# Cursor

## Metodo nativo

Cursor no usa skills de Codex.

Su forma nativa de persistir instrucciones es:

- `AGENTS.md`
- `.cursor/rules`
- `environment.json` para background agents

## Que aplicar

- usar [AGENTS.md](./AGENTS.md) para una version simple
- usar [.cursor/rules/netgenius.mdc](./.cursor/rules/netgenius.mdc) para una version mas estructurada
- usar [environment.json](./environment.json) si quieres preparar background agents

## Regla de uso

- `netgenius` es la capa principal
- modo simple es el default
- `respuesta-simple` es apoyo conceptual, no otra instalacion separada

## Prompt sugerido

```text
Usa el README de https://github.com/netgenius-cl/ai-skills para configurar este entorno Cursor con `netgenius`.

Usa modo simple por defecto.

Cuando termines, responde solo:
"Listo, ya quedo configurado para responder facil y claro."
Si falta algo, dilo en una sola frase simple.
```

## Confirmacion esperada

`Listo, ya quedo configurado para responder facil y claro.`
