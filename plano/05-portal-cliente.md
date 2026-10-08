# Etapa 5 — Portal do cliente (área única e dinâmica)

## Como funciona, em linguagem simples

**É uma página só, que muda conforme quem faz login.** É como o Netflix ou o app do banco: o app é o mesmo para todo mundo, e cada pessoa entra com a própria senha e vê só as coisas dela.

- Você **não cria uma página por cliente**. Existe **uma** "Área do Cliente".
- Cada cliente é **uma linha num banco de dados** (nome, e-mail, link do site, plano, status, módulos pedidos).
- Quando o cliente faz login, a página puxa a linha dele e mostra os dados dele.
- **Cadastrar um cliente novo = criar uma linha**, e quem faz isso é o n8n, automaticamente, depois do pagamento.

```
Cliente paga  →  n8n cria o usuário + a linha no banco  →  e-mail: "Seu acesso está pronto"
Cliente entra →  a mesma página de sempre mostra os dados DELE
```

## O que o cliente vê

1. **Meu site:** link, status ("No ar" / "Em construção") e a data da próxima renovação.
2. **Briefing:** formulário (só aparece enquanto o site está em construção).
3. **Pedir alteração:** campo de texto e anexo. O pedido vai para o n8n, que te avisa no WhatsApp. Mostra "2 de 2 alterações usadas neste mês".
4. **Módulos:** os 8 cards da etapa 1, com o botão "Tenho interesse".
5. **Relatório do mês:** visitas e cliques no WhatsApp (entra depois, com as etapas 6 e 7).

## Onde construir: recomendação

**Recomendação: dentro do próprio WordPress**, em `renesabio.com.br/area-do-cliente`.

| | Dentro do WordPress | App separado (GitHub → Easypanel) |
|---|---|---|
| Login e senha | Já vem pronto (usuários do WP) | Precisa construir |
| Memória na VPS de 2 GB | Nenhum serviço extra | Mais um container rodando |
| Manutenção | Uma coisa só para cuidar | Duas |
| Visual "cara de SaaS" | Dá, com uma página em tela cheia sem o menu do site | Mais liberdade |

Os dados de cada cliente ficam no próprio usuário do WordPress (campos extras). O n8n cria e atualiza esses usuários pela API do WordPress. A página da área do cliente é **um template único** que lê os dados de quem está logado.

Se no futuro o portal crescer muito, ele migra para um app separado. Para começar, o WordPress resolve com menos peças.

## Pendências

- [ ] Aprovar: portal dentro do WordPress (recomendado) ou app separado
- [ ] Definir o endereço: `/area-do-cliente` ou um subdomínio `cliente.renesabio.com.br`
