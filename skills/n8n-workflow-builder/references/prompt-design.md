# Prompt Design

Usar esta referencia antes de escribir prompts para nodos `chainLlm` o `agent`.

## Preguntas obligatorias

### 1. Datos reales o de ejemplo

```text
El agente debe usar datos reales del sistema?
O puede inventar datos de ejemplo para responder?
```

- si son reales, el prompt debe decir que no invente precios, productos ni datos faltantes
- si son de ejemplo, se puede permitir una respuesta mas libre para demo

### 2. Tono y estructura

```text
La respuesta es un email formal, un chat, un resumen o una lista?
Debe incluir precios, validez, firma o desglose?
```

### 3. Lo que no debe hacer

Siempre incluir restricciones claras:

```text
- NO inventes precios que no esten en la tabla
- NO incluyas servicios que no existan en el catalogo
- NO uses markdown si la salida va a HTML
- NO respondas en ingles
```

## Plantilla de cotizador

```text
Eres un asesor de ventas de {empresa}. Responde el correo con una cotizacion profesional.

## DATOS REALES DEL SISTEMA
### Precios vigentes:
{pricingText}

### Historial de ventas:
{salesData}

## CORREO A RESPONDER
De: {from}
Asunto: {subject}
Mensaje: {body}

## REGLAS
- Usa SOLO precios de la tabla anterior
- Si el producto no esta en la tabla, indica que se cotizara por separado
- Validez: 30 dias
- Idioma: espanol
- Formato: markdown
```
