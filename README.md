# 🏖️ Residencial Vera - Landing Page

Landing page para aluguel de apartamentos em Cachoeira do Bom Jesus, Florianópolis/SC.

## 📋 Características

- ✅ **Bilíngue**: Português e Espanhol
- ✅ **Formulário Multi-Step**: 3 etapas com navegação automática
- ✅ **Webhook Integration**: Envio de leads para Make.com
- ✅ **WhatsApp Integration**: Redirecionamento direto com mensagem pré-formatada
- ✅ **Responsivo**: Otimizado para mobile e desktop
- ✅ **Galerias de Fotos**: 3 apartamentos + praia
- ✅ **Google Maps**: Localização integrada
- ✅ **Seleção de Data**: Botões rápidos + calendário
- ✅ **Design Minimalista**: Modal compacto e limpo

## 🏗️ Estrutura

```
.
├── index.html                 # Página principal
├── webhook-config.md          # Documentação do webhook
├── copy-residencial-vera.txt  # Copy marketing
├── 201 2 quartos - sacada/    # Fotos apartamento 201
├── 203 - churrasqueira - sacada/ # Fotos apartamento 203
├── residencial vera 104 3 quartos - sacada - churrasqueira/ # Fotos apartamento 104
├── fotos da praia/            # Fotos da praia
├── canasvierias fotso.jpg     # Foto Canasvieiras
├── pronto de florianopolis.webp # Background hero
└── video da cachoeira.mp4     # Vídeo hero
```

## 🚀 Tecnologias

- **HTML5**
- **CSS3** (Gradientes, Animações, Flexbox, Grid)
- **JavaScript ES6+** (Fetch API, Async/Await)
- **Make.com** (Webhook automation)
- **WhatsApp API** (wa.me)

## 📱 Formulário

### Campos
1. **Pessoas**: 1, 2, 3, 4, 5, 6+ (botões)
2. **Data de Entrada**: Botões rápidos + calendário
3. **Dias**: 1-10, 10+ (botões)

### Navegação Automática
- Ao selecionar pessoas → avança para data (300ms)
- Ao selecionar data → avança para dias (500ms)
- Ao selecionar dias → envia formulário (300ms)

## 🔗 Webhook

**URL**: `https://hook.us2.make.com/bclkqerruqkkjcfaqnh27gqj6bgrejxx`

**Dados enviados**:
```json
{
  "quantas_pessoas": "2",
  "data_entrada": "2025-01-15",
  "quantos_dias": "7",
  "idioma": "Português",
  "plataforma": "META",
  "fonte": "Residencial Vera - Landing Page",
  "quando": "2025-12-28T18:30:45.123Z",
  "timestamp": "28/12/2025, 15:30:45"
}
```

## 📞 Contato

**WhatsApp**: +55 11 91094-0045

## 🎨 Design

- **Cores Principais**: 
  - Roxo: `#667eea`, `#764ba2`
  - Laranja: `#f59e0b`, `#d97706`
  - Verde: `#10b981`, `#22c55e`
- **Fontes**: System fonts (sans-serif)
- **Animações**: Smooth transitions, hover effects, pulse

## 🌐 Idiomas

- 🇧🇷 Português (padrão)
- 🇦🇷 Español

Toggle localizado abaixo do header fixo.

## 📦 Deploy

Arquivo único `index.html` - deploy simples em qualquer servidor:
- GitHub Pages
- Netlify
- Vercel
- Servidor tradicional

## 🔒 Segurança

- ✅ Snyk Code Scan: 0 vulnerabilidades
- ✅ Sem dependências externas
- ✅ HTTPS recomendado para produção

## 📝 Notas

- Cache control headers incluídos
- Meta tags otimizadas
- Versão: 2025-12-28
- Browser support: Chrome, Firefox, Safari, Edge (últimas 2 versões)

---

**Desenvolvido para Residencial Vera** 🏖️
Cachoeira do Bom Jesus - Florianópolis/SC
