# Painel de Estoque Nouê — como publicar (2 minutos)

Este painel usa um **banco de dados próprio da Nouê (Supabase)**. Tudo que a equipe
editar fica salvo no banco e aparece ao vivo para todos — não depende mais do
armazenamento do artifact.

## O que já está pronto
- Banco Supabase (projeto **Nouê Cosméticos**), tabela `painel_estoque`, 67 SKUs carregados.
- Segurança (RLS) e tempo real ligados.
- O arquivo `index.html` já aponta para esse banco.

## Publicar na Vercel (jeito mais rápido — arrastar)
1. Entre em https://vercel.com (conta/time **noue**).
2. **Add New… → Project → Deploy** (ou a área de deploy manual).
3. Arraste a pasta que contém o `index.html` (ou só o arquivo).
4. Framework: **Other / Static**. Clique em **Deploy**.
5. Em segundos sai uma URL pública tipo `https://painel-estoque-noue.vercel.app`.
   Compartilhe essa URL com o time — todo mundo edita e salva no mesmo banco.

## Alternativa (GitHub)
Suba `index.html` num repositório e conecte na Vercel (deploy automático a cada push).

## Como o time usa
- Abre a URL, digita o **nome** no campo "Quem está editando".
- Edita qualquer número; vê **"✅ salvo"** na hora. Ao atualizar a página, continua lá.
- Para dar baixa quando a mercadoria chega: aba **Estoque & chegadas** (subir CSV do WMS
  ou lançar a entrada, marcando "dar baixa na necessidade").

## Segurança
A chave usada é a **chave pública (anon)** do Supabase — é feita para rodar no navegador.
A proteção é a regra de acesso (RLS), que libera leitura/escrita **apenas** na tabela
`painel_estoque`. Quem tiver a URL consegue editar. Para uma operação interna está ok;
se quiser travar por login depois, dá para adicionar Supabase Auth.
