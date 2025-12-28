# Configuração do Webhook - Residencial Vera

## 📱 Número de WhatsApp Configurado
**+55 11 91094-0045**

## 🔗 Configuração do Webhook

### Localização no Código
O webhook está configurado no arquivo `index.html` na linha aproximada **2118**.

### URL do Webhook
Procure por esta linha no código:
```javascript
const webhookUrl = 'SUA_URL_WEBHOOK_AQUI'; // SUBSTITUA pela URL do webhook
```

**⚠️ IMPORTANTE**: Substitua `'SUA_URL_WEBHOOK_AQUI'` pela URL real do seu webhook.

### Exemplos de URLs de Webhook:
- **Make.com**: `https://hook.us1.make.com/seu-webhook-id`
- **Zapier**: `https://hooks.zapier.com/hooks/catch/seu-id/`
- **n8n**: `https://seu-n8n.app/webhook/seu-id`
- **Webhook.site (teste)**: `https://webhook.site/seu-token`

---

## 📦 Formato dos Dados Enviados

### Estrutura JSON

```json
{
  "perguntas": {
    "Quantas pessoas?": "2",
    "Data de entrada?": "2025-01-15",
    "Quantos dias?": "7"
  },
  "plataforma": "META",
  "fonte": "Residencial Vera - Landing Page",
  "quando": "2025-12-28T15:30:45.123Z",
  "timestamp": "28/12/2025, 12:30:45"
}
```

### Descrição dos Campos

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `perguntas` | Object | Contém todas as perguntas e respostas do formulário |
| `perguntas["Quantas pessoas?"]` | String | Número de pessoas (1-6+) |
| `perguntas["Data de entrada?"]` | String | Data no formato YYYY-MM-DD |
| `perguntas["Quantos dias?"]` | String | Número de dias da estadia |
| `plataforma` | String | Sempre "META" |
| `fonte` | String | Sempre "Residencial Vera - Landing Page" |
| `quando` | String | Timestamp ISO 8601 (UTC) |
| `timestamp` | String | Timestamp formatado em PT-BR (São Paulo) |

---

## 🛠️ Como Configurar

### Opção 1: Make.com (Recomendado)

1. Acesse [Make.com](https://www.make.com)
2. Crie um novo cenário
3. Adicione o módulo "Webhooks" → "Custom webhook"
4. Copie a URL gerada
5. Cole no código HTML substituindo `'SUA_URL_WEBHOOK_AQUI'`
6. Configure as ações desejadas (enviar email, salvar em planilha, etc.)

### Opção 2: Zapier

1. Acesse [Zapier](https://zapier.com)
2. Crie um novo Zap
3. Escolha "Webhooks by Zapier" como trigger
4. Selecione "Catch Hook"
5. Copie a URL do webhook
6. Cole no código HTML
7. Configure as ações subsequentes

### Opção 3: Google Sheets (Script)

1. Crie uma planilha no Google Sheets
2. Vá em **Extensões** → **Apps Script**
3. Cole o código abaixo:

```javascript
function doPost(e) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  const data = JSON.parse(e.postData.contents);
  
  sheet.appendRow([
    data.timestamp,
    data.perguntas["Quantas pessoas?"],
    data.perguntas["Data de entrada?"],
    data.perguntas["Quantos dias?"],
    data.plataforma,
    data.fonte
  ]);
  
  return ContentService.createTextOutput(JSON.stringify({status: 'success'}))
    .setMimeType(ContentService.MimeType.JSON);
}
```

4. **Implantar** → **Nova implantação**
5. Tipo: **Aplicativo da Web**
6. Executar como: **Eu**
7. Quem tem acesso: **Qualquer pessoa**
8. Copie a URL gerada
9. Cole no código HTML

---

## 🧪 Testar o Webhook

### 1. Webhook.site (Teste Rápido)

1. Acesse https://webhook.site
2. Copie a URL única gerada
3. Cole no código HTML temporariamente
4. Faça um teste no formulário
5. Volte ao Webhook.site para ver os dados recebidos

### 2. Teste Local com console.log

O código já inclui:
```javascript
console.log('Dados enviados para webhook:', webhookData);
```

Abra o console do navegador (F12) para ver os dados que seriam enviados.

---

## 🔒 Modo CORS

### Configuração Atual
```javascript
mode: 'no-cors' // Use 'cors' se o servidor suportar
```

**`no-cors`**: Não verifica permissões CORS, mas não retorna resposta.
**`cors`**: Requer que o servidor permita requisições do domínio da página.

### Se o webhook não funcionar:
1. Verifique se a URL está correta
2. Teste com Webhook.site primeiro
3. Mude para `mode: 'cors'` se o servidor suportar
4. Verifique o console do navegador para erros

---

## 📊 Exemplo de Integração Completa

### Make.com → Google Sheets

1. **Webhook Trigger**: Recebe os dados
2. **Google Sheets Module**: 
   - Adicionar linha
   - Planilha: "Leads Residencial Vera"
   - Colunas: Data/Hora | Pessoas | Check-in | Dias | Plataforma | Fonte

### Make.com → Email

1. **Webhook Trigger**: Recebe os dados
2. **Gmail Module**:
   - Para: seuemail@exemplo.com
   - Assunto: "Nova Reserva - Residencial Vera"
   - Corpo: Template com os dados

---

## 🆘 Troubleshooting

### Webhook não está recebendo dados?

✅ Verifique se substituiu `'SUA_URL_WEBHOOK_AQUI'`
✅ Certifique-se que a URL começa com `https://`
✅ Teste com Webhook.site primeiro
✅ Abra o console (F12) e procure por erros
✅ Verifique se o webhook está "ativo" na plataforma

### Dados não estão completos?

✅ Verifique se todos os campos do formulário estão preenchidos
✅ Olhe o console.log para ver exatamente o que está sendo enviado
✅ Verifique o formato esperado pelo seu sistema

---

## 📞 Contatos

**WhatsApp**: +55 11 91094-0045  
**Página**: Residencial Vera - Landing Page  
**Plataforma**: META

---

## 🔄 Atualizações Futuras

Para adicionar mais campos ao formulário:

1. Adicione o campo HTML no formulário
2. Capture o valor no JavaScript
3. Adicione ao objeto `webhookData.perguntas`
4. Atualize a documentação do webhook

Exemplo:
```javascript
const nomedoPessoa = document.getElementById('nome').value;

const webhookData = {
    perguntas: {
        "Nome": nome,
        "Quantas pessoas?": pessoas,
        // ... outros campos
    },
    // ...
};
```
