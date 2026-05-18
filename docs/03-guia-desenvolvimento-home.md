# 03 - Guia para desenvolver a nova Home

Este documento serve como roteiro completo para montar a Home atual do projeto `AppExemplo`, com a estrutura Razor e o CSS usados na pagina inicial.

## Objetivo

Ao final da implementacao, a Home deve ficar com:

- um banner principal com titulo, subtitulo e texto de apresentacao;
- tres cards de destaque para `Minha historia`, `Meu curriculo` e `Entre em contato`;
- layout centralizado e responsivo;
- rodape mantido no layout principal;
- estilos organizados no CSS global da aplicacao.

## Arquivos usados nesta etapa

### `Components/Pages/Home.razor`

Arquivo responsavel pela estrutura da pagina inicial.

### `wwwroot/app.css`

Arquivo responsavel pelos estilos globais da Home.

### `Components/Layout/MainLayout.razor`

Arquivo do layout principal. Ele ja contem o `@Body` e o rodape da aplicacao.

### `Components/Layout/MainLayout.razor.css`

Arquivo com os estilos do layout principal e do bloco de erro do Blazor.

## Estrutura final esperada

Depois desta etapa, a Home deve seguir esta organizacao:

```text
pagina-inicial
├── secao-banner
│   └── banner-principal
│       ├── subtitulo-banner
│       ├── titulo-banner
│       └── texto-banner
└── secao-destaques
    ├── cartao-destaque cartao-claro
    ├── cartao-destaque cartao-escuro
    └── cartao-destaque cartao-destaque-contato
```

## 1. Criar a estrutura base da pagina

Abra o arquivo:

```text
Components/Pages/Home.razor
```

Adicione a rota da pagina e o titulo exibido na aba do navegador:

```razor
@page "/"

<PageTitle>Home</PageTitle>
```

Em seguida, crie o container principal da Home:

```razor
<section class="pagina-inicial">
</section>
```

Esse bloco sera o wrapper da pagina e servira para controlar fundo, espacamento e altura minima.

## 2. Montar o banner principal

Dentro de `.pagina-inicial`, adicione a secao do banner:

```razor
<section class="secao-banner">
    <div class="banner-principal">
        <p class="subtitulo-banner">Portifolio do Joao</p>
        <h1 class="titulo-banner">Bem-vindo ao meu espaco pessoal</h1>
        <p class="texto-banner">
            Aqui voce encontra um resumo da minha historia, do meu curriculo e das formas de contato.
        </p>
    </div>
</section>
```

Esse banner concentra a primeira mensagem da pagina e deve funcionar como o ponto de entrada visual da Home.

## 3. Adicionar a secao de destaques

Logo abaixo do banner, adicione os tres cards principais:

```razor
<section class="secao-destaques" id="destaques" aria-label="Destaques do site">
    <article class="cartao-destaque cartao-claro">
        <span class="numero-destaque">01</span>
        <h2>Minha historia</h2>
        <p>Apresente sua trajetoria com uma narrativa curta, segura e facil de escanear.</p>
        <a href="#">Conhecer percurso</a>
    </article>

    <article class="cartao-destaque cartao-escuro">
        <span class="numero-destaque">02</span>
        <h2>Meu curriculo</h2>
        <p>Destaque competencias, experiencia e resultados com uma hierarquia visual mais forte.</p>
        <a href="#">Ver experiencias</a>
    </article>

    <article class="cartao-destaque cartao-destaque-contato" id="contato">
        <span class="numero-destaque">03</span>
        <h2>Entre em contato</h2>
        <p>Abra um caminho direto para conversa, parceria ou oportunidade profissional.</p>
        <a href="#">Iniciar conversa</a>
    </article>
</section>
```

Cada `<article>` representa um bloco de destaque independente. Essa estrutura facilita trocar texto, cor, link e ordem dos cards sem alterar o restante da pagina.

## 4. Resultado completo do arquivo `Home.razor`

Ao final, o arquivo deve ficar assim:

```razor
@page "/"

<PageTitle>Home</PageTitle>

<section class="pagina-inicial">
    <section class="secao-banner">
        <div class="banner-principal">
            <p class="subtitulo-banner">Portifolio do Joao</p>
            <h1 class="titulo-banner">Bem-vindo ao meu espaco pessoal</h1>
            <p class="texto-banner">
                Aqui voce encontra um resumo da minha historia, do meu curriculo e das formas de contato.
            </p>
        </div>
    </section>

    <section class="secao-destaques" id="destaques" aria-label="Destaques do site">
        <article class="cartao-destaque cartao-claro">
            <span class="numero-destaque">01</span>
            <h2>Minha historia</h2>
            <p>Apresente sua trajetoria com uma narrativa curta, segura e facil de escanear.</p>
            <a href="#">Conhecer percurso</a>
        </article>

        <article class="cartao-destaque cartao-escuro">
            <span class="numero-destaque">02</span>
            <h2>Meu curriculo</h2>
            <p>Destaque competencias, experiencia e resultados com uma hierarquia visual mais forte.</p>
            <a href="#">Ver experiencias</a>
        </article>

        <article class="cartao-destaque cartao-destaque-contato" id="contato">
            <span class="numero-destaque">03</span>
            <h2>Entre em contato</h2>
            <p>Abra um caminho direto para conversa, parceria ou oportunidade profissional.</p>
            <a href="#">Iniciar conversa</a>
        </article>
    </section>
</section>
```

