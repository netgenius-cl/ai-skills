# Skill Catalog

Esta carpeta organiza el catalogo para que pueda crecer sin volver el repo inmanejable.

## Principios

- `netgenius` es la puerta de entrada.
- `skill-maintainer` asegura, instala, actualiza o prepara skills cuando hace falta.
- Las skills de trabajo viven separadas por responsabilidad.
- El orquestador consulta el indice antes de decidir.
- Si una skill no existe o no se puede instalar, se hace fallback con una explicacion simple.

## Flujo

1. `netgenius` detecta el tipo de trabajo.
2. Consulta `skills-index.yaml`.
3. Si falta una skill importante, pide ayuda a `skill-maintainer`.
4. Usa la skill correcta.
5. Devuelve una respuesta simple al usuario final.

## Dominios iniciales

- `maintenance`
- `analytics`
- `reporting`
- `dashboards`
- `assurance`

