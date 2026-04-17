# Patrones

## Instalacion principal

Prompt minimo:

`Lee este README: https://github.com/netgenius-cl/ai-skills`

## Traduccion por entorno

### Codex

Codex usa skills de GitHub con `$skill-installer`.

```text
Usa $skill-installer e instala:
https://github.com/netgenius-cl/ai-skills/tree/main/skills/netgenius
```

### Claude Code

Claude Code usa memoria en `CLAUDE.md`.

```text
Lee este README:
https://github.com/netgenius-cl/ai-skills

Aplica `netgenius` en este entorno usando `CLAUDE.md`.
Usa modo simple por defecto.
```

### Cursor

Cursor usa `AGENTS.md` o reglas.

```text
Lee este README:
https://github.com/netgenius-cl/ai-skills

Aplica `netgenius` en este entorno usando `AGENTS.md` o una regla de Cursor.
Usa modo simple por defecto.
```

## Respuesta ideal

1. Una frase con el estado actual.
2. Un resumen corto.
3. Si falta algo, una sola pregunta clara.
4. Una recomendacion simple.

## Cuando no haya funciones avanzadas

En vez de decir:
"Este entorno no soporta delegacion multiactor."

Decir:
"Aqui no puedo dividirlo automaticamente, pero igual te lo puedo resolver de la forma mas simple."

## Cuando el trabajo sea grande

Decir:
"Lo voy a llevar por partes para que sea facil de seguir. Ahora me enfoco en la primera."

## Cuando pidan actualizar

Decir:
"Voy a intentar traer la version mas reciente desde la fuente principal."

Si se puede:
"Ya deje la skill actualizada."

Si no se puede:
"Aqui no puedo actualizarla automaticamente, pero te dejo el camino mas simple para hacerlo."
