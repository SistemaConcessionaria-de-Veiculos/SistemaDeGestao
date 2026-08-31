# Sistema de Gestão de Concessionária

Sistema web desenvolvido como atividade prática da disciplina de Engenharia de Software, com o objetivo de apoiar o gerenciamento de uma concessionária de veículos.

A aplicação possui frontend em Angular, backend em Spring Boot, autenticação baseada em JWT e persistência de dados. O sistema também está disponível em ambiente de produção no Render.

## Aplicação em produção

- Frontend: https://concessionaria-frontend-bev3.onrender.com
- Backend: https://concessionaria-backend-bqlh.onrender.com

> Os serviços utilizam o plano gratuito do Render e podem levar alguns segundos para responder após um período de inatividade.

## Funcionalidades

Entre as principais funcionalidades implementadas estão:

### Usuários e autenticação

- cadastro de usuários;
- autenticação de usuários;
- controle de acesso utilizando JWT;
- proteção das rotas da aplicação;
- encerramento de sessão.

### Clientes

- cadastro de clientes;
- consulta e pesquisa de clientes;
- visualização dos detalhes de clientes;
- edição de clientes;
- consulta do histórico de compras do cliente.

### Veículos

- cadastro de veículos;
- consulta e pesquisa de veículos;
- edição de veículos;
- controle do status do veículo;
- atualização automática do status do veículo após a realização de uma venda;
- bloqueio da alteração manual do status de veículos já vendidos.

### Vendas

- registro de vendas;
- consulta e pesquisa de vendas;
- visualização dos detalhes de vendas;
- associação da venda ao cliente e ao veículo;
- atualização do estoque após o registro da venda.

### Relatório de desempenho de vendas — US13

A aplicação disponibiliza um relatório gerencial consolidado para acompanhamento das vendas realizadas.

A consulta permite utilizar:

- ano obrigatório;
- semestre opcional;
- marca opcional.

Entre os indicadores apresentados estão:

- quantidade total de vendas;
- valor total das vendas;
- ticket médio;
- vendas agrupadas por marca;
- vendas agrupadas por modelo;
- modelos mais vendidos;
- modelos menos vendidos.

A tela também possui tratamento para:

- carregamento dos dados;
- filtros inválidos;
- sessão inválida;
- acesso não autorizado;
- falha de conexão;
- períodos sem vendas.

### Acompanhamento do estoque — US14

A aplicação também disponibiliza uma visão consolidada do estoque de veículos.

A consulta permite utilizar:

- marca opcional;
- status opcional.

Entre os indicadores apresentados estão:

- quantidade total de veículos;
- quantidade disponível;
- quantidade indisponível;
- percentual de disponibilidade;
- valor total dos veículos disponíveis;
- distribuição por marca;
- distribuição por modelo;
- distribuição por faixa de preço.

A tela também possui tratamento para:

- carregamento dos dados;
- filtros inválidos;
- sessão inválida;
- acesso não autorizado;
- falha de conexão;
- estoque sem resultados.

A funcionalidade é somente de consulta e não altera diretamente o status dos veículos.

## Tecnologias utilizadas

### Backend

- Java 21
- Spring Boot 3.2.5
- Spring Web
- Spring Data JPA
- Hibernate
- Spring Security
- JWT
- Maven
- JaCoCo

### Frontend

- Angular 22
- TypeScript
- RxJS
- Angular Router
- Angular Forms
- Vitest
- npm

### Banco de dados

- MySQL 8 para desenvolvimento local e testes
- PostgreSQL para o ambiente de produção

### Infraestrutura

- Docker
- Nginx
- Render
- GitHub Actions
- Git
- GitHub
- SonarQube Cloud

## Integrantes do grupo

### Laysa Beatriz do Nascimento Beserra

- Matrícula: 200751129
- GitHub: @laysabeatriizz
- E-mail: laysa.beatriz@ufape.edu.br

### Ricardo Matias de Lima

- Matrícula: 200751121
- GitHub: @RicardoMatiassl
- E-mail: ricardo.matias@ufape.edu.br

### Luana Siqueira de Sousa

- Matrícula: XXXXXX
- GitHub: @LuanaSiqueira-1
- E-mail: luana.siqueira@ufape.edu.br

### Riana de Queiroz Tenorio Vaz

- Matrícula: XXXXXX
- GitHub: @riannavaz
- E-mail: rianna.vaz@ufape.edu.br

## Estrutura do projeto

O repositório está dividido principalmente em duas aplicações:

```text
SistemaDeGestao/
├── .github/
│   └── workflows/
├── backend/
├── frontend/
├── .gitignore
└── README.md
```

- `backend/`: aplicação Spring Boot, regras de negócio, segurança, APIs e acesso aos bancos de dados;
- `frontend/`: aplicação Angular;
- `.github/workflows/`: pipelines de integração contínua do frontend, backend e análise de qualidade.

