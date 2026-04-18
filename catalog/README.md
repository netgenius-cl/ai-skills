# Skill Catalog

Esta carpeta organiza el catalogo para que pueda crecer sin volver el repo inmanejable.

## Principios

- `netgenius` es la puerta de entrada.
- `skill-maintainer` asegura, instala, actualiza o prepara skills cuando hace falta.
- Las skills de trabajo viven separadas por responsabilidad.
- El orquestador consulta el indice antes de decidir.
- Si una skill no existe o no se puede instalar, se hace fallback con una explicacion simple.
- El indice no es solo una lista: tambien define intenciones, orden de decision y apoyos opcionales.
- La recomendacion de modos y modelos vive separada para poder refrescarla sin romper las skills.

## Flujo

1. `netgenius` detecta el tipo de trabajo.
2. Consulta `skills-index.yaml`.
3. Si falta una skill importante, pide ayuda a `skill-maintainer`.
4. Usa la skill correcta.
5. Devuelve una respuesta simple al usuario final.

## Que debe resolver el indice

- skill principal por intencion
- palabras gatillo para enrutar
- skills de apoyo cuando el trabajo mezcla areas
- orden de decision para evitar saltar directo a codigo o setup
- fallback cuando una capacidad no esta disponible

## Guia viva de modelos

Usar [model-guidance.md](./model-guidance.md) como capa separada para:

- explicar `fast` y `plan`
- sugerir modelos segun tipo de tarea
- registrar la fecha de refresco
- dejar claro que esa parte debe volver a verificarse cuando cambien los modelos

## Casos importantes

- Si la persona habla de carpetas de Drive, rutas sincronizadas o enlaces compartidos, priorizar `google-drive`.
- Si hay codigo pero el stack no esta claro, no elegir tecnologia todavia: hacer una sola pregunta simple.
- Si el trabajo es mixto, usar una skill principal y sumar solo el menor numero de apoyos posible.

## Dominios iniciales

- `maintenance`
- `storage`
- `engineering`
- `analytics`
- `reporting`
- `dashboards`
- `assurance`
