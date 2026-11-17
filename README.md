# Delipastel

Custo de produção e preço de venda dos salgados da fábrica (fritos e assados).

- `site/` — o aplicativo (um único `index.html` + PWA instalável no celular).
- Os dados ficam no Supabase (tabela `delipastel_dados`, dentro do projeto `agenda-pagamentos` — o plano grátis só permite 2 projetos).
  O app pede o **código da fábrica** e usa as funções `delipastel_ler` e `delipastel_salvar`.
- Se dois aparelhos salvarem ao mesmo tempo, o app avisa e pergunta qual versão manter.

## Publicação
Cloudflare Workers ligado a este repositório: cada envio para `main` publica sozinho (`wrangler.jsonc`).
`worker/index.js` serve o site e acessa o banco a cada 2 dias para o Supabase não pausar.
Teste: abrir `/__ping-db` no endereço do app (deve mostrar `banco: 200`).
