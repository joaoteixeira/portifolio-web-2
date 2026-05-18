# 02 - Remocao dos exemplos iniciais do projeto

Este documento serve como roteiro para remover os exemplos criados automaticamente pelo template inicial do Blazor e deixar o projeto com uma base limpa para desenvolvimento.

## Objetivo

Ao final deste processo, o projeto deve ficar:

- sem as paginas de exemplo `Counter` e `Weather`;
- sem o menu lateral padrao do template;
- sem os estilos padrao do menu e do layout;
- com a Home substituida por uma pagina propria;
- com os estilos de erro do Blazor preservados;
- compilando sem erros.

## 1. Remover as paginas de exemplo

Remova os arquivos abaixo:

```text
Components/Pages/Counter.razor
Components/Pages/Weather.razor
```

Esses arquivos pertencem ao template inicial e demonstram recursos basicos do Blazor, como contador interativo, renderizacao de tabela e carregamento assincrono de dados simulados.

## 2. Remover o menu lateral padrao

Remova o componente de menu:

```text
Components/Layout/NavMenu.razor
```

Tambem remova o CSS isolado desse componente:

```text
Components/Layout/NavMenu.razor.css
```

Antes de remover o arquivo inteiro, este CSS continha classes usadas apenas pelos exemplos iniciais, como:

- `.bi-plus-square-fill-nav-menu`
- `.bi-list-nested-nav-menu`

Como as paginas `Counter` e `Weather` foram removidas, esses icones e links deixam de ser necessarios.

## 3. Simplificar o layout principal

Abra o arquivo:

```text
Components/Layout/MainLayout.razor
```

Remova a estrutura padrao do template:

- `<div class="page">`
- `<div class="sidebar">`
- `<NavMenu />`
- `<main>`
- `<article class="content">`

O layout deve renderizar diretamente o conteudo das paginas usando:

```razor
@Body
```

Mantenha o bloco de erro do Blazor:

```razor
<div id="blazor-error-ui" data-nosnippet>
    An unhandled error has occurred.
    <a href="." class="reload">Reload</a>
    <span class="dismiss">🗙</span>
</div>
```

Se o projeto tiver um rodape fixo com nome da aplicacao e autor, ele pode permanecer no layout.

## 4. Limpar o CSS do layout

Abra o arquivo:

```text
Components/Layout/MainLayout.razor.css
```

Remova os estilos do layout padrao, incluindo regras relacionadas a:

- `.page`
- `main`
- `.sidebar`
- `.content`
- regras responsivas do layout inicial

Nao remova os estilos abaixo, porque eles controlam a exibicao de erros nao tratados pelo Blazor:

```css
#blazor-error-ui {
    color-scheme: light only;
    background: lightyellow;
    bottom: 0;
    box-shadow: 0 -1px 2px rgba(0, 0, 0, 0.2);
    box-sizing: border-box;
    display: none;
    left: 0;
    padding: 0.6rem 1.25rem 0.7rem 1.25rem;
    position: fixed;
    width: 100%;
    z-index: 1000;
}

#blazor-error-ui .dismiss {
    cursor: pointer;
    position: absolute;
    right: 0.75rem;
    top: 0.5rem;
}
```

## 5. Substituir a Home padrao

Abra o arquivo:

```text
Components/Pages/Home.razor
```

Remova o conteudo padrao do template:

```text
Hello, world!
Welcome to your new app.
```

Substitua por uma Home propria do projeto. Neste projeto, a Home foi substituida por:

- um banner principal em largura total;
- uma imagem aleatoria no banner;
- tres circulos centralizados abaixo do banner:
  - `Minha historia`;
  - `Meu Curriculo`;
  - `Entre em Contato`.

Os estilos especificos da Home devem ficar no arquivo:

```text
Components/Pages/Home.razor.css
```

## 6. Conferir a estrutura esperada

Apos a limpeza, a estrutura principal de componentes deve ficar assim:

```text
Components/
├── App.razor
├── Routes.razor
├── _Imports.razor
├── Layout/
│   ├── MainLayout.razor
│   └── MainLayout.razor.css
└── Pages/
    ├── Error.razor
    ├── Home.razor
    └── Home.razor.css
```

## 7. Validar a compilacao

Execute o build do projeto:

```bash
dotnet build
```

O resultado esperado e:

```text
Compilacao com exito.
0 Aviso(s)
0 Erro(s)
```

## Resultado final

Depois desses passos, o projeto continua com a estrutura basica necessaria para executar uma aplicacao Blazor, mas sem as paginas demonstrativas, sem o menu lateral padrao e sem o CSS padrao do layout inicial.
