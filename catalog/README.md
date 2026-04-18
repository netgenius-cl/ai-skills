# Skill Catalog

Esta carpeta organiza el catalogo para que pueda crecer sin volver el repo inmanejable.

## Principios

- `netgenius` es la puerta de entrada.
- `context-index.md` es la carga minima para contexto rapido.
- `skill-maintainer` asegura, instala, actualiza o prepara skills cuando hace falta.
- Las skills de trabajo viven separadas por responsabilidad.
- El orquestador consulta el indice antes de decidir.
- Si una skill no existe o no se puede instalar, se hace fallback con una explicacion simple.
- El indice no es solo una lista: tambien define intenciones, orden de decision y apoyos opcionales.
- La recomendacion de modos y modelos vive separada para poder refrescarla sin romper las skills.

## Flujo

1. `netgenius` carga `context-index.md` si necesita orientacion rapida.
2. Detecta el tipo de trabajo.
3. Consulta `skills-index.yaml` solo si hace falta mas detalle.
4. Si falta una skill importante, pide ayuda a `skill-maintainer`.
5. Usa la skill correcta.
6. Devuelve una respuesta simple al usuario final.

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
- Si la persona habla de automatizaciones, workflows, webhooks o n8n, priorizar `automation-builder`.
- Si la persona habla de navegar una web, login, formularios, botones o URL, priorizar `browser`.
- Si hay codigo pero el stack no esta claro, no elegir tecnologia todavia: hacer una sola pregunta simple.
- Si hay automatizacion y no esta clara la tecnologia o las integraciones, aclararlo primero desde el orquestador.
- Si el trabajo es mixto, usar una skill principal y sumar solo el menor numero de apoyos posible.

## Dominios iniciales

- `maintenance`
- `storage`
- `automation`
- `browser`
- `engineering`
- `analytics`
- `reporting`
- `dashboards`
- `assurance`
