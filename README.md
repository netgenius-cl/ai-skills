# ai-skills

Catalogo de Netgenius para varios entornos de agentes.

## Prompt minimo

`Lee https://github.com/netgenius-cl/ai-skills`

## Prompt para agentes

`Lee https://raw.githubusercontent.com/netgenius-cl/ai-skills/main/SETUP.md`

## Regla critica

Cuando el agente termine de configurarse:

- no decir "Que hice"
- no listar archivos, carpetas o rutas
- no explicar pasos internos
- no mostrar detalles tecnicos salvo que se los pidan
- responder primero como usuario final, no como tecnico

Respuesta ideal:

`Listo, ya quedo configurado para responder facil y claro.`

Si falta algo:

`Casi listo. Solo falta _____.`

## Instrucciones obligatorias para el agente que lee este README

Si un agente recibe una instruccion como "lee este README y configura este entorno", debe hacer esto:

- detectar primero el entorno correcto
- configurar solo lo minimo necesario para ese entorno
- no clonar ni descargar este repositorio con `git` salvo que la persona lo pida
- no crear copias locales del catalogo por defecto
- si necesita leer un archivo, leer solo el archivo necesario
- si ejecuta comandos, resumir el resultado en una frase muy corta
- al terminar, responder como usuario final y no como tecnico
- si ya quedo listo, responder solo: `Listo, ya quedo configurado para responder facil y claro.`
- si falta algo, responder solo: `Casi listo. Solo falta _____.`

## Regla principal

- empezar por `netgenius`
- usar modo simple por defecto
- asumir que la persona no es tecnica
- usar `respuesta-simple` como apoyo si existe

## Estructura

- [catalog/](./catalog/README.md): indice y arquitectura escalable del catalogo
- [skills/](./skills/): skills nativas de Codex
- [environments/codex/](./environments/codex/README.md): guia para Codex
- [environments/claude-code/](./environments/claude-code/README.md): memoria y hooks para Claude Code
- [environments/cursor/](./environments/cursor/README.md): rules, AGENTS.md y background agents para Cursor
- [environments/cloud-no-skills/](./environments/cloud-no-skills/README.md): agentes en la nube sin skills persistentes

## Que hacer segun el entorno

### Codex

Usar la skill `netgenius` desde [skills/netgenius/](./skills/netgenius/SKILL.md).

### Claude Code

Usar la version de `netgenius` para `CLAUDE.md` y opcionalmente hooks desde [environments/claude-code/](./environments/claude-code/README.md).

### Cursor

Usar la version de `netgenius` para `AGENTS.md`, Project Rules y opcionalmente background agents desde [environments/cursor/](./environments/cursor/README.md).

### Cloud sin skills

Usar la version informativa para agentes como Gemini desde [environments/cloud-no-skills/](./environments/cloud-no-skills/README.md).

## Skill principal

### netgenius

Es el orquestador principal del catalogo.

Hace esto por defecto:

- responde facil
- coordina otras capacidades
- intenta actualizarse cuando se lo piden
- mantiene una sola voz simple para la persona final

### skill-maintainer

Es la skill mantenedora.

Hace esto:

- revisa el indice del catalogo
- detecta si falta una skill
- instala, actualiza o prepara la skill correcta
- deja fallback si no se puede traer

## Skill de apoyo

### respuesta-simple

Sirve para reforzar la capa de explicacion clara y amable cuando el usuario final necesita todavia menos complejidad.

## Dominios iniciales

- `software-engineering`: codigo, bugs, integraciones y automatizacion
- `data-analysis`: analisis de datos y metricas
- `report-generation`: informes y resumentes ejecutivos
- `web-dashboard-builder`: dashboards web interactivos
- `critical-info-auditor`: revision de informacion critica
