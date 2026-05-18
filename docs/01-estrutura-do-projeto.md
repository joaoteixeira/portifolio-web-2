# 01 - Estrutura de pastas e arquivos do projeto

Este documento explica a organizacao inicial do projeto `AppExemplo`, que e uma aplicacao web criada com ASP.NET Core Blazor usando .NET 9.

## Visao geral

```text
AppExemplo/
├── AppExemplo.csproj
├── AppExemplo.sln
├── Program.cs
├── appsettings.json
├── appsettings.Development.json
├── Components/
│   ├── App.razor
│   ├── Routes.razor
│   ├── _Imports.razor
│   ├── Layout/
│   └── Pages/
├── Properties/
│   └── launchSettings.json
├── wwwroot/
│   ├── app.css
│   ├── favicon.png
│   └── lib/
├── bin/   (gerado pelo build)
└── obj/   (gerado pelo build)
```

## Arquivos da raiz

### `AppExemplo.sln`

Arquivo de solucao do Visual Studio/.NET. Ele agrupa um ou mais projetos e facilita abrir, compilar e gerenciar a aplicacao em ferramentas como Visual Studio, Rider ou pela CLI do .NET.

### `AppExemplo.csproj`

Arquivo de projeto da aplicacao. Define configuracoes importantes de build, como:

- SDK usado pelo projeto: `Microsoft.NET.Sdk.Web`
- Framework alvo: `net9.0`
- Uso de nullable reference types: `Nullable` habilitado
- Imports implicitos do .NET: `ImplicitUsings` habilitado

### `Program.cs`

Ponto de entrada da aplicacao. E nele que a aplicacao web e configurada e iniciada.

As principais responsabilidades deste arquivo sao:

- Criar o builder da aplicacao.
- Registrar os servicos de Razor Components.
- Habilitar componentes interativos no servidor.
- Configurar tratamento de erros e HSTS fora do ambiente de desenvolvimento.
- Habilitar redirecionamento HTTPS.
- Habilitar antiforgery.
- Mapear arquivos estaticos.
- Mapear o componente raiz `App`.
- Iniciar a aplicacao com `app.Run()`.

### `appsettings.json`

Arquivo de configuracoes gerais da aplicacao. Normalmente guarda configuracoes compartilhadas entre ambientes, como connection strings, parametros de logging e outras opcoes da aplicacao.

### `appsettings.Development.json`

Arquivo de configuracoes especificas para o ambiente de desenvolvimento. Ele pode sobrescrever valores definidos em `appsettings.json` quando a aplicacao roda em modo `Development`.

### `.gitignore`

Arquivo que informa quais arquivos e pastas devem ficar fora do controle de versao. Neste projeto, ele ignora principalmente artefatos gerados pelo build, como `bin/` e `obj/`, alem de arquivos locais de IDE e sistema operacional.

## Pasta `Components`

Contem os componentes Razor da aplicacao Blazor. Essa e a principal pasta da interface da aplicacao.

### `Components/App.razor`

Componente raiz da aplicacao. Ele define a estrutura HTML base, inclui os arquivos CSS principais, configura o favicon, renderiza as rotas e carrega o script do Blazor.

### `Components/Routes.razor`

Responsavel pelo roteamento da aplicacao. Ele usa o componente `Router` para localizar paginas com rotas definidas e renderiza cada pagina usando o layout padrao `MainLayout`.

### `Components/_Imports.razor`

Arquivo usado para centralizar diretivas comuns aos componentes Razor, como `@using` e outros imports. Isso evita repetir as mesmas diretivas em varios componentes.

### `Components/Layout`

Contem componentes relacionados ao layout visual da aplicacao.

Arquivos principais:

- `MainLayout.razor`: layout principal usado pelas paginas.
- `MainLayout.razor.css`: CSS isolado do layout principal.
- `NavMenu.razor`: menu de navegacao da aplicacao.
- `NavMenu.razor.css`: CSS isolado do menu de navegacao.

### `Components/Pages`

Contem as paginas navegaveis da aplicacao. Cada arquivo `.razor` normalmente representa uma tela ou rota.

Arquivos atuais:

- `Home.razor`: pagina inicial.
- `Error.razor`: pagina usada para exibir erros.

## Pasta `Properties`

Contem configuracoes auxiliares do projeto.

### `Properties/launchSettings.json`

Define perfis de execucao usados durante o desenvolvimento. Esse arquivo costuma informar URLs, portas, variaveis de ambiente e comandos usados por ferramentas como Visual Studio e `dotnet run`.

## Pasta `wwwroot`

Pasta publica da aplicacao. Tudo que fica aqui pode ser servido como arquivo estatico pelo navegador.

Arquivos e pastas principais:

- `app.css`: CSS global da aplicacao.
- `favicon.png`: icone exibido na aba do navegador.
- `lib/`: bibliotecas estaticas de terceiros, como Bootstrap.

## Pastas geradas pelo build

### `bin`

Pasta gerada pela compilacao. Contem os arquivos finais produzidos pelo build, como `.dll`, `.pdb`, arquivos de configuracao copiados e executaveis.

Essa pasta nao deve ser editada manualmente.

### `obj`

Pasta intermediaria usada pelo processo de build do .NET. Contem arquivos temporarios, caches, assets gerados e metadados usados durante compilacao, restauracao de pacotes e publicacao.

Essa pasta tambem nao deve ser editada manualmente.

## Convencao para proximos documentos

A pasta `docs` sera usada para documentar as configuracoes e decisoes tecnicas do projeto. A sugestao e numerar os arquivos para manter uma ordem de leitura, por exemplo:

- `01-estrutura-do-projeto.md`
- `02-configuracoes-do-projeto.md`
- `03-execucao-e-ambientes.md`
