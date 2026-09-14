# Meu Glossário

Glossário pessoal de termos de desenvolvimento, banco de dados, infraestrutura e
web — anotados à medida que aparecem, em português, com exemplos concretos em
vez de definições de dicionário.

**Página:** https://danguibes.github.io/meuglossario/

## Como é feito

Um único `index.html`, escrito à mão. **Sem build**: o arquivo do repositório é
exatamente o arquivo que o navegador recebe — sem `npm`, sem `node_modules/`,
sem `dist/`, sem etapa nenhuma entre editar e ver. Publicado pelo GitHub Pages
direto da branch `main`.

Essa escolha é deliberada e está explicada no próprio glossário, no verbete
[Build](https://danguibes.github.io/meuglossario/#build): ferramenta de build só
se paga quando há muitos arquivos e dependências para resolver. Uma página de
conteúdo não ganha nada com bundle ou minificação, e passaria a ter dependências
que envelhecem.

## O que a página faz

- **Busca** que filtra os verbetes enquanto você digita (ignora acento; tecle `/`
  para focar o campo, `Esc` para limpar).
- **Filtro por seção**, nas pílulas abaixo da busca.
- **Links cruzados**: quando um verbete precisa de outro para ser entendido, o
  termo leva direto a ele. Se o destino estiver escondido por um filtro, o
  filtro é limpo automaticamente.
- **Classe do verbete** — `ling.`, `prot.`, `ferr.`, `conc.`… — no lugar do
  `s.m.`/`adj.` dos dicionários. A legenda está no topo da página.
- **Sentidos múltiplos**: quando a mesma palavra significa coisas diferentes
  conforme o contexto, o verbete traz o selo `2 sentidos` e lista os dois lado a
  lado — `CSR` (renderização / certificado), `token` (segurança / IA),
  `worker` (três sentidos, um deles o oposto do outro), `commit`, `branch`,
  `handshake`, `padding`, `hook`, `delta`, `REST`.
- **Tema claro e escuro**, seguindo a preferência do sistema, com botão para
  forçar um dos dois.
- Cada verbete tem **âncora própria** (`#parquet`, `#mtls`), então dá para
  mandar o link de um termo específico.

## Como editar

Abra o `index.html` e acrescente um `<article>` na seção correspondente:

```html
<article class="e" id="slug-do-termo" data-s="rede">
  <h3><a class="self" href="#slug-do-termo">Termo</a> <span class="t">prot.</span></h3>
  <p>Explicação, com <a class="x" href="#outro-termo">links cruzados</a>.</p>
</article>
```

Três convenções:

- `id` e `data-s` são obrigatórios — o `data-s` precisa bater com o da `<section>`.
- Link para outro verbete usa `class="x"`; o link do próprio título usa `class="self"`.
- A busca e as pílulas se montam sozinhas a partir do HTML. Não há lista de
  termos em JavaScript para manter em sincronia.

Para conferir antes de publicar, basta abrir o arquivo no navegador.
