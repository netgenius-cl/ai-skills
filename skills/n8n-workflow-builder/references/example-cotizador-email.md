# Example Cotizador Email

Workflow de referencia completo para cotizar por email con scraping, Sheets, IA y respuesta por Gmail.

## Vista general

Nodos documentados:

- `c1` Gmail Trigger
- `c2` HTTP Request
- `c2b` HTML Extract
- `c3` Google Sheets read
- `c4` Code prompt
- `c5` chainLlm
- `c6` DeepSeek LLM
- `c9` Code parser
- `c7` Gmail reply
- `c8` Google Sheets append
- `wh1` y `wh2` webhook de prueba

## Flujo

```text
c1 Gmail Trigger
  -> c2 HTTP GET
    -> c2b HTML Extract
      -> c3 Google Sheets read
        -> c4 Code
          -> c5 chainLlm <- c6 DeepSeek LLM (ai_languageModel)
            -> c9 Code parser
              -> c7 Gmail reply
                -> c8 Google Sheets append

[desconectado]
wh1 Webhook
  -> wh2 respondToWebhook
```

## c1 Gmail Trigger

- usa `gmailOAuth2`
- campos utiles: `id`, `from`, `subject`, `text`, `snippet`

```json
{
  "id": "c1",
  "name": "Gmail: nuevo correo",
  "type": "n8n-nodes-base.gmailTrigger",
  "typeVersion": 1.2,
  "parameters": {
    "pollTimes": { "item": [{ "mode": "everyMinute" }] },
    "filters": {}
  }
}
```

## c2 HTTP Request

- GET publico
- sin credentials
- devuelve HTML completo

```json
{
  "id": "c2",
  "name": "GET precios eloqiant.com",
  "type": "n8n-nodes-base.httpRequest",
  "typeVersion": 4.2,
  "parameters": { "url": "https://eloqiant.com", "options": {} }
}
```

## c2b HTML Extract

- `cssSelector: "body"`
- salida `pricing_text`

```json
{
  "id": "c2b",
  "name": "Extraer texto precios",
  "type": "n8n-nodes-base.htmlExtract",
  "typeVersion": 1,
  "parameters": {
    "extractionValues": {
      "values": [{ "key": "pricing_text", "cssSelector": "body" }]
    },
    "options": {}
  }
}
```

## c3 Google Sheets read

- `googleSheets` requiere `googleSheetsOAuth2Api`
- `mode: "url"` acepta la URL completa
- `mode: "id"` requiere solo el ID

```json
{
  "id": "c3",
  "name": "Leer informe de ventas",
  "type": "n8n-nodes-base.googleSheets",
  "typeVersion": 4.5
}
```

## c4 Code prompt

- usar `try/catch` para nodos opcionales
- pasar metadata hacia abajo
- truncar `pricing_text` si es muy largo

```js
const email = $('Gmail: nuevo correo').first().json;
const pricingText = ($('Extraer texto precios').first().json.pricing_text || '')
  .replace(/\s+/g, ' ').slice(0, 3000);

let salesData = '(no disponible)';
try {
  const rows = $('Leer informe de ventas').all();
  if (rows.length > 0) {
    salesData = rows.map(r => Object.values(r.json).join(' | ')).join('\n').slice(0, 2000);
  }
} catch (e) {}

return [{
  json: {
    prompt: `...${pricingText}...${salesData}...`,
    replyTo: email.from,
    subject: 'Cotizacion - ' + (email.subject || 'Su consulta'),
    fecha: new Date().toISOString().split('T')[0],
    mesHoja: new Date().toISOString().slice(0, 7)
  }
}];
```

## c5 y c6 chainLlm + DeepSeek

- `chainLlm` no lleva credentials
- el sub-nodo LLM se conecta por `ai_languageModel`
- la salida de `chainLlm` es `text`