## Pré-requisitos para execução local

Antes de executar o projeto localmente, é necessário possuir:

- Java 21
- Node.js
- npm
- MySQL 8
- Git

O Docker também pode ser utilizado para execução do banco de dados e criação das imagens das aplicações.

## Banco de dados local

No ambiente de desenvolvimento e testes, o backend utiliza MySQL 8.

As configurações de acesso ao banco devem ser definidas por meio da configuração da aplicação ou de variáveis de ambiente.

Credenciais e outros dados sensíveis não devem ser adicionados ao repositório.

Exemplo de variáveis utilizadas no ambiente local:

```text
SPRING_DATASOURCE_URL
SPRING_DATASOURCE_USERNAME
SPRING_DATASOURCE_PASSWORD
```

## Executando o backend localmente

A partir da raiz do repositório:

```powershell
cd backend
.\mvnw.cmd spring-boot:run
```

Por padrão, o backend local é acessado em:

```text
http://localhost:8080
```

## Executando o frontend localmente

Em outro terminal, a partir da raiz do repositório:

```powershell
cd frontend
npm ci
npm start
```

O frontend de desenvolvimento é acessado em:

```text
http://localhost:4200
```

Durante o desenvolvimento local, o frontend utiliza a API configurada para o ambiente correspondente.

## Build do frontend

Para gerar o build de produção do Angular:

```powershell
cd frontend
npm run build
```

Os arquivos gerados para execução em produção são servidos pelo Nginx no container do frontend.

## Testes do frontend

Os testes podem ser executados com:

```powershell
cd frontend
npm test -- --no-watch --no-progress
```

Na validação final da Sexta Iteração, a suíte do frontend executou:

```text
40 testes
40 aprovados
```

O pipeline do frontend também executa automaticamente os testes e o build da aplicação.

## Testes e cobertura do backend

O backend utiliza Maven e JaCoCo para execução de testes e geração das informações de cobertura.

Para executar a verificação completa do backend com o profile de testes:

```powershell
cd backend
.\mvnw.cmd clean verify "-Dspring.profiles.active=test"
```

O ambiente de testes utiliza MySQL.

Na validação final da Sexta Iteração, a suíte do backend executou:

```text
107 testes
107 aprovados
0 falhas
0 erros
```

A verificação do JaCoCo também foi concluída com sucesso, atendendo aos limites definidos pelo projeto.

## Critérios de cobertura

Na Sexta Iteração foram adotados os seguintes critérios mínimos:

- cobertura de instruções: pelo menos 70%;
- cobertura de branches: pelo menos 80%.

O Maven utiliza o JaCoCo para impedir que a verificação seja concluída com sucesso quando os limites configurados não são atendidos.

## Qualidade de código

O projeto utiliza SonarQube Cloud para análise estática de qualidade.

A análise inclui, entre outros pontos:

- segurança;
- confiabilidade;
- manutenibilidade;
- duplicação de código;
- cobertura;
- análise do código novo.

A análise final da branch `main` da Sexta Iteração apresentou Quality Gate aprovado.

## Integração contínua

O projeto possui pipelines do GitHub Actions para frontend, backend e análise de qualidade.

### Frontend CI

O workflow do frontend executa:

1. checkout do código;
2. configuração do Node.js;
3. instalação das dependências com `npm ci`;
4. execução dos testes;
5. build da aplicação Angular.

O workflow é executado em pushes e pull requests direcionados à branch `main`.

### Backend CI

O workflow do backend executa:

1. checkout do código;
2. inicialização de um serviço MySQL 8 para os testes;
3. configuração do Java 21;
4. execução do Maven;
5. testes automatizados;
6. geração de cobertura com JaCoCo.

### Análise de qualidade

O projeto também possui integração com SonarQube Cloud.

A análise é executada sobre o código integrado e utiliza as informações produzidas pelo projeto, incluindo cobertura de testes.

## Docker

As duas partes da aplicação possuem configuração própria para Docker.

### Backend

O backend utiliza uma imagem com Java 21.

O processo é dividido em duas etapas:

1. compilação da aplicação com Maven;
2. execução do arquivo JAR utilizando uma imagem JRE.

A aplicação expõe a porta `8080`.

### Frontend

O frontend utiliza um build em múltiplas etapas:

1. compilação da aplicação Angular utilizando Node.js;
2. disponibilização dos arquivos estáticos utilizando Nginx.

O Nginx também está configurado para permitir o funcionamento das rotas da SPA, redirecionando as rotas da aplicação para o `index.html` quando necessário.

## Ambiente de produção

A aplicação foi publicada no Render utilizando serviços separados para frontend, backend e banco de dados.

### Frontend

O frontend Angular é compilado dentro de um container Docker e servido pelo Nginx.

URL:

```text
https://concessionaria-frontend-bev3.onrender.com
```

### Backend

O backend Spring Boot é executado em um container Docker no Render.

