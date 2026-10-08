# Etapa 1 — Oferta e módulos do portal

## 1. Planos

| Plano | Implantação | Mensal (12 meses) | O que entrega |
|---|---|---|---|
| **Landing Page** | R$800 | R$300 | 1 página de vendas, botão de WhatsApp, formulário, domínio |
| **Site Institucional** | R$1.600 | R$300 | Início, Sobre, Serviços, Blog, Contato, botão de WhatsApp, formulário, domínio |

**Como apresentar** (lição do conselho: nunca esconder o total):

> **Site Institucional:** R$1.600 de implantação + R$300/mês com tudo incluso.
> Contrato de 12 meses. O domínio fica no seu nome.

### O que está incluso nos R$300/mês

Escrito em linguagem de resultado, sem termos técnicos assustadores:

- **Seu site sempre no ar.** Se cair, eu resolvo em até 24h.
- **Protegido e atualizado.** Segurança, backups semanais e monitoramento.
- **Hospedagem e domínio sob meus cuidados.** Você não paga nada à parte.
- **Até 2 alterações por mês.** Trocar texto, foto, telefone ou banner.
- **Publicação no blog com a formatação certa.** Você manda o texto, eu publico.
- **Relatório mensal simples.** Visitas e cliques no WhatsApp. *(Entra com as etapas 6 e 7: medição e fluxos.)*

### Regras de contrato (proteção para quem trabalha sozinho)

- Ajustes: até 2 por mês ou 1h no total, sem acumular. O que passar disso: R$120/h.
- Saída antecipada: o cliente paga 30% das mensalidades que faltam **ou** leva o site exportado mediante uma taxa.
- **Renovação anual automática:** domínio e hospedagem são pagos por ano, então o contrato renova por mais 12 meses. Para não renovar, o cliente avisa com 30 dias de antecedência do fim do ciclo.
- Você manda um lembrete 45 dias antes do fim do ciclo (automação no n8n).
- Domínio no nome do cliente; você administra.
- Cobrança pelo checkout no próprio site (detalhes abaixo). Implantação: 50% no aceite e 50% na entrega, ou 100% no checkout.

## 1.1 Checkout no site (InfinitePay)

**Decisão: InfinitePay**, que você já usa e que já tem **link de assinatura** cobrando R$300/mês no cartão. Não há motivo para trocar. O Mercado Pago também tem assinatura, mas fica só como plano B.

**Como fica no site** (página `/contratar`):

| Plano | Botão 1: implantação | Botão 2: assinatura |
|---|---|---|
| Landing Page | Pagar R$800 (link avulso InfinitePay) | Assinar R$300/mês (link de assinatura InfinitePay) |
| Site Institucional | Pagar R$1.600 (link avulso InfinitePay) | Assinar R$300/mês (link de assinatura InfinitePay) |

**Depois do pagamento:**
- Se a InfinitePay avisar automaticamente (webhook), o n8n libera o portal sozinho.
- Se não avisar, o caminho simples é: você recebe a notificação do pagamento e clica em um botão no n8n (ou responde "pago" no WhatsApp) para liberar o cliente. É 1 clique por venda. Confira no painel da InfinitePay se há webhook ou notificação por e-mail que o n8n possa ler.

Quando alguém te chamar no WhatsApp, você só manda o link de `/contratar`.

## 2. Módulos do portal ("Tenho interesse")

Cada módulo é um card com nome, uma frase de benefício e o botão **Tenho interesse**. O clique dispara o n8n, que te avisa no WhatsApp, cria ou atualiza o contato no Brevo e mostra ao cliente: *"Recebemos! O Renê vai te chamar em até 1 dia útil."*

| Módulo | Frase no card | Faixa de preço sugerida (só para você negociar) |
|---|---|---|
| **SEO Local** | Apareça no Google quando procurarem pelo seu serviço na sua cidade. | +R$150 a 300/mês |
| **Conteúdo para o Blog** | 2 artigos por mês escritos para o seu público, publicados por mim. | +R$200 a 400/mês |
| **Google Meu Negócio** | Perfil otimizado no Google Maps, com fotos, horários e avaliações. | R$300 a 500 (único) |
| **Atendimento com IA** | Um assistente que responde e qualifica clientes no seu site 24h. | +R$200 a 500/mês |
| **Automação de WhatsApp** | Respostas automáticas, lembretes e follow-up de orçamento. | +R$200 a 400/mês |
| **Landing Page de Campanha** | Uma página extra para uma promoção ou um serviço específico. | R$500 a 800 (único) |
| **E-mail Profissional** | voce@suaempresa.com.br configurado. | R$100 a 200 (único) |
| **Relatório Avançado** | Painel mensal com origem das visitas e dos contatos. | +R$100/mês |

**Preço não aparece no portal.** O card só mostra o benefício, e você negocia no contato. Assim você descobre o que tem demanda antes de construir.

### Regras dos módulos

- O botão sempre diz **"Tenho interesse"** ou **"Solicitar"**, nunca "Ativar".
- Depois do clique, o card muda para **"Solicitado — aguardando contato"**.
- Você só constrói um módulo de verdade depois que **3 clientes pedirem**.

## 3. Pendências desta etapa

- [x] Hospedagem e domínio inclusos nos R$300 (confirmado)
- [x] Lista de módulos aprovada
- [ ] Pedir um depoimento curto aos clientes atuais (Syna Seguros, RHP Invest, Synait, S91, Harpio)
