# Plano — Renê Sábio: site novo, portal do cliente e prospecção

Documento vivo. Cada etapa tem um arquivo próprio nesta pasta. Status: ⬜ a fazer · 🟡 em andamento · ✅ feito.

## Decisões já tomadas

| Tema | Decisão |
|---|---|
| Site institucional | 5 páginas (Início, Sobre, Serviços, Blog, Contato): **R$1.600 de implantação + R$300/mês** |
| Landing page | **R$800 de implantação + R$300/mês** |
| Manutenção | Obrigatória, R$300/mês com hospedagem e domínio inclusos, contrato de 12 meses com **renovação anual automática** |
| Pagamento | **Regra: receber na hora.** Mensalidade e implantação por Pix no **Asaas** (lembrete automático, NFS-e, webhook). Implantação no cartão ou parcelada pela **InfinitePay** (recebe na hora). Aguardando sua confirmação |
| Medição | **Google Analytics 4** + rastreamento de quem visitou (Brevo Tracker) |
| Portal do cliente | "Cara de SaaS": cadastro → briefing → área do cliente com módulos em **"Tenho interesse"** (nunca "Ativar") |
| Servidor | VPS Hostgator 2 GB com Easypanel. Desligar **Inbound Hub** e **Klaryo** |
| Site renesabio.com.br | Sai do HTML/GitHub e passa para **WordPress** no Easypanel |
| Portal | **Dentro do WordPress**, em `renesabio.com.br/area-do-cliente`. Uma única página dinâmica: cada cliente faz login e vê só os dados dele |
| Domínios de e-mail | `renesabio.com.br` = domínio limpo (contato e clientes). `renesabio.com` = prospecção |
| DNS | Cloudflare |
| WhatsApp | Seu número pessoal, via Evolution API (riscos e limites na etapa 8) |
| Ferramentas | n8n (na mesma VPS), Brevo (CRM), Evolution API |

## Etapas

| # | Etapa | Arquivo | Status |
|---|---|---|---|
| 1 | Oferta e módulos do portal | [01-oferta-e-modulos.md](01-oferta-e-modulos.md) | ✅ |
| 2 | Estrutura e textos do site novo | 02-site-estrutura-e-textos.md | ⬜ |
| 3 | Easypanel: desligar apps antigos e subir o WordPress | 03-easypanel-wordpress.md | ⬜ |
| 4 | Montar o site no WordPress | 04-montagem-wordpress.md | ⬜ |
| 5 | Portal do cliente (área única e dinâmica) | [05-portal-cliente.md](05-portal-cliente.md) | 🟡 |
| 6 | Medição: GA4 e quem visitou o site | [06-medicao-e-rastreamento.md](06-medicao-e-rastreamento.md) | 🟡 |
| 7 | Fluxos no n8n (checkout, briefing, interesse, alterações, Brevo) | 07-fluxos-n8n.md | ⬜ |
| 8 | E-mail e WhatsApp (domínio .com, Evolution API, limites) | 08-email-whatsapp.md | ⬜ |
| 9 | SEO e atendimento por IA | 09-seo-e-atendimento-ia.md | ⬜ |
| 10 | Prospecção (Google Maps, sequências de 3 e-mails e 2 WhatsApp) | 10-prospeccao.md | ⬜ |

## Pontos de atenção (para não esquecer)

1. **DNS do renesabio.com.br:** nos testes, o domínio não resolveu. Confira no Cloudflare se o registro A aponta para o IP da VPS.
2. **Memória da VPS (2 GB):** WordPress + MySQL + n8n + Evolution API (com Postgres/Redis) + portal ficam apertados. Avaliar na etapa 3. Pode ser preciso subir para 4 GB ou mover algo.
3. **Número pessoal no WhatsApp:** prospecção fria pelo número pessoal tem risco real de banimento. Detalhes e limites na etapa 8.
4. **Teto do MEI:** com cerca de 20 clientes na recorrência, você passa do limite anual. Falar com um contador antes.
5. **LGPD e cookies:** rastrear quem visitou exige banner de consentimento e aviso na Política de Privacidade (etapa 6).
