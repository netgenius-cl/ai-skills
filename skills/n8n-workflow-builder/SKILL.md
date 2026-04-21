---
name: n8n-workflow-builder
description: Usar cuando pidan crear, modificar, respaldar o desplegar workflows en n8n via API. Triggers comunes: crea un workflow en n8n, modifica el workflow, respalda el workflow, hazlo en n8n, genera el flujo.
argument-hint: Describe el flujo: que lo dispara, que hace, que nodos necesita y si ya existe un workflow previo.
user-invocable: true
---

# n8n Workflow Builder

Resolver workflows de n8n via API con estructura clara, sin secretos hardcodeados y sin archivos sueltos.

## Instancia

- URL: `https://n8n.netgenius.cl`
- auth header: `X-N8N-API-KEY: {token}`

## Regla de instancia

Si se detecta `n8n` y la persona no indica otra instancia:

- leer `../../catalog/service-defaults.json`
- usar `https://n8n.netgenius.cl` por defecto
- asumir la instancia compartida de Netgenius como camino base
- solo cambiar de instancia si la persona da otra URL o dice claramente que usa otro n8n

## Token

- no hardcodear tokens en la skill
- usar el token local definido por `eloqiant-n8n`
- si falta token, volver a `eloqiant-n8n` para conectarlo primero

## Directorios de trabajo

Usar nombres simples y descriptivos.

Preferir este orden:

1. `.netgenius/local/n8n-workflow-builder/`
2. `ai-skills/local/n8n-workflow-builder/`

Subdirectorios:

- `workflows/` para versiones listas
- `backups/` para respaldos
- `docs/` para notas simples de trabajo
- `tmp/` para archivos temporales

## Nombres

Usar nombres faciles y descriptivos en minusculas con guiones.

Ejemplos:

- `lineas-de-tiempo-n8n`
- `cotizaciones-whatsapp-n8n`
- `seguimiento-clientes-n8n`

## Aterrizar el flujo

Ayudar tambien con el concepto de flujo, no solo con el JSON.

Explicarlo simple:

- `disparador`: que inicia el flujo
- `pasos`: que hace en el medio
- `salida`: que devuelve, crea o responde

Si la persona esta perdida, bajar primero el flujo a estas tres partes antes de hablar de nodos.

## Alcance y disciplina

Cuando esta skill toma un caso de `n8n`, es la ruta principal.

- priorizar esta skill por sobre caminos manuales o tangenciales
- no salir del alcance hacia otras herramientas si el trabajo real es `n8n`
- no intentar abrir navegador para hacer el workflow manualmente
- no desviar a una solucion manual salvo que el bloqueo real sea conectar una credencial en la UI
- para crear, leer, modificar, activar, desactivar o respaldar workflows, usar API y archivos locales
- leer primero el workflow actual y sus cambios antes de tocarlo

## Herramientas correctas

Para trabajo de workflows en `n8n`:

- usar API de `n8n.netgenius.cl`
- usar archivos temporales y respaldos locales
- usar notas en `docs/` para workflows grandes
- no usar `browser` para construir o editar workflows
- no pedir pasos manuales si la API resuelve el trabajo

## Cuando el pedido es muy general

Si dicen algo muy amplio como `quiero un agente` o `quiero automatizar algo`:

- hacer una sola pregunta corta: `Cual? tienes uno en mente?`
- no inventar el caso de uso
- no bajar a nodos o APIs antes de aterrizar el objetivo

## Lista de lo que hace falta

Cuando todavia faltan datos, dar una lista simple de lo necesario.

Lista base:

- objetivo
- disparador
- apps o servicios
- datos que entran
- respuesta o salida esperada
- credenciales o cuentas
- condiciones o validaciones
- que hacer si algo falla

## Flujo obligatorio

