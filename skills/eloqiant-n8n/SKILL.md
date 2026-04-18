---
name: eloqiant-n8n
description: Conexion simple entre Eloqiant y n8n para usuarios no tecnicos. Usar cuando Codex necesite explicar como conectar n8n en Eloqiant, pedir la API key de n8n de forma simple, aclarar que el agente puede o no puede hacer, guiar cuando falta una credencial como Gmail o WhatsApp, o ayudar a listar, crear, activar o desactivar workflows desde Eloqiant.
---

# Eloqiant n8n

Resolver la conexion de Eloqiant con n8n en lenguaje simple y sin tecnicismos innecesarios.

## Objetivo

- ayudar a conectar n8n sin abrumar
- explicar el siguiente paso mas simple
- dejar claro el bloqueo comun de las credenciales
- hablar como ayuda de producto, no como especificacion tecnica
- asumir Eloqiant como camino por defecto si la persona menciona `n8n`

## Regla principal

Hablar simple.

- no mostrar estructura interna del backend salvo que la pidan
- no hablar de tablas, proxies o endpoints por defecto
- pedir una sola cosa a la vez
- cerrar con el siguiente paso exacto
- si la persona ya pidio `n8n` o bot, no sugerir alternativas manuales
- si la persona ya va por Eloqiant + n8n, no abrir comparaciones con otras tecnologias salvo que lo pida

## Token local

Antes de pedir nada, revisar si ya existe un token guardado localmente.

Orden de ubicacion:

1. `.netgenius/local/eloqiant-n8n/secrets/n8n-api-key.txt`
2. `ai-skills/local/eloqiant-n8n/secrets/n8n-api-key.txt`

Si el token llega por chat:

- guardarlo en la primera ruta disponible
- no repetirlo completo en la respuesta
- usar siempre el mismo archivo para reemplazarlo si cambia

El estado local puede vivir en:

1. `.netgenius/local/eloqiant-n8n/state/`
2. `ai-skills/local/eloqiant-n8n/state/`

## Lo que el agente si puede hacer

Explicarlo en simple:

- ver workflows
- crear o ajustar workflows
- prender o apagar workflows
- ver ejecuciones recientes
- ver los nombres de las credenciales ya conectadas

## Lo que el agente no puede hacer solo

Explicarlo tambien en simple:

- conectar cuentas tipo Gmail, WhatsApp o Google por ti
- ver el contenido secreto de una credencial
- hacer debug manual paso por paso en la interfaz de n8n

## Bloqueo mas comun

Si falta una credencial, decirlo asi de simple:

- "Yo puedo dejarte el flujo armado, pero primero necesitas conectar esa cuenta en n8n."

## Cuando falta conectar n8n

Si no hay token local, pedirlo con este texto simple:

Para conectarlo necesito tu token de n8n.

1. entra a `https://n8n.eloqiant.com`
2. inicia sesion
3. ve a `Settings` -> `API`
4. crea una API key nueva
5. guardala
6. pegala aqui y yo sigo

Luego cerrar con:

- "Cuando me la pegues aqui, la guardo y ya te puedo mostrar, crear o apagar workflows."

Para el texto exacto extendido, ver [references/connect-tutorial.md](references/connect-tutorial.md).

## Cuando falta una credencial dentro de n8n

Usar este camino simple:

1. entrar a `https://n8n.eloqiant.com/credentials`
2. crear la credencial que falta
3. volver y decir el nombre exacto de esa credencial

Si ya hay credenciales disponibles, mostrarlas como lista corta.

Para el texto exacto extendido, ver [references/missing-credential.md](references/missing-credential.md).

## Flujo sugerido

1. revisar si n8n ya esta conectado
2. si no esta conectado, dar tutorial corto
3. si esta conectado, revisar si falta una credencial concreta
4. si falta, pedir que la conecten en la UI de n8n
5. si no falta, seguir con el workflow

## Caso guia

Si la persona dice "quiero automatizar WhatsApp y responder cotizaciones con n8n":

- no preguntar si usa WhatsApp Business manual o personal para desviar a una solucion basica
- no recomendar respuestas rapidas manuales
- mantener el camino de bot con n8n
- pedir solo el siguiente dato que desbloquea el flujo

Ejemplos de siguiente pregunta valida:

- "Ya tienes n8n conectado aqui o primero lo conectamos?"
- "Que datos usas para armar la cotizacion?"

## Cuando usar apoyo

- usar `automation-builder` si hay que pensar el flujo o construir el workflow
- usar `respuesta-simple` si hace falta bajar aun mas la complejidad

## Referencias

- Ver [references/connect-tutorial.md](references/connect-tutorial.md) para el tutorial exacto de conexion.
- Ver [references/missing-credential.md](references/missing-credential.md) para el mensaje cuando falta una credencial.
- Ver [references/capabilities.md](references/capabilities.md) para el limite simple de lo que el agente puede y no puede hacer.
- Ver [references/local-storage.md](references/local-storage.md) para saber donde guardar el token y el estado local.
