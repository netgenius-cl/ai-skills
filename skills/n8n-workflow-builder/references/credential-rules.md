# Credential Rules

Usar esta referencia antes de cada `PUT` o `POST`.

## OAuth

Para nodos como Gmail o Google Sheets:

- usar una sola key en `credentials`
- no usar `authentication` ni `genericAuthType` en `parameters`
- no mezclar con `httpHeaderAuth`

## Google Sheets

- nodos `googleSheets` requieren `googleSheetsOAuth2Api`
- no usar `googleOAuth2Api` en nodos de Sheets
- si `documentId` queda vacio, el nodo queda invalido
- si `sheetName` queda vacio, el nodo queda invalido

## HTTP Header Auth

Para `HTTP Request` con auth por credential:

- `authentication: "genericCredentialType"`
- `genericAuthType: "httpHeaderAuth"`
- una sola key en `credentials`
- no hardcodear tokens en `headerParameters`
- no usar `sendHeaders` + `headerParameters` para pasar el token
- no usar `nodeCredentialType`

## Regla general

- cada nodo tiene exactamente una key en `credentials`
- primero descubrir ids o nombres reales desde la instancia
- nunca escribir ids fijos en esta skill
- al editar, tocar un nodo por vez
- usar guardas tipo `if (n.id !== 'nX') return n;`
- no hacer `map` generico sobre todos los nodos cuando el cambio es puntual

## Check sugerido

```js
d.nodes.forEach(node => {
  const credKeys = Object.keys(node.credentials || {});
  if (credKeys.length > 1) throw new Error(`${node.id} tiene ${credKeys.join(',')} y solo una credential es valida`);
  console.log(node.id, node.type, '|', node.parameters?.authentication ?? '-', '|', credKeys);
});
```

## Check mas estricto

```js
const gmailTypes = ['n8n-nodes-base.gmail', 'n8n-nodes-base.gmailTrigger'];

d.nodes.forEach(node => {
  const credKeys = Object.keys(node.credentials || {});
  const authParam = node.parameters?.authentication;

  if (gmailTypes.includes(node.type)) {
    if (authParam) throw new Error(`${node.id} Gmail no debe tener authentication`);
    if (!credKeys.includes('gmailOAuth2')) throw new Error(`${node.id} Gmail sin gmailOAuth2`);
    if (credKeys.length > 1) throw new Error(`${node.id} Gmail tiene credentials extra: ${credKeys.join(',')}`);
  }

  if (node.type.includes('googleSheets')) {
    if (!credKeys.includes('googleSheetsOAuth2Api')) {
      throw new Error(`${node.id} Google Sheets sin googleSheetsOAuth2Api`);
    }
  }
});
```
