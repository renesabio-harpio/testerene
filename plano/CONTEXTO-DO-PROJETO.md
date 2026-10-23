# Contexto do projeto — Renê Sábio (sites + portal + prospecção)

> Leia este arquivo inteiro antes de qualquer coisa num chat novo. Depois abra `plano/00-indice.md` para ver o status de cada etapa.

## 1. Quem é o Renê e o que ele faz

- Empreendedor solo que **cria sites em WordPress/Elementor** para pequenas e médias empresas B2B de serviços.
- Domínio principal: **renesabio.com.br** (site atual em HTML, que vai virar WordPress).
- Portfólio real: **Syna Seguros** e **RHP Invest** (corretoras de seguros), **Synait** (integradora de TI), **S91 Digital** (tecnologia) e **Harpio** (SaaS de recrutamento com IA).
- Os clientes atuais já pagam **R$1.600 de implantação + R$300/mês** de manutenção. Hoje pagam por Pix, alguns agendados e outros só depois de ele lembrar.

## 2. Como trabalhar com o Renê (preferências)

- Responder **um passo de cada vez**, com **no máximo 3 itens** por resposta, e **perguntar se pode seguir** ao final de cada passo.
- **Sempre trazer um plano antes de executar.**
- Em tarefas com passo a passo, mostrar primeiro o **índice resumido** e depois avançar um passo por resposta.
- Avisar quando a conversa estiver ficando longa. Ele **prefere continuar no mesmo chat** e só abrir um novo quando o contexto ficar grande.
- Ele é leigo em algumas partes técnicas: explicar com analogias simples.
- **Registrar tudo em arquivos `.md` na pasta `plano/`** e fazer commit e push a cada atualização.

## 3. Oferta (decidida)

| Plano | Implantação | Mensal |
|---|---|---|
| Landing Page | R$800 | R$300 |
| Site Institucional (Início, Sobre, Serviços, Blog, Contato) | R$1.600 | R$300 |

- Os R$300/mês são **obrigatórios**, com **hospedagem e domínio inclusos** (ele cuida de tudo), contrato de 12 meses e **renovação anual automática**, porque domínio e hospedagem são pagos por ano.
- Incluso nos R$300: site no ar, segurança, backups, até 2 alterações por mês, publicação no blog e relatório mensal.
- Ajustes acima do limite: R$120/h. Regras de saída e de contrato detalhadas em `plano/01-oferta-e-modulos.md`.

## 4. Pagamento (regra: **receber na hora**)

- **Mensalidade e implantação por Pix → Asaas.** O Pix cai na hora. O Asaas também lembra o cliente sozinho, emite a NFS-e e manda webhook para o n8n. O cartão fica **desligado** na mensalidade, porque no Asaas ele cai só em D+32.
- **Implantação no cartão, à vista ou parcelada → InfinitePay**, que paga na hora. Ele já tem conta CNPJ lá.
- Saque automático do Asaas para o Nubank PJ via n8n (webhook "pagamento recebido" → Pix). A conta PJ tem 30 transferências grátis por mês.
- Custo por Pix no Asaas: cerca de R$3,47 por cobrança (Pix + NF + lembretes).
- **Status:** combinação Asaas + InfinitePay proposta, **aguardando confirmação final do Renê**.

## 5. Portal do cliente ("cara de SaaS")

- Fica **dentro do WordPress**, em **`renesabio.com.br/area-do-cliente`**. É **uma única página dinâmica**: cada cliente faz login e vê só os dados dele. **Nunca** criar uma página por cliente.
- Fluxo: pagamento → n8n cria o usuário no WordPress → e-mail com o acesso → briefing → status do site, pedido de alteração e catálogo de módulos.
- **8 módulos** com o botão **"Tenho interesse"** (nunca "Ativar"): SEO Local, Conteúdo para o Blog, Google Meu Negócio, Atendimento com IA, Automação de WhatsApp, Landing Page de Campanha, E-mail Profissional e Relatório Avançado. Cada clique avisa o Renê no WhatsApp e no Brevo, e ele negocia. Um módulo só é construído de verdade depois que 3 clientes pedirem.

## 6. Infraestrutura e ferramentas

- **VPS Hostgator de 2 GB com Easypanel.** Hoje roda 3 apps: Inbound Hub, Klaryo e René Sábio. **Desligar o Inbound Hub e o Klaryo**, e o René Sábio passa para **WordPress**.
- O **n8n** roda na mesma VPS. A memória é apertada: avaliar se WordPress + n8n + Evolution API cabem em 2 GB.
- **DNS no Cloudflare.** Nos testes, o `renesabio.com.br` **não resolveu**: verificar o registro A.
- **E-mail:** `renesabio.com.br` = domínio limpo (clientes e contato); `renesabio.com` = disparos de prospecção.
- **WhatsApp:** o **número pessoal** do Renê via **Evolution API** (ele não quer outro número). Risco de banimento: usar poucos envios por dia e aprovação manual.
- **Brevo** como CRM e para rastrear quem visitou o site (Brevo Tracker). **GA4** via Site Kit. Banner de cookies obrigatório (LGPD).
- Ele também tem conectores do **Lusha** (plano gratuito, 40 créditos) e do **Apollo**. Para o perfil de cliente "sem site ou com site ruim", a fonte de prospecção recomendada é o **Google Maps (Places API)**.

## 7. Decisões e aprendizados dos conselhos (não revisitar)

- "Só o site" não se sustenta: a mensalidade precisa de **entregas visíveis** (relatório, alterações, Google).
- **Nunca esconder o preço total.** Apresentar implantação + mensal juntos.
- Prospecção fria com Lusha para os clientes dos clientes **não funciona** (o público deles é pessoa física). O Lusha e o Google Maps servem para prospectar **os clientes do próprio Renê**.
- SaaS self-service completo **não agora**: a "cara de SaaS" é só uma vitrine com o botão "Tenho interesse".
- Atenção ao **teto do MEI**: com cerca de 20 clientes na recorrência, ele estoura. Falar com um contador.

## 8. Onde paramos

- ✅ Etapa 1: oferta e módulos.
- 🟡 Etapa 5: portal (conceito aprovado). Etapa 6: medição (plano escrito).
- ⏳ Aguardando a confirmação **Asaas (Pix) + InfinitePay (cartão)**.
- ▶️ **Próximo passo: Etapa 2 — estrutura e textos do site** (Início, Sobre, Serviços, Portfólio, Blog, Contato, Contratar e Área do Cliente), com posicionamento B2B: *"Sites profissionais para empresas de serviços, seguros e tecnologia"*.

## 9. Arquivos

| Arquivo | Conteúdo |
|---|---|
| `plano/00-indice.md` | Decisões, as 10 etapas com status e pontos de atenção |
| `plano/01-oferta-e-modulos.md` | Planos, contrato, pagamento (comparação e custos), módulos |
| `plano/05-portal-cliente.md` | Como o portal funciona (página única e dinâmica) |
| `plano/06-medicao-e-rastreamento.md` | GA4, Brevo Tracker e LGPD |
