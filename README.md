# Site do Éthyan

Estrutura:

```
index.html       site (ficha, livro de regras, lore, painel do mestre)
api/sheet.js     criar, ler e atualizar fichas
api/master.js    lista todas as fichas (protegido por senha)
api/_db.js       acesso ao banco (Upstash Redis)
```

## Como publicar no Vercel

1. Suba esta pasta para um repositório no GitHub e importe no Vercel (ou use `vercel` na pasta).
2. No projeto, vá em **Storage / Marketplace** e adicione o **Upstash Redis** (plano gratuito basta). Isso cria as variáveis `KV_REST_API_URL` e `KV_REST_API_TOKEN` sozinho.
3. Em **Settings → Environment Variables**, crie `MASTER_KEY` com a senha do mestre.
4. Faça o deploy (ou redeploy, para as variáveis valerem).

## Como funciona

- Cada ficha ganha um código de 8 caracteres e um link (`/?f=codigo`). Quem tem o link edita a ficha, sem login.
- O salvamento é automático, 0,8 s depois de editar.
- A aba **Mestre** lista todas as fichas com a senha `MASTER_KEY`.

## Para expandir

Lore e regras estão nos arrays `LORE` e `RULES` no topo do script do `index.html`. Ethynias e bônus ficam em `ETHYNIAS`.
