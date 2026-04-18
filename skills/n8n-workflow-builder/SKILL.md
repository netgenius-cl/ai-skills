---
name: n8n-workflow-builder
description: Usar cuando pidan crear, modificar, respaldar o desplegar workflows en n8n via API. Triggers comunes: crea un workflow en n8n, modifica el workflow, respalda el workflow, hazlo en n8n, genera el flujo.
argument-hint: Describe el flujo: que lo dispara, que hace, que nodos necesita y si ya existe un workflow previo.
user-invocable: true
---

# n8n Workflow Builder

Resolver workflows de n8n via API con estructura clara, sin secretos hardcodeados y sin archivos sueltos.

## Instancia

- URL: `https://n8n.eloqiant.com`
- auth header: `X-N8N-API-KEY: {token}`

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
- `tmp/` para archivos temporales

## Nombres

Usar nombres faciles y descriptivos en minusculas con guiones.

Ejemplos:

- `lineas-de-tiempo-n8n`
- `cotizaciones-whatsapp-n8n`
- `seguimiento-clientes-n8n`

## Flujo obligatorio

1. hacer `GET /api/v1/workflows/:id` si es modificacion
2. construir o ajustar JSON en `tmp/`
3. verificar credenciales con el check antes del envio
4. hacer `PUT /api/v1/workflows/:id` o `POST /api/v1/workflows`
5. volver a traer el workflow y validar que quedo bien
6. borrar los temporales

## Reglas de credenciales

No hardcodear ids, nombres ni secretos de credenciales en la skill.

Primero obtener lo disponible desde la instancia o desde el contexto actual.

### OAuth

Para nodos tipo Gmail o Google:

- usar exactamente una key en `credentials`
- no agregar `authentication` ni `genericAuthType` en `parameters`
- no mezclar con `httpHeaderAuth`

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

## Check antes de subir

Siempre correr un check local del JSON antes de `PUT` o `POST`.

Usar placeholders o listas construidas al vuelo, no ids fijos dentro del script.

Patron minimo:

```js
d.nodes.forEach(node => {
  const credKeys = Object.keys(node.credentials || {});
  if (credKeys.length > 1) throw new Error(`${node.id} tiene ${credKeys} y solo una credential es valida`);
  console.log(node.id, node.type, '|', node.parameters?.authentication ?? '—', '|', credKeys);
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

## Operaciones

### Crear

```bash
curl -s -X POST "https://n8n.eloqiant.com/api/v1/workflows" \
  -H "X-N8N-API-KEY: $TOKEN" \
  -H "Content-Type: application/json" \
  -d @workflow.json
```

### Modificar

```bash
curl -s "https://n8n.eloqiant.com/api/v1/workflows/{id}" \
  -H "X-N8N-API-KEY: $TOKEN" > wf.json
```

```bash
curl -s -X PUT "https://n8n.eloqiant.com/api/v1/workflows/{id}" \
  -H "X-N8N-API-KEY: $TOKEN" \
  -H "Content-Type: application/json" \
  -d @wf-put.json > wf-result.json
```

### Activar o desactivar

```bash
curl -s -X POST "https://n8n.eloqiant.com/api/v1/workflows/{id}/activate" \
  -H "X-N8N-API-KEY: $TOKEN"
```

```bash
curl -s -X POST "https://n8n.eloqiant.com/api/v1/workflows/{id}/deactivate" \
  -H "X-N8N-API-KEY: $TOKEN"
```

### Backup

Guardar respaldos dentro de `backups/<nombre-simple>/`.

## Limpieza

Siempre borrar temporales al terminar.

No dejar `wf.json`, `wf-put.json` o similares fuera de `tmp/`.

## Referencias

- Ver [references/credential-rules.md](references/credential-rules.md) para reglas de credenciales y checks.
- Ver [references/payload-rules.md](references/payload-rules.md) para campos permitidos en `PUT`.
- Ver [references/storage-and-naming.md](references/storage-and-naming.md) para directorios y nombres simples.
