# Context Index

Indice corto para cargar primero en contexto.

No reemplaza al catalogo completo.
Sirve para orientarse rapido y abrir solo el archivo minimo necesario.

## Comportamiento base

- responder simple por defecto
- asumir usuario no tecnico salvo evidencia clara
- mantener una sola voz calma y clara
- usar una skill principal y solo apoyos minimos
- si falta una capacidad o archivo, usar `skill-maintainer`

## Ruta rapida de decision

1. identificar la intencion principal
2. elegir la skill mas pequena que resuelva el pedido
3. abrir mas detalle solo si hace falta

## Cuando abrir cada archivo

- para ruteo fino por palabras gatillo y apoyos: `catalog/skills-index.yaml`
- para modos o recomendacion de modelos: `catalog/model-guidance.md`
- para vigencia o mantenimiento: `catalog/update-policy.json`
- para instrucciones completas de una skill: `skills/<nombre>/SKILL.md`

## Mapa corto de skills

- `netgenius`: entrada principal, simplifica y coordina
- `respuesta-simple`: baja complejidad al explicarle al usuario
- `skill-maintainer`: instala, actualiza o prepara skills faltantes
- `google-drive`: archivos de Drive, rutas sincronizadas y enlaces de Drive
- `eloqiant-n8n`: conexion simple de Eloqiant con n8n y ruta por defecto cuando se menciona n8n
- `automation-builder`: automatizaciones, workflows, webhooks y eleccion de tecnologia como n8n
- `browser`: web, URL, login, formularios y lectura cuidadosa de interfaces
- `community-manager`: redes sociales, posts, captions, replies, tono y emojis
- `software-engineering`: codigo, bugs, APIs e integraciones tecnicas
- `data-analysis`: metricas, datasets y analisis
- `report-generation`: informes y resumentes accionables
- `web-dashboard-builder`: dashboards y visualizaciones web
- `critical-info-auditor`: cifras sensibles, trazabilidad y decisiones criticas

## Gatillos utiles

- Drive o carpeta sincronizada: ir a `google-drive`
- n8n o Eloqiant + n8n: ir a `eloqiant-n8n`
- automatizacion, workflow, Make, Zapier o webhook: ir a `automation-builder`
- navegador, URL, login o formulario: ir a `browser`
- redes sociales, Instagram, LinkedIn, TikTok, caption o community manager: ir a `community-manager`
- codigo, bug, API o script: ir a `software-engineering`
- metricas, csv, sql o datos: ir a `data-analysis`
- informe o resumen ejecutivo: ir a `report-generation`
- dashboard o panel: ir a `web-dashboard-builder`
- auditoria o informacion sensible: ir a `critical-info-auditor`

## Reglas de duda

- si el pedido parece de codigo y falta stack o alcance, hacer una sola pregunta corta
- si el pedido es de automatizacion y falta tecnologia, preguntar una sola cosa corta
- si el pedido es de automatizacion y faltan integraciones clave, el orquestador debe aclararlas antes de bajar al detalle
- si el trabajo mezcla varias areas, elegir una principal y sumar uno o dos apoyos maximo
- si el pedido es local, estable y simple, no abrir archivos extra

## Secuencia recomendada de carga

1. `catalog/context-index.md`
2. `catalog/skills-index.yaml` solo si hace falta detalle de ruteo
3. `catalog/model-guidance.md` solo si hay decision de modo o modelo
4. `skills/<nombre>/SKILL.md` solo para la skill elegida
