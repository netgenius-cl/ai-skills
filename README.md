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
- usar este repo local como fuente principal si ya existe en el entorno
- si el repo no existe localmente, usar este mismo repositorio por enlace
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
- optimizar tokens en el razonamiento interno, no en la calidez visible para el usuario

## Estructura

- [catalog/](./catalog/README.md): indice y arquitectura escalable del catalogo
- [catalog/context-index.md](./catalog/context-index.md): indice corto para cargar primero en contexto
- [catalog/service-defaults.json](./catalog/service-defaults.json): instancias, URLs y rutas por defecto
- [catalog/model-guidance.md](./catalog/model-guidance.md): guia viva de modelos, modos y politica de refresco
- [skills/](./skills/): skills nativas de Codex
- [environments/antigravity/](./environments/antigravity/README.md): guia para Antigravity
- [environments/codex/](./environments/codex/README.md): guia para Codex
- [environments/claude-code/](./environments/claude-code/README.md): memoria y hooks para Claude Code
- [environments/cursor/](./environments/cursor/README.md): rules, AGENTS.md y background agents para Cursor
- [environments/cloud-no-skills/](./environments/cloud-no-skills/README.md): agentes en la nube sin skills persistentes

## Que hacer segun el entorno

### Codex

Usar la skill `netgenius` desde [skills/netgenius/](./skills/netgenius/SKILL.md).

### Antigravity

Usar [environments/antigravity/README.md](./environments/antigravity/README.md) y preferir `AGENTS.md`. Mantener `GEMINI.md` solo como compatibilidad si ese entorno o version todavia lo usa.

### Claude Code

Usar la version de `netgenius` para `CLAUDE.md` y opcionalmente hooks desde [environments/claude-code/](./environments/claude-code/README.md).

### Cursor

Usar la version de `netgenius` para `AGENTS.md`, Project Rules y opcionalmente background agents desde [environments/cursor/](./environments/cursor/README.md).

### Cloud sin skills

Usar la version informativa para agentes como Gemini desde [environments/cloud-no-skills/](./environments/cloud-no-skills/README.md).

## Reglas de autonomia local

- este repo debe poder funcionar sin depender de enlaces externos como fuente principal
- si hay una instruccion local y una remota, preferir la local
- cuando pidan persistencia, usar archivos persistentes del repo antes que prompts efimeros

## Regla de entrada

- mantener instalacion facil por enlace para cualquier agente
- mantener tambien uso local cuando el repo ya este clonado
- no crear dos catalogos distintos: el remoto y el local deben representar este mismo repo

## Instalacion local completa

Si el entorno ya tiene este repo, se puede materializar un catalogo persistente completo en `.netgenius/`.

Ese catalogo incluye:

- `skills/`
- `catalog/`
- `environments/`
- `local/`
- `README.md`
- `SETUP.md`
- `.gitignore`

Ademas, si existe el plugin local de Codex, el refresco debe dejarlo alineado con la misma fuente.

La instalacion o refresco local se hace con:

`npm run netgenius:install`

Validacion rapida:

`npm run netgenius:validate`

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

- `google-drive`: acceso a archivos de Google Drive sincronizados, montados o compartidos
- `eloqiant-n8n`: conexion simple entre Eloqiant y n8n para usuarios finales
- `automation-builder`: automatizaciones, workflows, webhooks y tecnologia como n8n
- `browser`: navegacion web segura, lectura de paginas, formularios, login y validacion antes de hacer clic
- `software-engineering`: codigo, bugs, integraciones y automatizacion tecnica
- `data-analysis`: analisis de datos y metricas
- `report-generation`: informes y resumentes ejecutivos
- `web-dashboard-builder`: dashboards web interactivos
- `critical-info-auditor`: revision de informacion critica

## Regla de orquestacion

El orquestador no debe adivinar.

Debe usar [catalog/skills-index.yaml](./catalog/skills-index.yaml) como mapa de decision:

Antes, si necesita una carga minima, puede leer [catalog/context-index.md](./catalog/context-index.md).

- primero detectar intencion
- luego elegir una skill principal
- sumar apoyos solo si hacen falta
- si hace falta una URL o instancia por defecto, leer `catalog/service-defaults.json`
- si faltan archivos o una skill, llamar a `skill-maintainer`
- si el pedido es de automatizacion y falta tecnologia, preguntar una sola cosa corta antes de enrutar
- si el pedido es de automatizacion y faltan integraciones especificas, aclararlas desde el orquestador
- si el pedido menciona Drive, rutas sincronizadas o enlaces de Drive, probar `google-drive` antes que otras skills
- si el pedido menciona navegador, browser, URL, formularios o una interfaz web, probar `browser` antes de saltar a codigo

## Modos y modelos

La guia viva esta en [catalog/model-guidance.md](./catalog/model-guidance.md).

La politica de vigencia esta en [catalog/update-policy.json](./catalog/update-policy.json).

Regla:

- `fast`: resolver rapido, poco overhead, preguntas cortas y cambios pequenos
- `plan`: pensar mas, aclarar riesgos y enrutar mejor cuando el trabajo es ambiguo o importante
- las recomendaciones de modelos cambian con el tiempo y deben refrescarse con fecha
