# n8n

Usar esta referencia solo cuando la tecnologia elegida sea `n8n` o cuando haya que compararla con otra.

## Cuando conviene

- flujos medianos o complejos
- varias integraciones en un mismo proceso
- necesidad de control fino en datos o ramificaciones
- webhooks, cron, transformaciones y logica intermedia

## Como pensar un flujo en n8n

1. trigger
2. normalizacion de datos
3. decisiones o filtros
4. llamadas a servicios
5. manejo de errores
6. salida o confirmacion

## Piezas comunes

- `Webhook` para entradas externas
- `Schedule Trigger` para ejecucion programada
- nodos de apps para servicios conocidos
- `HTTP Request` para APIs no cubiertas
- `Set`, `Code` o transformaciones para ordenar datos
- `IF`, `Switch` y ramificaciones para decisiones

## Buenas practicas

- nombrar cada paso por intencion
- no mezclar demasiada logica en un solo nodo
- separar transformacion, validacion y envio
- definir que pasa si falla una app externa
- dejar claro que datos entran y cuales salen

## Cuando pedir apoyo de codigo

- autenticaciones especiales
- firmas, hashing o transforms complejas
- integraciones internas sin conector estable
- logica demasiado custom para nodos visuales

## Salida recomendada

- trigger elegido
- nodos o pasos principales
- datos clave por paso
- errores esperables
- decision de por que n8n calza bien