```json
{
  "id": "c5",
  "name": "Generar cotizacion con IA",
  "type": "@n8n/n8n-nodes-langchain.chainLlm",
  "typeVersion": 1.5,
  "parameters": { "promptType": "define", "text": "={{ $json.prompt }}" }
}
```

```json
{
  "id": "c6",
  "name": "DeepSeek LLM",
  "type": "@n8n/n8n-nodes-langchain.lmChatDeepSeek",
  "typeVersion": 1
}
```

```json
{
  "connections": {
    "DeepSeek LLM": {
      "ai_languageModel": [[{ "node": "Generar cotizacion con IA", "type": "ai_languageModel", "index": 0 }]]
    }
  }
}
```

## c9 Code parser

- convierte markdown a HTML
- extrae precio con regex
- extrae cliente desde `from`

```js
const raw = $('Generar cotizacion con IA').first().json.text || '';
const email = $('Gmail: nuevo correo').first().json;
const prep = $('Preparar prompt').first().json;

function mdToHtml(md) {
  return md
    .replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>')
    .replace(/\*(.+?)\*/g, '<em>$1</em>')
    .replace(/^---+$/gm, '<hr>')
    .replace(/^[*-]\s+(.+)$/gm, '<li>$1</li>')
    .replace(/(<li>.*<\/li>\n?)+/g, m => '<ul>' + m + '</ul>')
    .split(/\n{2,}/)
    .map(b => {
      b = b.trim();
      if (!b || b.startsWith('<ul>') || b.startsWith('<hr>')) return b;
      return '<p>' + b.replace(/\n/g, '<br>') + '</p>';
    })
    .join('\n');
}

const mensaje = mdToHtml(raw);
const precioMatch =
  raw.match(/(?:Total|Precio|Subtotal)[^\n]*?\$?([\d.,$]{3,}(?:\s*CLP|\s*USD)?)/i) ||
  raw.match(/\$([\d.,]+(?:\s*CLP|\s*USD)?)/i);
const precio = precioMatch ? precioMatch[0].trim() : '(ver cotizacion)';

const fromMatch = (email.from || '').match(/^"?([^"<]+)"?\s*</);
const cliente = fromMatch ? fromMatch[1].trim() : (email.from || '(desconocido)');

return [{
  json: {
    mensaje,
    cliente,
    email_destino: email.from || '',
    asunto: prep.subject || 'Cotizacion',
    precio,
    fecha: prep.fecha,
    mesHoja: prep.mesHoja
  }
}];
```

## c7 Gmail reply

- `sendAsHtml: true` es obligatorio
- leer `messageId` desde Gmail Trigger
- leer `mensaje` desde el parser

```json
{
  "id": "c7",
  "name": "Responder por Gmail",
  "type": "n8n-nodes-base.gmail",
  "typeVersion": 2.2,
  "parameters": {
    "operation": "reply",
    "messageId": "={{ $('Gmail: nuevo correo').first().json.id }}",
    "message": "={{ $('Parsear respuesta IA').first().json.mensaje }}",
    "options": { "sendAsHtml": true }
  }
}
```

## c8 Google Sheets append

- `mappingMode: defineBelow`
- mapear columnas por nombre, no por posicion

```json
{
  "id": "c8",
  "name": "Guardar registro cotizacion",
  "type": "n8n-nodes-base.googleSheets",
  "typeVersion": 4.5,
  "parameters": {
    "operation": "append",
    "columns": {
      "mappingMode": "defineBelow"
    }
  }
}
```

## wh1 y wh2 webhook de prueba

- patron desconectado del flujo principal
- usar `respondToWebhook`
- posicionarlos con `Y >= 600` para separacion visual

```json
{
  "id": "wh1",
  "name": "TEST: Recibir POST",
  "type": "n8n-nodes-base.webhook",
  "typeVersion": 2
}
```

```json
{
  "id": "wh2",
  "name": "TEST: Responder webhook",
  "type": "n8n-nodes-base.respondToWebhook",
  "typeVersion": 1.1
}
```
