# ai-skills

Catalogo de Netgenius para varios entornos de agentes.

## Prompt minimo

`Lee https://github.com/netgenius-cl/ai-skills`

## Prompt recomendado

```text
Usa el README de https://github.com/netgenius-cl/ai-skills para configurar este entorno con `netgenius`.

Usa modo simple por defecto.

Cuando termines, responde solo en simple:
"Listo, tu agente ya quedo configurado para responder facil y claro."
Y si falta algo, dilo en una sola frase simple.
```

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

## Regla principal

- empezar por `netgenius`
- usar modo simple por defecto
- asumir que la persona no es tecnica
- usar `respuesta-simple` como apoyo si existe

## Estructura

- [skills/](./skills/): skills nativas de Codex
- [environments/codex/](./environments/codex/README.md): guia para Codex
- [environments/claude-code/](./environments/claude-code/README.md): memoria y hooks para Claude Code
- [environments/cursor/](./environments/cursor/README.md): rules, AGENTS.md y background agents para Cursor

## Que hacer segun el entorno

### Codex

Usar la skill `netgenius` desde [skills/netgenius/](./skills/netgenius/SKILL.md).

### Claude Code

Usar la version de `netgenius` para `CLAUDE.md` y opcionalmente hooks desde [environments/claude-code/](./environments/claude-code/README.md).

### Cursor

Usar la version de `netgenius` para `AGENTS.md`, Project Rules y opcionalmente background agents desde [environments/cursor/](./environments/cursor/README.md).

## Regla de cierre

Despues de aplicar la configuracion, el agente debe confirmarlo en lenguaje simple.

Frase recomendada:

`Listo, ya quedo configurado para responder facil y claro.`

## Skill principal

### netgenius

Es el orquestador principal del catalogo.

Hace esto por defecto:

- responde facil
- coordina otras capacidades
- intenta actualizarse cuando se lo piden
- mantiene una sola voz simple para la persona final

## Skill de apoyo

### respuesta-simple

Sirve para reforzar la capa de explicacion clara y amable cuando el usuario final necesita todavia menos complejidad.
