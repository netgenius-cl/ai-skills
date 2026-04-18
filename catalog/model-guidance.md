# Model Guidance

Ultimo refresco: 2026-04-17

Esta guia no es una verdad fija.

Debe revisarse cada vez que el catalogo se actualice y cambien los modelos o sus puntos fuertes.

## Regla de refresco

Cuando alguien actualice este catalogo, debe revisar primero fuentes actuales y luego refrescar este archivo con:

- fecha exacta del refresco
- modelo recomendado por tipo de trabajo
- que cambio respecto a la version anterior
- si la recomendacion es una preferencia operativa del catalogo o una afirmacion respaldada por docs del proveedor

## Fuentes a revisar

- Anthropic models overview: https://docs.anthropic.com/en/docs/about-claude/models/all-models
- OpenAI models / GPT-5 family docs: https://platform.openai.com/docs/models y https://platform.openai.com/docs/guides/gpt-5
- Google Gemini / Vertex AI model docs: https://cloud.google.com/vertex-ai/generative-ai/docs/models

No dejar esta parte congelada por meses sin revisarla.

## Modos

### fast

Usar `fast` cuando:

- la tarea es clara
- hay poco riesgo
- hace falta respuesta rapida
- el cambio es pequeno o local
- la persona quiere salir del paso rapido

Esperado:

- menos vueltas
- menos contexto
- una pregunta corta si hace falta
- una recomendacion directa

### plan

Usar `plan` cuando:

- la tarea es ambigua
- hay varias opciones reales
- el cambio afecta codigo, datos o arquitectura importante
- hace falta orquestar varias skills o agentes
- un error costaria caro o haria perder tiempo

Esperado:

- mejor encuadre
- una o pocas preguntas simples
- mejor ruteo entre skills
- mas cuidado con riesgos y dependencias

## Preferencia operativa actual del catalogo

Esta es la preferencia actual de Netgenius. No es universal y puede cambiar:

- codigo profundo y analisis de datos importante: Claude Opus
- trabajo general y orquestacion cotidiana: GPT o Gemini
- tareas rapidas y generales: priorizar la opcion mas agil del entorno

## Baseline actual

### Anthropic

- Claude Opus 4.1: recomendado para trabajo profundo de codigo y razonamiento exigente.
- Claude Sonnet 4: buena opcion equilibrada cuando hace falta velocidad con buena calidad.

Base: Anthropic describe Opus 4.1 como su modelo mas capaz para razonamiento complejo y codigo avanzado.

### OpenAI

- GPT-5.1: buena opcion general y tambien fuerte para codigo y tareas agenticas.
- GPT-5 mini: mejor cuando prima velocidad y costo.

Base: OpenAI presenta GPT-5.1 como su modelo principal para coding y tareas agenticas.

### Google

- Gemini 2.5 Pro: buena opcion para razonamiento complejo, trabajo multimodal y problemas grandes.
- Gemini 2.5 Flash: buena opcion general por balance entre costo, velocidad y capacidad.

Base: Google presenta Gemini 2.5 Pro como su modelo de razonamiento mas avanzado y Gemini 2.5 Flash como su mejor balance de precio y rendimiento.

## Como usar esta guia sin rigidez

- Si el usuario ya eligio modelo, respetarlo.
- Si el entorno ya viene atado a un modelo, adaptarse a eso.
- Si el trabajo es simple, no abrir una discusion larga de modelos.
- Si el trabajo es importante, mencionar la recomendacion como sugerencia breve, no como dogma.
- Si dudas por cambios recientes del mercado, volver a verificar antes de afirmar.

## Nota sobre Antigravity

Antigravity puede variar segun version y modelo disponible.

Para este catalogo:

- usar `fast` para iteraciones rapidas
- usar `plan` cuando la tarea necesite mejor encuadre o varias piezas
- si el entorno ofrece varias familias de modelos, seguir esta guia como preferencia inicial y volver a revisar en futuras actualizaciones
