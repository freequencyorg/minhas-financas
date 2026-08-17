# Minhas Finanças 💰 

App pessoal de finanças — simples, em português, feito para funcionar no celular e no computador, com os dados sincronizados num repositório **privado** do GitHub.

**Acesse:** `https://SEU-USUARIO.github.io/minhas-financas/`

## O que ele faz

- **Lançamentos** — registre receitas e despesas por categoria, com busca e filtros
- **Painel do mês** — saldo, gráfico de gastos por categoria, comparação dos últimos 6 meses e previsão do mês com base nas contas fixas
- **Fixas** — contas a pagar e a receber todo mês (aluguéis, luz, internet…), com um toque para marcar como pago/recebido
- **Orçamento** — limite de gasto por categoria com barra de progresso
- **Metas** — objetivos de economia com acompanhamento
- **Backup** — exporte/importe seus dados em JSON quando quiser

## Como funciona a sincronização

O app é 100% estático (um único `index.html`, publicado no GitHub Pages). Os seus dados **não ficam neste repositório** — ficam num segundo repositório, **privado**, chamado `minhas-financas-dados`, num arquivo `dados.json` que o app lê e grava pela API do GitHub usando um token que só você tem.

```
┌─────────────────────┐        ┌──────────────────────────┐
│  minhas-financas    │        │  minhas-financas-dados   │
│  (público, só o app)│        │  (PRIVADO, seus números) │
│  GitHub Pages       │  token │  dados.json              │
│  index.html ────────┼───────►│                          │
└─────────────────────┘        └──────────────────────────┘
```

## Publicar (uma vez só)

1. Crie um repositório público chamado `minhas-financas` e envie o `index.html` e este `README.md`.
2. Em **Settings → Pages**, em *Branch* escolha `main` e salve. Em ~1 minuto o app estará no ar em `https://SEU-USUARIO.github.io/minhas-financas/`.
3. Crie um repositório **privado** chamado `minhas-financas-dados` (pode ficar vazio — o app cria o `dados.json` sozinho na primeira conexão).
4. Crie um token *fine-grained* em `github.com/settings/personal-access-tokens/new`:
   - **Repository access:** *Only select repositories* → `minhas-financas-dados`
   - **Permissions → Contents:** *Read and write*
   - Validade: 1 ano (quando vencer, gere outro e cole no app de novo)
5. Abra o app, informe usuário, repositório de dados e o token. Pronto.

## No celular

Abra o endereço no navegador e use **"Adicionar à tela de início"** — vira um atalho como um app de verdade. Na primeira vez, cole o mesmo token (é a única configuração).

## Segurança

- O repositório de dados é privado; só o seu token acessa.
- O token fica salvo apenas no navegador de cada aparelho (localStorage), tem acesso a **um único repositório** e pode ser revogado a qualquer momento em GitHub → Settings → Developer settings.
- Ninguém além de você vê seus números — nem este repositório público os contém.

---

Feito com [Claude](https://claude.com) 🤖
