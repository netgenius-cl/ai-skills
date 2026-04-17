# Netgenius Setup

Lee este archivo para configurar el entorno actual.

## Objetivo

Dejar este entorno listo para responder facil, claro y breve a usuarios finales no tecnicos.

## Reglas globales

- No clonar ni descargar este repositorio con `git` salvo que la persona lo pida.
- No crear copias locales del catalogo por defecto.
- Leer solo los archivos necesarios de este repositorio.
- Crear solo los archivos nativos del entorno actual.
- No explicar pasos internos salvo que la persona lo pida.
- No listar archivos, carpetas o rutas en la respuesta final salvo que la persona lo pida.
- Si ejecutas comandos, resumir el resultado en una frase muy corta.

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

### Claude Code

Hacer esto:

1. Crear o actualizar `CLAUDE.md` usando `environments/claude-code/CLAUDE.md`.
2. Crear o actualizar `.claude/settings.json` solo si hace falta hooks.
3. No clonar este repo.

### Cursor

Hacer esto:

1. Crear o actualizar `AGENTS.md` usando `environments/cursor/AGENTS.md`.
2. Crear o actualizar `.cursor/rules/netgenius.mdc` si el entorno usa rules.
3. Crear o actualizar `environment.json` solo si realmente se necesita background agents.
4. No clonar este repo.
5. No crear carpetas tipo `.netgenius` por defecto.

### Otros agentes

1. Detectar el mecanismo nativo de instrucciones persistentes.
2. Traducir `netgenius` a ese formato.
3. Mantener modo simple por defecto.
4. No clonar este repo salvo que la persona lo pida.

## Fuente por entorno

- Codex: `environments/codex/README.md`
- Claude Code: `environments/claude-code/README.md`
- Cursor: `environments/cursor/README.md`

## Respuesta final

Si ya quedo listo, responder solo:

`Listo, ya quedo configurado para responder facil y claro.`

Si falta algo, responder solo:

`Casi listo. Solo falta _____.`