## 5. Adicionar o CSS base da Home

Abra o arquivo:

```text
wwwroot/app.css
```

Comece definindo o fundo global da aplicacao e o wrapper da Home:

```css
html,
body {
  background: #f8fafc;
  font-family: "Segoe UI", "Helvetica Neue", Arial, sans-serif;
  margin: 0;
}

.pagina-inicial {
  background: #f8fafc;
  color: #1e293b;
  min-height: 100vh;
  padding: 2rem 1.5rem 4rem;
}

.secao-banner,
.secao-destaques {
  margin: 0 auto;
  max-width: 1100px;
}
```

Essas regras garantem uma largura controlada para o conteudo e uma leitura mais confortavel em telas grandes.

## 6. Estilizar o banner

Adicione as regras abaixo para o topo da pagina:

```css
.secao-banner {
  padding: 1.5rem 0 2rem;
}

.banner-principal {
  background: linear-gradient(135deg, #1d4ed8, #0f172a);
  border-radius: 20px;
  color: #f8fafc;
  padding: 2rem;
  text-align: center;
}

.subtitulo-banner,
.numero-destaque {
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.subtitulo-banner {
  color: #bfdbfe;
  margin: 0 0 0.75rem;
}

.titulo-banner {
  font-family: "Georgia", "Times New Roman", serif;
  font-size: clamp(2rem, 4vw, 3rem);
  margin: 0;
}

.texto-banner {
  line-height: 1.6;
  margin: 1rem auto 0;
  max-width: 38rem;
}
```

Esse conjunto cria contraste forte, destaque tipografico e limita a largura do texto para nao prejudicar a leitura.

## 7. Estilizar os cards de destaque

Depois do CSS do banner, adicione o grid e os estilos dos cards:

```css
.secao-destaques {
  display: grid;
  gap: 1rem;
  grid-template-columns: repeat(3, minmax(0, 1fr));
}

.cartao-destaque {
  background: #ffffff;
  border: 1px solid #dbe4f0;
  border-radius: 16px;
  box-shadow: 0 10px 24px rgba(15, 23, 42, 0.06);
  padding: 1.5rem;
}

.cartao-claro {
  background: #ffffff;
}

.cartao-escuro {
  background: #1e293b;
  color: #f8fafc;
}

.cartao-destaque-contato {
  background: #fff7ed;
}

.numero-destaque {
  color: #2563eb;
  display: inline-block;
  margin-bottom: 1.25rem;
}

.cartao-destaque h2 {
  font-family: "Georgia", "Times New Roman", serif;
  font-size: 1.7rem;
  margin: 0 0 0.75rem;
}

.cartao-destaque p {
  line-height: 1.65;
  margin: 0 0 1.25rem;
}

.cartao-destaque a {
  color: inherit;
  font-weight: 700;
  text-decoration: none;
}

.cartao-destaque a:hover,
.cartao-destaque a:focus {
  text-decoration: underline;
}
```

Use `.cartao-destaque` para as regras compartilhadas e classes extras para variacoes de cor.

## 8. Adicionar responsividade

Para que a Home funcione em telas menores, adicione estas regras no final do `app.css`:

```css
@media (max-width: 900px) {
  .secao-destaques {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .pagina-inicial {
    padding: 1rem 1rem 3rem;
  }

  .banner-principal,
  .cartao-destaque {
    border-radius: 14px;
  }

  .banner-principal {
    padding: 1.5rem;
  }
}
```

Com isso, os tres cards deixam de ficar lado a lado em telas menores e passam a empilhar verticalmente.

## 9. Resultado completo do arquivo `app.css`

O trecho da Home no CSS deve ficar assim:

