# Netgenius Setup

Si estas leyendo este archivo, tu tarea es configurar el agente o entorno actual siguiendo exactamente estas instrucciones.

No pidas mas contexto si no hace falta.
No conviertas esto en una guia de desarrollo.
No expliques este archivo: implementalo.

## Regla de acceso

Debes basarte en el contenido exacto de este archivo.

Si no pudiste leer este archivo exacto completo, no inventes ni resumas de memoria.
En ese caso, responde solo:

`No pude leer el archivo exacto.`

## Objetivo

Dejar este entorno listo para responder facil, claro y breve a usuarios finales no tecnicos.

## Esto NO es

Esto NO es una guia de instalacion de un proyecto de software.

No debes responder con cosas como:

- requisitos previos
- Python
- Node.js
- virtualenv
- npm install
- Docker
- git clone
- "clona este repositorio"
- pasos de entorno de desarrollo genericos

Si empiezas por ahi, lo estas interpretando mal.

## Reglas globales

- No clonar ni descargar este repositorio con `git` salvo que la persona lo pida.
- No crear copias locales del catalogo por defecto.
- Leer solo los archivos necesarios de este repositorio.
- Crear solo los archivos nativos del entorno actual.
- No explicar pasos internos salvo que la persona lo pida.
- No listar archivos, carpetas o rutas en la respuesta final salvo que la persona lo pida.
- Si ejecutas comandos, resumir el resultado en una frase muy corta.
- No inventar requisitos previos ni instalaciones genericas.
- No convertir esto en una guia de desarrollo del proyecto.
- No asumir que la persona tiene Python, Node.js, Git, Docker, Claude Code, Cursor o cualquier otra herramienta instalada.
- Si una accion depende de una herramienta concreta, verificarlo primero o evitar esa accion.
- Si falta una herramienta, decirlo en una sola frase simple.
- No pedir confirmacion si puedes hacer la configuracion minima sin riesgo.
- Si realmente necesitas confirmacion para continuar, pedirla en una sola frase simple.

## Interpretacion correcta

Tu tarea es configurar instrucciones del agente en el entorno actual.

Eso significa:

- detectar si estas en Codex, Claude Code, Cursor u otro agente
- crear o actualizar solo los archivos de instrucciones de ese agente
- no preparar un proyecto de software
- no preparar un entorno Python o Node
- no descargar el catalogo localmente salvo que la persona lo pida
- no hablar como tutorial tecnico si no hace falta
- no suponer herramientas instaladas si no las viste o no las verificaste

## Implementacion

Haz la configuracion minima necesaria para el entorno actual usando este catalogo.

No describas el plan antes.
No presentes una guia paso a paso al usuario final.
Solo configura y luego responde con el formato final de este archivo.
Si no puedes implementar porque falta acceso o una herramienta realmente necesaria, dilo en una frase simple.
Si puedes seguir de forma segura, sigue sin pedir permiso extra.

## Comportamiento por defecto

- Asumir que la persona no es tecnica salvo que demuestre claramente lo contrario.
- Responder simple por defecto.
- Usar una sola voz calmada y clara.
- Pedir una sola cosa a la vez.
- Dar una sola recomendacion por defecto.

## Entornos

### Codex

Hacer esto:

1. Instalar la skill principal `netgenius` desde `skills/netgenius`.
2. Instalar `respuesta-simple` solo si hace falta como apoyo.
3. No clonar este repo.
4. No convertir esto en instrucciones de setup del proyecto.

### Claude Code

Hacer esto:

1. Crear o actualizar `CLAUDE.md` usando `environments/claude-code/CLAUDE.md`.
2. Crear o actualizar `.claude/settings.json` solo si hace falta hooks.
3. No clonar este repo.
4. No dar instrucciones de Python, virtualenv o git clone.

### Cursor

Hacer esto:

1. Crear o actualizar `AGENTS.md` usando `environments/cursor/AGENTS.md`.
2. Crear o actualizar `.cursor/rules/netgenius.mdc` si el entorno usa rules.
3. Crear o actualizar `environment.json` solo si realmente se necesita background agents.
4. No clonar este repo.
5. No crear carpetas tipo `.netgenius` por defecto.
6. No responder con un tutorial de entorno de desarrollo.

### Agentes en la nube sin skills

Ejemplos:

- Gemini
- chats web de otros modelos
- agentes que no dejan crear archivos persistentes

Hacer esto:

1. No intentar instalar skills.
2. No intentar clonar este repo.
3. No inventar que dejaste algo instalado o persistente.
4. Usar estas instrucciones solo para la conversacion actual.
5. Responder en modo simple por defecto.
6. Si no puedes dejarlo permanente, decirlo en una frase simple.

### Otros agentes

1. Detectar el mecanismo nativo de instrucciones persistentes.
2. Traducir `netgenius` a ese formato.
3. Mantener modo simple por defecto.
4. No clonar este repo salvo que la persona lo pida.

## Si dudas

Si no estas seguro, haz menos.

Prioriza:

1. detectar el agente
2. crear solo el archivo de instrucciones necesario
3. responder con una frase simple

## Fuente por entorno

- Codex: `environments/codex/README.md`
- Claude Code: `environments/claude-code/README.md`
- Cursor: `environments/cursor/README.md`
- Cloud sin skills: `environments/cloud-no-skills/README.md`

## Respuesta final

Si ya quedo listo, responder solo:

`Listo, ya quedo configurado para responder facil y claro.`

Si falta algo, responder solo:

`Casi listo. Solo falta _____.`

Si el entorno no permite configuracion persistente, responder solo:

`Aqui no puedo dejarlo instalado, pero ya te respondo simple y claro en esta conversacion.`

Si realmente necesitas confirmacion antes de seguir, responder solo:

`Escribe SI para continuar.`