1. hacer `GET /api/v1/workflows/:id` si es modificacion
2. leer bien el workflow actual antes de cambiarlo
3. si es modificacion, crear backup obligatorio antes de subir cualquier cambio
4. si el workflow es grande o tiene muchos nodos, escribir primero un documento simple en `docs/` para ir revisando
5. construir o ajustar JSON en `tmp/`
6. agregar comentarios o notas utiles dentro del flujo si ayuda a entenderlo
7. verificar credenciales con el check antes del envio
8. hacer `PUT /api/v1/workflows/:id` o `POST /api/v1/workflows`
9. volver a traer el workflow y validar que quedo bien
10. si quedo bien, construir y compartir el enlace correcto del workflow
11. borrar los temporales

## Enlace del workflow

Si el workflow se crea o actualiza bien:

- usar el `id` real devuelto o confirmado por el refetch
- compartir el enlace directo: `https://n8n.netgenius.cl/workflow/<id>`
- no decir que esta listo antes de confirmar la carga con un `GET` final
- si el refetch falla, no prometer que quedo bien

## Documento simple para workflows grandes

Si el workflow es grande, largo o facil de perder:

- decir en simple: `Escribire un documento para ir revisando.`
- crear una nota corta en `docs/<nombre-simple>.md`
- usar esa nota como guia de trabajo mientras se arma o corrige el flujo
- mantenerla breve, clara y facil de seguir

Usar esta estructura simple:

```md
# <nombre-simple>

## Objetivo

## Disparador

## Pasos principales

## Nodos pendientes

## Credenciales a revisar

## Check final
```

## Reglas de credenciales

No hardcodear ids, nombres ni secretos de credenciales en la skill.

Primero obtener lo disponible desde la instancia o desde el contexto actual.

### OAuth

Para nodos tipo Gmail o Google:

- usar exactamente una key en `credentials`
- no agregar `authentication` ni `genericAuthType` en `parameters`
- no mezclar con `httpHeaderAuth`

### Google Sheets

Para nodos `googleSheets`:

- usar `googleSheetsOAuth2Api`
- no usar `googleOAuth2Api` en nodos de Sheets
- si `documentId` o `sheetName` quedan vacios, el nodo queda invalido
- si falta el dato real, dejarlo claro en el nombre del nodo con un `TODO`

### HTTP Header Auth

Para nodos `HTTP Request` con auth por header:

- usar `authentication: "genericCredentialType"`
- usar `genericAuthType: "httpHeaderAuth"`
- usar exactamente una key en `credentials`
- no mandar tokens a mano con headers hardcodeados si existe credential
- no usar `sendHeaders` + `headerParameters` para el token porque se puede perder al guardar
- no usar `nodeCredentialType`

### Regla general

- cada nodo tiene exactamente una key en `credentials`
- nunca dos
- nunca ids o nombres fijos escritos en la skill
- al editar, parchear un nodo a la vez
- no usar un `map` generico sobre todos los nodos si solo cambia uno

## Comentarios y notas en el flujo

Cuando el flujo sea mediano o grande:

- usar nombres de nodo claros y descriptivos
- agregar notas para separar bloques o explicar logica delicada
- preferir `n8n-nodes-base.stickyNote` para comentarios visibles dentro del workflow
- usar notas cortas y utiles, no decorativas
- dejar claro donde empieza el trigger, donde vive la logica y donde sale el resultado

Ejemplos de notas utiles:

- `Entrada del flujo`
- `Validacion antes de llamar al API`
- `IA genera la respuesta`
- `Salida al usuario`

## AI y scraping

Usar ejemplos base reales para crear nodos AI o de scraping.

Para detalles, ver [references/ai-and-scraping.md](references/ai-and-scraping.md).

## Diseno de prompts para agentes IA

Antes de escribir un prompt para `chainLlm` o `agent`:

- preguntar si los datos son reales o de ejemplo
- preguntar el tono y la estructura esperada
- preguntar que no debe hacer el agente

No asumir esto por cuenta propia si cambia la calidad de la respuesta.

Para la guia exacta y una plantilla de cotizador, ver [references/prompt-design.md](references/prompt-design.md).

## Check antes de subir

Siempre correr un check local del JSON antes de `PUT` o `POST`.

Usar placeholders o listas construidas al vuelo, no ids fijos dentro del script.

