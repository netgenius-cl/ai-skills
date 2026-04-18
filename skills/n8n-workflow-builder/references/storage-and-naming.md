# Storage And Naming

Usar esta referencia para no dejar archivos sueltos.

## Directorios

Preferir este orden:

1. `.netgenius/local/n8n-workflow-builder/`
2. `ai-skills/local/n8n-workflow-builder/`

Subdirectorios:

- `workflows/`
- `backups/`
- `docs/`
- `tmp/`

## Nombres

Usar minusculas con guiones.

Ejemplos:

- `lineas-de-tiempo-n8n`
- `cotizaciones-whatsapp-n8n`
- `recordatorios-cobranza-n8n`

## Regla

- un workflow por carpeta descriptiva si hace falta versionarlo
- si el workflow es grande, crear una nota corta en `docs/<nombre-simple>.md`
- esa nota debe servir para revisar el flujo paso a paso sin perderse
- compartir el enlace del workflow solo despues de confirmar el `id` y la carga final
- agregar notas o comentarios visibles dentro del flujo cuando sea complejo
- temporales siempre en `tmp/`
- respaldos siempre en `backups/`

## Backups

- si el repo ya usa `services/n8n/workflows/`, preferir esa ruta para backups del proyecto
- si no existe esa carpeta, usar `backups/<nombre-simple>/`
- guardar backup antes del cambio
- guardar backup final despues del cambio
- usar fecha y hora en el nombre
- no sobrescribir el backup anterior

Ejemplos:

- `services/n8n/workflows/cotizaciones-whatsapp-n8n-20260418.json`
- `backups/cotizaciones-whatsapp-n8n/cotizaciones-whatsapp-n8n-before-20260418-153000.json`
- `backups/cotizaciones-whatsapp-n8n/cotizaciones-whatsapp-n8n-after-20260418-154200.json`
