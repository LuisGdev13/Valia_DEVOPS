# Valia — Global Solution 2026/2

## Sobre o projeto

O Valia é uma plataforma desenvolvida com o objetivo de promover condições de trabalho mais justas, permitindo que trabalhadores registrem e acompanhem suas jornadas, vínculos empregatícios e pagamentos, além de identificar possíveis irregularidades trabalhistas por meio de inteligência artificial.

O projeto busca proporcionar maior transparência, segurança e acesso à informação nas relações de trabalho.

## Objetivo — DevOps

A proposta desta entrega é implementar um ambiente de integração e entrega contínua (CI/CD), utilizando os serviços do Azure DevOps e da Microsoft Azure para automatizar a compilação, execução de testes e implantação da aplicação backend.

## Tecnologias utilizadas

- Java 21
- Spring Boot
- Spring Security e JWT
- Spring AI
- Maven
- Oracle Database
- RabbitMQ
- Ollama
- Swagger
- Azure DevOps
- Azure Boards
- Azure Repos
- Azure Pipelines
- Azure App Service
- Azure CLI
- PowerShell

## Arquitetura Macro

![Arquitetura Macro](docs/arquitetura.png)

A arquitetura proposta utiliza o Azure DevOps para gerenciamento de tarefas, versionamento do código-fonte e automação das etapas de integração e entrega contínua.

A aplicação será hospedada no Azure App Service, utilizando Java 21 e conexão JDBC com o banco de dados Oracle.

## Infraestrutura Azure

| Recurso | Nome | Finalidade |
|---|---|---|
| Resource Group | rg-valia | Organização dos recursos |
| App Service Plan | asp-valia | Ambiente de hospedagem |
| Azure Web App | app-valia | Execução da API Java |
| Oracle Database | Banco externo | Persistência dos dados |
| Service Connection | sc-valia-arm | Integração entre Azure DevOps e Azure |

## Pipeline CI/CD

### Continuous Integration (CI)

A etapa de integração contínua foi planejada para executar automaticamente após a integração das alterações na branch Main.

- Compilação da aplicação com Maven;
- Execução dos testes automatizados;
- Publicação dos resultados dos testes;
- Geração do artefato JAR;
- Publicação do artefato no Azure Pipelines.

### Continuous Delivery (CD)

A etapa de entrega contínua é responsável pela implantação da aplicação no ambiente Azure.

- Download do artefato publicado na etapa de CI;
- Autenticação na Azure por meio da Service Connection;
- Deploy da aplicação no Azure App Service.

## Estratégia de versionamento

O projeto utiliza Git e Azure Repos para gerenciamento do código-fonte.

O fluxo de desenvolvimento proposto consiste em:

1. Criação de uma tarefa no Azure Boards;
2. Criação de uma branch de desenvolvimento;
3. Desenvolvimento e realização de commits;
4. Abertura de um Pull Request;
5. Revisão e aprovação das alterações;
6. Integração na branch Main;
7. Execução automática da pipeline CI/CD.

## Estrutura do projeto

- `/src` — Código-fonte da aplicação Java.
- `/scripts` — Scripts de provisionamento da infraestrutura e banco de dados.
- `/docs` — Documentação e arquitetura macro.
- `pom.xml` — Dependências e configurações Maven.
- `docker-compose.yml` — Ambiente de desenvolvimento local.
- `azure-pipeline.yml` — Configuração da pipeline CI/CD.
- `README.md` — Documentação do projeto.

## Como executar localmente

### Pré-requisitos

- Java JDK 21;
- Maven;
- Oracle Database;
- RabbitMQ;
- Docker, caso seja utilizado o ambiente local em containers.

### Configuração das variáveis de ambiente

| Variável | Descrição |
|---|---|
| DB_URL | URL JDBC de conexão com o Oracle |
| DB_USER | Usuário do banco de dados |
| DB_PASSWORD | Senha do banco de dados |
| RABBIT_HOST | Endereço do RabbitMQ |
| RABBIT_PORT | Porta do RabbitMQ |
| RABBIT_USER | Usuário do RabbitMQ |
| RABBIT_PASSWORD | Senha do RabbitMQ |
| JWT_SECRET | Chave de autenticação JWT |
| OLLAMA_BASE_URL | Endereço do serviço Ollama |
| SEED_ENABLED | Habilitação dos dados de demonstração |

As credenciais devem ser configuradas por meio de variáveis de ambiente, evitando sua exposição no repositório.

### Compilar e executar os testes

```bash
mvn clean package
```

### Executar a aplicação

```bash
mvn spring-boot:run
```

### Acessar a documentação Swagger

Com a aplicação em execução:

http://localhost:8080/swagger-ui.html

## Provisionamento da infraestrutura

Os scripts disponíveis na pasta `/scripts` foram elaborados utilizando Azure CLI e PowerShell, com o objetivo de automatizar a criação e configuração dos recursos necessários para hospedagem da aplicação.

Para autenticação na Azure:

```powershell
az login
```

Os scripts devem ser revisados e configurados de acordo com a assinatura Azure utilizada antes de sua execução.

## Segurança

A solução contempla as seguintes práticas de segurança:

- Autenticação através de tokens JWT;
- Gerenciamento de credenciais por variáveis de ambiente;
- Controle de acesso ao repositório;
- Revisão de código por Pull Requests;
- Separação entre código-fonte e configurações sensíveis.

## Status da entrega

A arquitetura macro e a estratégia de infraestrutura foram definidas, juntamente com a configuração proposta para a pipeline CI/CD.

Devido a dificuldades durante a configuração do ambiente Azure e ao prazo de entrega, a implantação definitiva da aplicação e a validação completa da pipeline não foram concluídas.

As integrações externas com Oracle Database, RabbitMQ e Ollama ainda necessitam de validação no ambiente de nuvem.

## Utilização de inteligência artificial

Durante o desenvolvimento, foram utilizadas ferramentas de inteligência artificial generativa como apoio na elaboração da documentação, definição da arquitetura, configuração de scripts e desenvolvimento da pipeline CI/CD.

---
