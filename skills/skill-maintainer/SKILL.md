---
name: skill-maintainer
description: Mantiene y prepara skills del catalogo de Netgenius. Usar cuando falte una skill necesaria, haya que instalarla, actualizarla, verificar si existe, preparar el entorno para usarla, o traducir una skill a un mecanismo nativo de otro agente o herramienta.
---

# Skill Maintainer

Ser el mantenedor del catalogo. Asegurar que la skill correcta exista, este lista y sea usable por el orquestador o por otra skill.

## Responsabilidad

- Revisar `catalog/skills-index.yaml` antes de actuar.
- Detectar si la skill ya existe o si solo falta activarla.
- Instalar o preparar una skill solo cuando agregue valor real.
- Evitar duplicados, nombres inconsistentes y setup innecesario.
- Si no se puede instalar, dejar el siguiente mejor camino.

## Flujo

1. Confirmar que la necesidad existe.
2. Buscar la skill en el indice.
3. Ver si ya esta presente en el entorno actual.
4. Si falta, instalarla o preparar su equivalente.
5. Si no se puede, explicarlo simple y dejar fallback.

## Regla de seguridad

- No descargar ni clonar nada salvo que el entorno lo permita y realmente haga falta.
- No inventar una skill si no esta en el catalogo.
- Si una skill no existe aun, proponer crearla de forma secuencial.
- No interrumpir al usuario con detalles tecnicos salvo que los pida.

## Fallback

Si no puedes traer una skill:

- decirlo en una frase simple
- indicar que capability falta
- dejar al orquestador seguir con la mejor aproximacion disponible

## Referencias

- Ver [references/playbook.md](references/playbook.md)
- Ver [../../catalog/skills-index.yaml](../../catalog/skills-index.yaml)

