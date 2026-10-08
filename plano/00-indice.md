# Plano — Renê Sábio: site novo, portal do cliente e prospecção

Documento vivo. Cada etapa tem um arquivo próprio nesta pasta. Status: ⬜ a fazer · 🟡 em andamento · ✅ feito.

## Decisões já tomadas

| Tema | Decisão |
|---|---|
| Site institucional | 5 páginas (Início, Sobre, Serviços, Blog, Contato): **R$1.600 de implantação + R$300/mês** |
| Landing page | **R$800 de implantação + R$300/mês** |
| Manutenção | Obrigatória, fidelidade de 12 meses, R$300/mês |
| Portal do cliente | "Cara de SaaS": cadastro → briefing → área do cliente com módulos em **"Tenho interesse"** (nunca "Ativar") |
| Servidor | VPS Hostgator 2 GB com Easypanel. Desligar **Inbound Hub** e **Klaryo** |
| Site renesabio.com.br | Sai do HTML/GitHub e passa para **WordPress** no Easypanel |
| Portal | App separado, publicado pelo **GitHub → Easypanel** (ex.: `portal.renesabio.com.br`) |
| Domínios de e-mail | `renesabio.com.br` = domínio limpo (contato e clientes). `renesabio.com` = prospecção |
| DNS | Cloudflare |
| WhatsApp | Seu número pessoal, via Evolution API (riscos e limites na etapa 7) |
| Ferramentas | n8n, Brevo (CRM), Evolution API |

## Etapas

| # | Etapa | Arquivo | Status |
|---|---|---|---|
| 1 | Oferta e módulos do portal | [01-oferta-e-modulos.md](01-oferta-e-modulos.md) | 🟡 |
| 2 | Estrutura e textos do site novo | 02-site-estrutura-e-textos.md | ⬜ |
| 3 | Easypanel: desligar apps antigos e subir o WordPress | 03-easypanel-wordpress.md | ⬜ |
| 4 | Montar o site no WordPress | 04-montagem-wordpress.md | ⬜ |
| 5 | Portal do cliente (GitHub → Easypanel) | 05-portal-cliente.md | ⬜ |
| 6 | Fluxos no n8n (briefing, interesse, alterações, Brevo) | 06-fluxos-n8n.md | ⬜ |
| 7 | E-mail e WhatsApp (domínio .com, Evolution API, limites) | 07-email-whatsapp.md | ⬜ |
| 8 | SEO e atendimento por IA | 08-seo-e-atendimento-ia.md | ⬜ |
| 9 | Prospecção (Google Maps, sequências de 3 e-mails e 2 WhatsApp) | 09-prospeccao.md | ⬜ |

## Pontos de atenção (para não esquecer)

1. **DNS do renesabio.com.br:** nos testes, o domínio não resolveu. Confira no Cloudflare se o registro A aponta para o IP da VPS.
2. **Memória da VPS (2 GB):** WordPress + MySQL + n8n + Evolution API (com Postgres/Redis) + portal ficam apertados. Avaliar na etapa 3. Pode ser preciso subir para 4 GB ou mover algo.
3. **Número pessoal no WhatsApp:** prospecção fria pelo número pessoal tem risco real de banimento. Detalhes e limites na etapa 7.
4. **Teto do MEI:** com cerca de 20 clientes na recorrência, você passa do limite anual. Falar com um contador antes.
