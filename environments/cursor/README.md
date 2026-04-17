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
