# AI And Scraping

Usar esta referencia como base cuando el workflow incluya IA, LangChain o scraping web.

## Nodos AI y LangChain disponibles

En esta instancia, `@n8n/n8n-nodes-langchain` esta disponible dentro de n8n.

No confiar en `/api/v1/node-types` para descubrirlos en esta version, porque puede devolver `404`.

### Chains

- `@n8n/n8n-nodes-langchain.chainLlm` con `typeVersion: 1.5`
- `@n8n/n8n-nodes-langchain.chainRetrievalQa`
- `@n8n/n8n-nodes-langchain.chainSummarization`

### LLMs

- `@n8n/n8n-nodes-langchain.lmChatDeepSeek` con `typeVersion: 1`
- `@n8n/n8n-nodes-langchain.lmChatOpenAi`
- `@n8n/n8n-nodes-langchain.lmChatGoogleGemini`

### Agents

- `@n8n/n8n-nodes-langchain.agent`

## Patron de conexion AI

El sub-nodo LLM se conecta al chain con `ai_languageModel`, no con `main`.

```json
{
  "connections": {
    "DeepSeek LLM": {
      "ai_languageModel": [
        [
          { "node": "Mi Chain", "type": "ai_languageModel", "index": 0 }
        ]
      ]
    },
    "Mi Chain": {
      "main": [
        [
          { "node": "Siguiente nodo", "type": "main", "index": 0 }
        ]
      ]
    }
  }
}
```

## Regla del chain

- `chainLlm` no lleva `credentials`
- las `credentials` van solo en el sub-nodo LLM
- la salida confiable de `chainLlm` es `text`
- usar siempre algo como `$('Mi Chain').first().json.text`

## HTML para respuestas de agentes

Si un agente IA genera contenido para email:

- pedir HTML valido, no texto plano
- no pedir markdown ni bloques de codigo
- en Gmail habilitar `sendAsHtml`

## JSON estructurado y DeepSeek

- no confiar en que DeepSeek devuelva JSON perfecto de forma consistente
- no usar salida JSON del LLM directamente en campos de n8n
- preferir este patron: `chainLlm -> Code -> Gmail/Sheets`
- dejar que el LLM responda libremente y luego parsear en un nodo Code

Prompt sugerido:

```text
Responde UNICAMENTE con HTML valido listo para insertar en un email.
No incluyas bloques de codigo markdown. Solo el HTML directo.
```

Ejemplo en Gmail:

```json
{
  "parameters": {
    "operation": "reply",
    "options": { "sendAsHtml": true }
  }
}
```

## Markdown a HTML y extraccion

Patron base para convertir markdown y extraer precio en un nodo Code:

```js
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

const precioMatch =
  raw.match(/(?:Total|Precio|Subtotal)[^\n]*?\$?([\d.,$]{3,}(?:\s*CLP|\s*USD)?)/i) ||
  raw.match(/\$([\d.,]+(?:\s*CLP|\s*USD)?)/i);
```

## Scraping web

Para scraping simple web usar este patron:

- `n8n-nodes-base.httpRequest`
- `n8n-nodes-base.htmlExtract`

Orden recomendado:

1. `httpRequest` para traer la URL
2. `htmlExtract` con `cssSelector: "body"`
3. `htmlExtract` con `returnValue: "text"`

## Recordatorio

- usar estos ejemplos como base para crear JSON de nodos
- no inventar tipos de conexion AI
- no mover credentials al chain si pertenecen al LLM
