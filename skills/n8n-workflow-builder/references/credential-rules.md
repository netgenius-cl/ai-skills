# Credential Rules

Usar esta referencia antes de cada `PUT` o `POST`.

## OAuth

Para nodos como Gmail o Google Sheets:

- usar una sola key en `credentials`
- no usar `authentication` ni `genericAuthType` en `parameters`
- no mezclar con `httpHeaderAuth`

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
