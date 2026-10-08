# Etapa 6 — Medição: GA4 e quem visitou o site

Objetivo: saber **quantas** pessoas visitam (GA4) e **quem** visitou (Brevo), como no rastreamento de leads do RD Station.

## 1. Google Analytics 4 (quantas pessoas, de onde, o quê)

- Instalar com o plugin **Site Kit by Google**, o mesmo que você já usa nos sites dos clientes. Ele conecta GA4 e Search Console de uma vez.
- **Eventos a configurar:**
  - `clique_whatsapp`: botão de WhatsApp
  - `envio_formulario`: formulário de contato
  - `inicio_checkout`: clique em "Pagar" ou "Assinar"
  - `cadastro_portal`: cadastro na área do cliente
- Marcar `inicio_checkout` e `envio_formulario` como **conversões**.
- Isso responde: quantos visitaram, de qual canal vieram (Google, WhatsApp, e-mail) e quantos clicaram para falar com você.

**Limite:** o GA4 é anônimo. Ele não diz *quem* é cada visitante.

## 2. Saber quem visitou (estilo RD Station): Brevo Tracker

É a mesma lógica do RD Station: quando a pessoa **clica num e-mail seu**, ela fica identificada, e a partir daí cada página que ela visita aparece no histórico do contato.

**Como funciona:**
1. Você instala o **script de rastreamento do Brevo** no WordPress (plugin oficial do Brevo ou o código no cabeçalho).
2. O contato é identificado quando:
   - clica num link de e-mail enviado pelo Brevo, ou
   - preenche um formulário do site (o n8n ou o plugin manda o e-mail para o Brevo).
3. No Brevo, dentro do contato, você vê **as páginas visitadas, quando e quantas vezes**.
4. Gatilho útil: *"visitou /contratar ou /servicos 2 vezes em 7 dias"* → automação no Brevo ou no n8n → **aviso no seu WhatsApp**: "Fulano está olhando a página de preços". Essa é a hora de ligar.

**Para cada e-mail enviado você vai ver:** quem abriu, quem clicou e quais páginas do site visitou depois.

## 3. Bônus: empresas anônimas (opcional, para depois)

O **Lusha** tem um recurso de *website visits* que identifica **a empresa** (não a pessoa) que visitou o site, mesmo sem clique em e-mail. No plano gratuito é limitado. Fica como opção para quando o volume de visitas crescer.

## 4. LGPD (obrigatório)

- **Banner de cookies** com consentimento (plugin *Complianz* ou *CookieYes*, ambos com versão gratuita).
- O script do Brevo e o GA4 **só carregam depois do aceite**.
- A **Política de Privacidade** deve dizer que você rastreia a navegação de contatos identificados para fins comerciais, e como a pessoa pede a exclusão.

## 5. Painel para você

- **Brevo** (contato por contato): quem visitou, o que abriu, o que clicou.
- **GA4 / Site Kit** (visão geral): tráfego e conversões no painel do WordPress.
- **Depois (etapa 7):** um resumo semanal automático no seu WhatsApp, montado pelo n8n: "Esta semana: X visitas, Y cliques no WhatsApp, Z contatos quentes".

## Pendências

- [ ] Ter uma conta GA4 (ou criar) para o renesabio.com.br
- [ ] Confirmar o plano do Brevo (o rastreamento de site está disponível no gratuito, mas confira os limites no seu painel)
- [ ] Escolher o plugin de cookies
