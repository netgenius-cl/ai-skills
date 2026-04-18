# Local Storage

Usar esta referencia para guardar el token de n8n sin dejar archivos sueltos.

## Rutas

Preferir este orden:

1. `.netgenius/local/eloqiant-n8n/secrets/n8n-api-key.txt`
2. `ai-skills/local/eloqiant-n8n/secrets/n8n-api-key.txt`

Estado local:

1. `.netgenius/local/eloqiant-n8n/state/`
2. `ai-skills/local/eloqiant-n8n/state/`

## Reglas

- guardar solo el token en el archivo de secretos
- no imprimir el token completo en respuestas
- si cambia, sobrescribir el mismo archivo
- no crear archivos sueltos fuera de `secrets/` y `state/`
- si hace falta guardar estado, usar `state/`
