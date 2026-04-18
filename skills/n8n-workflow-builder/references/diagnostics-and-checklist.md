# Diagnostics And Checklist

Usar esta referencia para diagnosticar workflows con problemas y antes de activarlos.

## Error comun

`The workflow has issues and cannot be executed`

Esto suele ser validacion previa del workflow, no un error de ejecucion.

## Causas frecuentes

- `googleSheets` con `documentId` vacio
- `googleSheets` con `sheetName` vacio
- `gmail` reply con `messageId` invalido
- credential asignada con tipo incorrecto

## Diagnostico por API

```js
d.nodes.forEach(node => {
  if (node.type.includes('googleSheets')) {
    const docId = node.parameters?.documentId?.value ?? node.parameters?.documentId ?? '';
    const sheet = node.parameters?.sheetName?.value ?? node.parameters?.sheetName ?? '';
    console.log(node.id, node.name, '| docId:', docId || 'EMPTY', '| sheet:', sheet || 'EMPTY');
  }
});
```

## Regla para Sheets

Si un nodo de Google Sheets queda sin `documentId` real:

- dejarlo marcado en el nombre con `TODO`
- no activarlo como si estuviera listo

Ejemplo:

- `Escribir en Sheet [TODO: configurar Sheet]`

## Checklist antes de activar

```text
[ ] Todos los nodos Google Sheets tienen documentId real
[ ] Todos los nodos Google Sheets tienen sheetName real
[ ] Todos los nodos con credentials muestran un tipo correcto
[ ] Los chainLlm tienen el sub-nodo LLM conectado por ai_languageModel
[ ] Las connections usan nombres exactos de nodos
[ ] El Gmail Trigger tiene filtro o esta en modo all emails
[ ] El trigger principal esta realmente configurado
```
