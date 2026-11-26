# DUTON — Landing Page v2 (azul/laranja + Growth Score)

Arquivo único e autocontido: `index.html` (HTML, CSS e JS no mesmo arquivo; fonte Inter via Google Fonts).

## O que mudou em relação à LP original (verde/coral)
| Antes | Agora |
|---|---|
| Identidade verde/coral (histórica) | Identidade aprovada: azul-marinho, azul, laranja, branco gelo + logo vetorial de estudo |
| 13 serviços com filtro | 4 frentes de valor (detalhe vai para a proposta) |
| 3 planos + Insight, Essential em destaque | Escada: Growth Score → Sessão de Direção → Insight → Growth → Executive; Essential fora do site |
| Sem lead magnet | **Growth Score interativo** (10 perguntas, 5 dimensões, resultado + prioridade) que pré-preenche o formulário |
| Sem oferta de lançamento | Bloco **Programa Fundadores** (5 vagas) |
| Formulário sem consentimento | Consentimento LGPD obrigatório + link para Política de Privacidade |

## Testes realizados (Chromium/Playwright)
- Desktop 1366 px e mobile 390 px: sem rolagem horizontal, sem erros de JavaScript.
- Quiz: 10 respostas → pontuação, faixa de maturidade, prioridade e preenchimento do campo oculto `growth_score`.
- Formulário: bloqueia envio sem campos obrigatórios e sem consentimento; sem configuração, informa claramente que é demonstração e **não envia dados**.
- Eventos `dataLayer`: `cta_click`, `plan_select`, `growth_score_start`, `growth_score_complete`, `form_start`, `form_submit_success`, `form_submit_error`, `form_mailto_open`, `form_demo_submit`, `whatsapp_click`.

## Antes de publicar (nada foi publicado)
1. Aprovar textos, preços "a partir de" e o Programa Fundadores.
2. Confirmar registro do domínio `somosduton.com.br` em nome da empresa e HTTPS.
3. Publicar a **Política de Privacidade** e preencher `privacyUrl`.
4. Configurar captação em `DUTON_CONFIG` (fim do arquivo):
   - **Recomendado no stack Zoho:** criar formulário no Zoho Forms ou um webhook no Zoho Flow que crie o Lead no Zoho CRM; usar a URL HTTPS em `formEndpoint` (POST JSON). Mapear campos: nome, empresa, email, telefone, cargo, interesse, desafio, growth_score, origem, consentimento, data_envio. Testar CORS e um envio real ponta a ponta.
   - Alternativa provisória: preencher apenas `email` (abre o aplicativo de e-mail do visitante).
   - `whatsapp`: somente números com DDI; o botão flutuante aparece automaticamente.
5. Instalar GTM (snippet no `<head>` e `<body>`) e configurar GA4 com os eventos acima como conversões (`form_submit_success`, `growth_score_complete`). Avaliar banner de consentimento de cookies conforme as tags usadas.
6. Remover `<meta name="robots" content="noindex, nofollow">` e ativar o `canonical` somente na revelação pública (26/01/2027).
7. Hospedagem: qualquer hospedagem estática com HTTPS (o arquivo não exige servidor). Apontar DNS do domínio conforme o provedor escolhido.
