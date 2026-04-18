---
name: browser
description: Navegacion web cuidadosa para paginas, enlaces, formularios, login, pestanas, extraccion de informacion visible y validacion antes de hacer clic o enviar. Usar cuando Codex necesite moverse por una interfaz web sin cometer acciones torpes, irreversibles o fuera de contexto.
---

# Browser

Navegar la web con calma, contexto y disciplina.

## Objetivo

- entender donde esta parado el agente antes de actuar
- avanzar con pasos pequenos y verificables
- evitar clics, envios o cambios irreversibles por apuro
- extraer informacion visible sin mutar nada cuando solo hace falta leer

## Regla principal

Primero orientarse, despues actuar.

Antes de cualquier clic o escritura, confirmar:

- pagina o app actual
- cuenta, workspace o sesion activa
- objetivo exacto del paso
- efecto esperado del siguiente gesto

## Flujo

1. identificar el objetivo real
2. leer URL, titulo, encabezado y elementos visibles clave
3. detectar si la tarea es de solo lectura o si requiere mutacion
4. elegir el paso mas pequeno y seguro
5. despues de cada navegacion, verificar que la pagina resultante coincide con lo esperado
6. antes de enviar o confirmar algo sensible, hacer preflight final

## Preflight para acciones sensibles

Aplicar este chequeo antes de:

- enviar formularios
- publicar
- borrar
- pagar
- descargar ejecutables
- subir archivos
- cambiar permisos
- autorizar accesos
- confirmar acciones con impacto real

Checklist:

- es la cuenta correcta
- es el registro, archivo o persona correcta
- el boton correcto esta claro
- la accion era parte del pedido del usuario
- el impacto es reversible o aceptado

Si una de esas respuestas no esta clara, frenar y reorientar.

## Reglas de navegacion

- preferir URLs directas o rutas claras cuando existan
- no asumir que un boton hace lo que parece: validar texto, contexto y pagina
- no encadenar varios clics a ciegas
- no abrir pestanas innecesarias si una sola basta
- si aparece una pantalla inesperada, detenerse y describir el estado antes de seguir
- si solo hace falta leer, no iniciar sesion ni tocar configuraciones
- si una accion cambia datos reales, no improvisar

## Formularios

- mapear primero que campos existen y cuales son obligatorios
- verificar etiquetas, placeholders y validaciones visibles antes de escribir
- completar con valores exactos, no aproximados
- revisar el resumen final antes de enviar
- si el formulario mezcla varios pasos, confirmar el resultado de cada paso antes del siguiente

## Extraccion de informacion

- preferir contenido visible y verificable
- citar URL, titulo o seccion cuando ayude a evitar confusion
- si hay tablas o listas largas, resumir sin perder datos clave
- distinguir claramente entre lo visto y lo inferido

## Cuando parar

- si la cuenta o workspace no estan claros
- si la pagina no coincide con el objetivo
- si hay dos acciones parecidas con consecuencias distintas
- si el siguiente clic puede enviar, borrar, pagar o publicar sin vuelta facil
- si el sitio pide permisos, extensiones o descargas inesperadas

## Handoffs

- usar `critical-info-auditor` si la decision en pantalla es sensible o de alto riesgo
- usar `software-engineering` si el usuario ya no quiere navegar manualmente y pide automatizacion o integracion tecnica

## Referencias

- Ver [references/navigation-checklist.md](references/navigation-checklist.md)
