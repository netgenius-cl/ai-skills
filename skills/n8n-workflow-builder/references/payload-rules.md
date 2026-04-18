# Payload Rules

Usar esta referencia al construir el body de `PUT`.

## Campos permitidos

```json
{
  "name": "...",
  "nodes": [],
  "connections": {},
  "settings": { "executionOrder": "v1" },
  "staticData": null
}
```

## Regla

- no reenviar metadata, timestamps ni campos internos de la respuesta original
- traer el workflow, limpiar el payload y recien despues subir
- si editas, conservar el flujo y parchear solo el nodo o bloque que cambia
- despues del `PUT` o `POST`, volver a traer el workflow antes de confirmar exito

## Campos que rompen el `PUT`

Si se incluyen, pueden devolver `400`:

- `versionId`
- `active`
- `callerPolicy`
- `availableInMCP`
- `binaryMode`
