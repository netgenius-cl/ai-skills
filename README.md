# ai-skills

Catalogo publico de skills para Codex hecho por Netgenius.

## Empieza por aqui

Si no sabes cual skill elegir, instala esta:

```text
Usa $skill-installer e instala:
https://github.com/netgenius-cl/ai-skills/tree/main/skills/netgenius
```

Luego, si no aparece de inmediato, reinicia Codex.

## Como usar este catalogo

1. Abre este repositorio.
2. Elige una skill.
3. Copia su bloque de instalacion.
4. Pegalo en Codex.

## Skill principal

### Agente Netgenius

Es la puerta de entrada del catalogo. Habla simple, coordina especialistas detras de escena, puede ayudarte a crear nuevas skills una por una e intenta actualizarse cuando se lo pides.

Instalar:

```text
Usa $skill-installer e instala:
https://github.com/netgenius-cl/ai-skills/tree/main/skills/netgenius
```

Usar:

```text
Usa $netgenius para ayudarme sin tecnicismos y coordinar lo necesario.
```

Para crear skills:

```text
Usa $netgenius para crear una nueva skill paso a paso y dejarla lista para publicar.
```

Para probarla rapido:

```text
Usa $netgenius para actuar como un asistente virtual muy inteligente, claro y sin tecnicismos.
```

Para pedirle que se actualice:

```text
Usa $netgenius para intentar actualizar esta skill desde su fuente principal y explicarme el resultado simple.
```

## Skills de apoyo

### Respuesta Simple

Habla claro, amable y sin tecnicismos para usuarios no tecnicos. Sirve como capa de simplificacion para explicar, pedir datos y resumir trabajo complejo de forma facil de entender.

Instalar:

```text
Usa $skill-installer e instala:
https://github.com/netgenius-cl/ai-skills/tree/main/skills/respuesta-simple
```

Usar:

```text
Usa $respuesta-simple para responderle a esta persona de la forma mas simple posible.
```

## Publicar nuevas skills

Cada skill vive dentro de `skills/<nombre-skill>/` y debe incluir al menos un archivo `SKILL.md`.

## Compatibilidad

La skill principal esta escrita para funcionar de forma portable: si el agente tiene funciones avanzadas las aprovecha, y si no las tiene sigue ayudando en modo simple. La idea es que sirva bien en Codex, Claude Code y entornos parecidos sin depender por completo de una sola plataforma.