```css
html,
body {
  background: #f8fafc;
  font-family: "Segoe UI", "Helvetica Neue", Arial, sans-serif;
  margin: 0;
}

.pagina-inicial {
  background: #f8fafc;
  color: #1e293b;
  min-height: 100vh;
  padding: 2rem 1.5rem 4rem;
}

.secao-banner,
.secao-destaques {
  margin: 0 auto;
  max-width: 1100px;
}

.secao-banner {
  padding: 1.5rem 0 2rem;
}

.banner-principal {
  background: linear-gradient(135deg, #1d4ed8, #0f172a);
  border-radius: 20px;
  color: #f8fafc;
  padding: 2rem;
  text-align: center;
}

.subtitulo-banner,
.numero-destaque {
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.subtitulo-banner {
  color: #bfdbfe;
  margin: 0 0 0.75rem;
}

.titulo-banner {
  font-family: "Georgia", "Times New Roman", serif;
  font-size: clamp(2rem, 4vw, 3rem);
  margin: 0;
}

.texto-banner {
  line-height: 1.6;
  margin: 1rem auto 0;
  max-width: 38rem;
}

.secao-destaques {
  display: grid;
  gap: 1rem;
  grid-template-columns: repeat(3, minmax(0, 1fr));
}

.cartao-destaque {
  background: #ffffff;
  border: 1px solid #dbe4f0;
  border-radius: 16px;
  box-shadow: 0 10px 24px rgba(15, 23, 42, 0.06);
  padding: 1.5rem;
}

.cartao-claro {
  background: #ffffff;
}

.cartao-escuro {
  background: #1e293b;
  color: #f8fafc;
}

.cartao-destaque-contato {
  background: #fff7ed;
}

.numero-destaque {
  color: #2563eb;
  display: inline-block;
  margin-bottom: 1.25rem;
}

.cartao-destaque h2 {
  font-family: "Georgia", "Times New Roman", serif;
  font-size: 1.7rem;
  margin: 0 0 0.75rem;
}

.cartao-destaque p {
  line-height: 1.65;
  margin: 0 0 1.25rem;
}

.cartao-destaque a {
  color: inherit;
  font-weight: 700;
  text-decoration: none;
}

.cartao-destaque a:hover,
.cartao-destaque a:focus {
  text-decoration: underline;
}

@media (max-width: 900px) {
  .secao-destaques {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .pagina-inicial {
    padding: 1rem 1rem 3rem;
  }

  .banner-principal,
  .cartao-destaque {
    border-radius: 14px;
  }

  .banner-principal {
    padding: 1.5rem;
  }
}
```

## 10. O que fica no layout e o que fica na Home

Mantenha no layout principal apenas a estrutura compartilhada da aplicacao.

No arquivo `Components/Layout/MainLayout.razor`, o projeto ja possui:

```razor
<div class="app-shell">
    <main class="app-content">
        @Body
    </main>

    <footer class="app-footer">
        <span>AppExemplo</span>
        <span>Autor: Joao Jr</span>
    </footer>
</div>
```

Ou seja:

- o conteudo da Home deve continuar em `Home.razor`;
- o rodape deve permanecer no layout;
- o bloco `#blazor-error-ui` deve ser preservado;
- estilos do rodape continuam em `MainLayout.razor.css`.

## 11. Como fazer alteracoes futuras

Para alterar a Home depois desta implementacao:

1. Edite o conteudo textual no `Home.razor`.
2. Edite cores, espacamentos e tipografia no `wwwroot/app.css`.
3. Se criar nova secao com grid ou colunas, adicione tambem uma regra responsiva.
4. Evite mover conteudo da Home para `MainLayout.razor`.

Exemplo de nova secao:

```razor
<section class="secao-projetos" id="projetos">
    <h2>Projetos</h2>
    <p>Projetos em destaque desenvolvidos durante minha trajetoria.</p>
</section>
```

CSS correspondente:

```css
.secao-projetos {
  margin: 0 auto;
  max-width: 1100px;
  padding: 2rem 0;
}
```

## 12. Validar o resultado

Depois das alteracoes, valide com:

```bash
dotnet build
```

Se estiver usando recarga automatica durante o desenvolvimento, tambem pode executar:

```bash
dotnet watch
```

## Resultado final

Com essas etapas, a Home passa a ter uma implementacao completa, documentada e facil de manter, com o HTML/Razor da pagina separado do layout principal e com todo o CSS necessario para banner, cards e responsividade.

````

## Regras de organizacao

Siga estas regras ao evoluir a Home:

- mantenha estrutura da pagina em `Home.razor`;
- mantenha estilos visuais da Home em `wwwroot/app.css`;
- mantenha estilos gerais de layout em `MainLayout.razor.css`;
- nao recrie o menu lateral padrao do template;
- nao recrie as paginas `Counter` e `Weather`;
- nao remova o bloco `#blazor-error-ui`;
- use textos curtos nos cards;
- use nomes de classes descritivos;
- mantenha a responsividade para telas menores.

## Checklist antes de finalizar

Antes de considerar a Home pronta, confira:

- o banner aparece no topo;
- os tres cards aparecem abaixo do banner;
- os textos nao estouram em telas pequenas;
- os links possuem `href` definido;
- o rodape continua aparecendo;
- o projeto compila sem erros.

## Validacao

Execute:

```bash
dotnet build
````

O resultado esperado e:

```text
Compilacao com exito.
0 Aviso(s)
0 Erro(s)
```