Patron minimo:

```js
d.nodes.forEach(node => {
  const credKeys = Object.keys(node.credentials || {});
  if (credKeys.length > 1) throw new Error(`${node.id} tiene ${credKeys} y solo una credential es valida`);
  console.log(node.id, node.type, '|', node.parameters?.authentication ?? '-', '|', credKeys);
});
```

Para reglas mas detalladas, ver [references/credential-rules.md](references/credential-rules.md).

## PUT body permitido

Usar solo:

```json
{
  "name": "...",
  "nodes": [],
  "connections": {},
  "settings": { "executionOrder": "v1" },
  "staticData": null
}
```

No enviar campos de estado, metadata o timestamps de la respuesta original.

Para la lista ampliada de campos que rompen el `PUT`, ver [references/payload-rules.md](references/payload-rules.md).

## Operaciones

### Crear

```bash
curl -s -X POST "https://n8n.netgenius.cl/api/v1/workflows" \
  -H "X-N8N-API-KEY: $TOKEN" \
  -H "Content-Type: application/json" \
  -d @workflow.json
```

Guardar el `id` de respuesta para futuras modificaciones.

### Modificar

```bash
curl -s "https://n8n.netgenius.cl/api/v1/workflows/{id}" \
  -H "X-N8N-API-KEY: $TOKEN" > wf.json
```

```bash
curl -s -X PUT "https://n8n.netgenius.cl/api/v1/workflows/{id}" \
  -H "X-N8N-API-KEY: $TOKEN" \
  -H "Content-Type: application/json" \
  -d @wf-put.json > wf-result.json
```

### Activar o desactivar

```bash
curl -s -X POST "https://n8n.netgenius.cl/api/v1/workflows/{id}/activate" \
  -H "X-N8N-API-KEY: $TOKEN"
```

```bash
curl -s -X POST "https://n8n.netgenius.cl/api/v1/workflows/{id}/deactivate" \
  -H "X-N8N-API-KEY: $TOKEN"
```

### Backup

Guardar respaldos dentro de `backups/<nombre-simple>/`.

## Backups rigurosos

Si se va a modificar un workflow existente:

- hacer backup antes de tocar nada
- guardar el original completo antes del cambio
- guardar una copia final despues del cambio si quedo bien
- usar nombres con fecha y hora para no sobrescribir
- no subir cambios si el backup previo no existe
- leer el original y el payload final antes del `PUT`
- confirmar por refetch que el workflow guardado coincide con lo esperado

Formato sugerido:

- `backups/<nombre-simple>/<nombre-simple>-before-YYYYMMDD-HHMMSS.json`
- `backups/<nombre-simple>/<nombre-simple>-after-YYYYMMDD-HHMMSS.json`

Nunca reemplazar el unico backup anterior.

## Errores comunes y checklist

Para diagnostico y activacion segura, ver [references/diagnostics-and-checklist.md](references/diagnostics-and-checklist.md).

## Ejemplo completo

Si hace falta un caso base real y documentado nodo por nodo, usar [references/example-cotizador-email.md](references/example-cotizador-email.md).

## Limpieza

Siempre borrar temporales al terminar.

No dejar `wf.json`, `wf-put.json` o similares fuera de `tmp/`.

## Referencias

- Ver [references/credential-rules.md](references/credential-rules.md) para reglas de credenciales y checks.
- Ver [references/payload-rules.md](references/payload-rules.md) para campos permitidos en `PUT`.
- Ver [references/storage-and-naming.md](references/storage-and-naming.md) para directorios y nombres simples.
- Ver [references/ai-and-scraping.md](references/ai-and-scraping.md) para nodos AI, LangChain y scraping.
- Ver [references/prompt-design.md](references/prompt-design.md) para prompts de agentes IA.
- Ver [references/diagnostics-and-checklist.md](references/diagnostics-and-checklist.md) para diagnostico y checklist final.
- Ver [references/example-cotizador-email.md](references/example-cotizador-email.md) para un workflow de referencia completo.
