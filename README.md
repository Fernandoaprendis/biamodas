# Bia Modas

Código da loja virtual Bia Modas: moda feminina e perfumes árabes femininos e masculinos.

## Estado atual

- Layout responsivo em português, pesquisa e filtros por categoria.
- Sacola com sessões independentes, inclusão, alteração de quantidades e remoção.
- Categorias e imagens ilustrativas; produtos, tamanhos, volumes e estoque ainda precisam ser cadastrados.
- Preços em aberto por decisão da proprietária.
- Integração Mercado Pago preparada, desativada e sem testes de transações reais.
- Esta publicação no GitHub disponibiliza somente o código. Não publica o site nem conecta um domínio.

## Tecnologias

React, TypeScript, Vinext/Vite e Cloudflare D1. O projeto foi iniciado com o starter do Sites. Preserve os arquivos em `build/`, `scripts/` e `.openai/` para continuar usando essa plataforma. A aplicação usa servidor e banco de dados; não funciona integralmente como um site estático no GitHub Pages.

## Executar localmente

Requer Node.js 22.13 ou superior.

```sh
npm run install:ci
npm run build
npx wrangler d1 execute DB --local --config dist/server/wrangler.json --file drizzle/0000_hard_zombie.sql
npm run dev -- --host 127.0.0.1 --port 5173
```

Aplique a migração uma vez em um banco novo. Para servir a compilação de produção localmente, use `npm run start`. A configuração de ambiente depende do perfil do Sites; o arquivo `.env.example` documenta as variáveis esperadas, mas não contém segredos.

## Antes de receber pagamentos

Cadastre produtos reais com preços e estoque, configure dados comerciais e entrega, configure os segredos do Mercado Pago no servidor e teste o fluxo completo. Mantenha `STORE_READY=false` até essa validação. Nunca coloque credenciais em arquivos públicos, no navegador ou em commits.

O checkout calcula valores no servidor. A notificação exige verificação da assinatura e consulta do pagamento ao Mercado Pago. A página de retorno não confirma pagamento por parâmetros da URL. Cancelamentos, reembolsos, conciliação e administração de estoque precisam ser concluídos antes da operação comercial.

## Validação

Verificação TypeScript e compilação de produção passaram. Testes locais verificaram catálogo sem valores, isolamento de sacolas, inclusão e remoção, validação de quantidades e bloqueio do checkout sem configuração. Não houve cobrança nem teste com pagamentos reais.

## Fotografias

As fotos são ilustrativas e não representam itens confirmados para venda.

- [Vestido — StockSnap, Valeria Boltneva](https://stocksnap.io/photo/woman-dress-KDQ60E3BPD): CC0, arquivo local.
- [Blusa — Unsplash](https://unsplash.com/photos/a-womans-hand-holding-onto-a-white-blouse-sbGRrZogFvQ): licença Unsplash, carregamento por URL.
- [Perfume — Unsplash](https://unsplash.com/photos/gold-perfume-bottle-on-white-textile-a5917t2ea8I): licença Unsplash, carregamento por URL. Não identifica uma fragrância árabe específica.

Arquivos do starter e dependências mantêm suas respectivas licenças. Não foi atribuída uma licença de distribuição ao código personalizado da loja.
