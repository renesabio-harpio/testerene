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

## 1.1 Pagamento e checkout no site

**Situação hoje:** os clientes pagam por Pix, alguns agendados e outros só depois de você lembrar. Ninguém usa cartão recorrente.

### Comparação (pesquisa feita em out/2026, confira taxas no site de cada um)

| | **Asaas** | Mercado Pago | Stripe | InfinitePay |
|---|---|---|---|---|
| Assinatura recorrente nativa | ✅ Cartão, boleto com QR Pix e **Pix Automático** (via API) | ✅ Só cartão (link de assinatura) | ✅ Cartão e **Pix recorrente** (desde abr/2026) | ❌ Não documentada |
| Cobra e lembra o cliente sozinho | ✅ E-mail, SMS e WhatsApp | Parcial | Parcial | ❌ |
| Webhook (para o n8n) | ✅ Completo | ✅ | ✅ Excelente | Só por link pago |
| WordPress | Plugin para WooCommerce, ou só links e API (sem loja) | Plugin oficial para WooCommerce | Plugins | Link de pagamento |
| Nota fiscal (NFS-e) automática | ✅ | ❌ | ❌ | ❌ |
| Conta CNPJ | ✅ | ✅ | ✅ | ✅ (você já tem) |

### Recomendação: **Asaas**

1. **Resolve o seu problema real:** o Asaas gera a cobrança todo mês e **lembra o cliente sozinho**. Você para de cobrar na mão.
2. **O cliente continua pagando por Pix**, que é o que ele já faz, ou por cartão ou boleto, se preferir.
3. **Emite a nota fiscal automaticamente** a cada pagamento.
4. **Webhook completo:** quando alguém paga, atrasa ou cancela, o n8n fica sabendo e age (libera o portal, te avisa no WhatsApp, atualiza o Brevo).
5. **Não precisa de WooCommerce.** O site só tem um formulário "Contratar".

### Como fica o checkout no site (página `/contratar`)

```
Cliente escolhe o plano e preenche nome, CNPJ, e-mail, WhatsApp
   → n8n cria o cliente no Asaas
   → n8n cria a cobrança da implantação (R$800 ou R$1.600) + a assinatura de R$300/mês
   → o cliente cai na página de pagamento do Asaas (Pix, cartão ou boleto)
   → pagou: webhook → n8n libera o portal, manda o briefing e te avisa no WhatsApp
```

Quando alguém te chamar no WhatsApp, você só manda o link de `/contratar`.

**Clientes atuais:** cadastre cada um no Asaas com a assinatura de R$300/mês. A partir daí a cobrança e o lembrete passam a ser automáticos.

### Custo real no Asaas (tabela oficial enviada por você, out/2026)

Taxas padrão (os 3 primeiros meses têm preço promocional menor):

| Item | Taxa |
|---|---|
| Pix recebido | R$1,99 por pagamento |
| Boleto recebido | R$1,99 por pagamento |
| Cartão de crédito (assinatura) | R$0,49 + 2,99% |
| Nota fiscal (NFS-e) | R$0,49 por nota |
| Lembretes por e-mail + SMS | R$0,99 por cobrança paga (sem limite de mensagens) |
| Lembrete por WhatsApp | R$0,55 por mensagem (opcional) |
| Transferência Pix para sua conta (PJ) | 30 grátis por mês |
| Conta, mensalidade e emissão de cobrança | Grátis |

**Quanto sobra por cliente:**

| Cobrança | Pago por Pix + NF + lembretes | Pago no cartão + NF + lembretes |
|---|---|---|
| Mensalidade R$300 | Custo **R$3,47** (1,2%) → recebe **R$296,53** | Custo R$10,94 → recebe R$289,06 |
| Implantação R$1.600 | Custo **R$3,47** → recebe **R$1.596,53** | Custo R$49,81 → recebe R$1.550,19 |

**Configuração recomendada:** Pix como forma principal, cartão como opção, lembretes por e-mail + SMS ligados e WhatsApp desligado (você já tem o seu próprio).

### Quando o dinheiro fica disponível no Asaas

| Forma de pagamento | Disponível para sacar |
|---|---|
| **Pix** | **Na hora** (24/7) |
| Boleto | 0 a 2 dias úteis |
| Cartão de débito | 1 a 3 dias |
| Cartão de crédito à vista | **D+32** (32 dias depois) |
| Cartão parcelado | Uma parcela a cada 32 dias (D+32, D+64…) |
| Antecipação do cartão | Recebe tudo em até 2 dias úteis, pagando 1,25% ao mês (à vista) ou 1,70% ao mês (parcelado), sujeito a análise de crédito |

**Transferência automática para o Nubank PJ:** não achei na documentação do Asaas uma opção nativa de "saque automático". Dá para montar no n8n: chega o webhook "pagamento recebido", o n8n manda um Pix do saldo para a sua chave do Nubank PJ. São 30 transferências Pix grátis por mês para PJ. Confirme com o suporte do Asaas se a API de transferência exige alguma liberação extra (whitelist de IP ou token de segurança).

**Plano B:** Stripe, que tem o melhor checkout e suporta Pix recorrente, mas não emite nota fiscal.

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