URL:

```text
https://concessionaria-backend-bqlh.onrender.com
```

### Banco de dados

No ambiente de produção é utilizado PostgreSQL.

O backend utiliza um profile específico de produção e recebe os dados de conexão por meio de variáveis de ambiente.

## Variáveis de ambiente de produção

O backend utiliza as seguintes variáveis no ambiente de produção:

```text
PORT
DB_URL
DB_USERNAME
DB_PASSWORD
JWT_SECRET
FRONTEND_URL
```

Nenhum valor sensível dessas variáveis deve ser armazenado diretamente no repositório.

O profile de produção pode ser ativado com:

```text
SPRING_PROFILES_ACTIVE=prod
```

## Integração entre frontend e backend

O frontend utiliza configurações específicas de ambiente para acessar a API.

Em desenvolvimento, o backend normalmente é disponibilizado em:

```text
http://localhost:8080
```

Em produção, a aplicação utiliza:

```text
https://concessionaria-backend-bqlh.onrender.com
```

O backend possui configuração de CORS para aceitar requisições da origem definida pela variável:

```text
FRONTEND_URL
```

No ambiente publicado, essa variável corresponde ao endereço do frontend no Render.

## Segurança

A aplicação utiliza Spring Security e autenticação baseada em JWT.

Após uma autenticação válida, o frontend utiliza o token recebido para acessar as rotas protegidas da API.

O frontend possui guardas de rota e interceptor HTTP para integração com a autenticação.

As novas funcionalidades da Sexta Iteração também respeitam a política de autenticação da aplicação.

As configurações sensíveis utilizadas na geração e validação dos tokens são fornecidas por variáveis de ambiente no ambiente de produção.

## Histórico das funcionalidades recentes

### Quinta Iteração

A Quinta Iteração adicionou e consolidou funcionalidades relacionadas a:

- edição de veículo;
- edição de cliente;
- consulta do histórico de compras do cliente;
- autenticação e autorização;
- integração frontend/backend;
- testes automatizados;
- cobertura;
- análise de qualidade.

### Sexta Iteração

A Sexta Iteração adicionou duas funcionalidades gerenciais principais.

#### US13 — Relatório de desempenho de vendas

Permite acompanhar indicadores consolidados das vendas utilizando os dados registrados no sistema.

Principais recursos:

- filtro por ano;
- filtro opcional por semestre;
- filtro opcional por marca;
- quantidade vendida;
- valor total;
- ticket médio;
- vendas por marca;
- vendas por modelo;
- ranking de mais vendidos;
- ranking de menos vendidos;
- estados de carregamento, erro e ausência de vendas.

#### US14 — Acompanhamento do estoque

Permite acompanhar a situação consolidada dos veículos cadastrados.

Principais recursos:

- filtro por marca;
- filtro por status;
- total de veículos;
- disponíveis;
- indisponíveis;
- percentual disponível;
- valor total disponível;
- distribuição por marca;
- distribuição por modelo;
- distribuição por faixa de preço;
- estados de carregamento, erro e estoque vazio.

## Validação funcional

Durante o desenvolvimento foram realizados testes manuais dos principais fluxos da aplicação.

Entre os fluxos validados estão:

- cadastro de usuário;
- login;
- logout;
- acesso às áreas protegidas;
- cadastro de cliente;
- consulta de clientes;
- visualização de detalhes do cliente;
- edição de cliente;
- histórico de compras do cliente;
- cadastro de veículo;
- consulta de veículos;
- edição de veículo;
- registro de venda;
- consulta de vendas;
- visualização dos detalhes da venda;
- relatório de desempenho de vendas;
- filtro de relatório por semestre;
- filtro de relatório por marca;
- relatório sem vendas no período;
- acompanhamento do estoque;
- filtro de estoque por marca;
- filtro de estoque por status;
- estoque sem resultados;
- integração entre relatório, vendas e estoque.

Os testes confirmaram a comunicação entre:

```text
Frontend Angular
        ↓
Backend Spring Boot
        ↓
Banco de dados
```

## Fluxo de desenvolvimento

O desenvolvimento do projeto utiliza Git e GitHub com trabalho realizado em branches e integração por pull requests.

O fluxo adotado consiste, de forma geral, em:

1. criação ou atualização da branch de trabalho;
2. implementação da tarefa;
3. testes locais;
4. commit das alterações;
5. push da branch;
6. abertura de pull request;
7. revisão;
8. merge na branch `main`;
9. execução dos workflows de integração contínua;
10. análise de qualidade;
11. validação funcional;
12. publicação de uma nova release.

## Status da aplicação

A aplicação encontra-se integrada e funcional, com frontend, backend e banco de dados comunicando-se corretamente.

As funcionalidades da Sexta Iteração estão integradas às funcionalidades já existentes, com relatório de desempenho de vendas e acompanhamento do estoque disponíveis para usuários autenticados.