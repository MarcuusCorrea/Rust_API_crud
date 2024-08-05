Esta é uma API CRUD simples desenvolvida em Rust, utilizando PostgreSQL como banco de dados. A aplicação é containerizada utilizando Docker e Docker Compose.

## Pré-requisitos

- Docker
- Docker Compose

## Estrutura do Projeto

- `src/`: Contém o código-fonte da aplicação Rust.
- `Dockerfile`: Define a imagem Docker para a aplicação Rust.
- `docker-compose.yml`: Configuração do Docker Compose para levantar a aplicação e o banco de dados PostgreSQL.

## Configuração

### Variáveis de Ambiente

Certifique-se de definir a variável de ambiente `DATABASE_URL` no `docker-compose.yml`.


version: '3.9'

    services:
      rustapp:
        container_name: rustapp
        image: francescoxx/rustapp:1.0.0
        build:
          context: .
          dockerfile: Dockerfile
          args:
            DATABASE_URL: postgres://postgres:postgres@db:5432/postgres
        ports:
          - '8080:8080'
        depends_on:
          - db
      db:
        container_name: db
        image: postgres:12
        environment:
          POSTGRES_USER: postgres
          POSTGRES_PASSWORD: Zafenatepane1@
          POSTGRES_DB: postgres
        ports:
          - '5432:5432'
        volumes:
          - pgdata:/var/lib/postgresql/data
    
    volumes:
      pgdata: {}
    Instruções para Construção e Execução
    Clone o repositório:
----------------------------
    git clone <URL_DO_REPOSITORIO>
    cd <NOME_DO_REPOSITORIO>

Construa e inicie os containers:

    docker-compose up --build
    A API estará disponível em http://localhost:8080.

Criar um Novo Usuário (POST)

    URL: http://localhost:8080/users
    Método: POST
    Headers:
    Content-Type: application/json
    Body:
    json

    {
      "name": "John Doe",
      "email": "johndoe@example.com"
    }

Obter Todos os Usuários (GET)

      URL: http://localhost:8080/users
      Método: GET
      Obter um Usuário Específico (GET)
      URL: http://localhost:8080/users/{id}
      Método: GET

Atualizar um Usuário (PUT)

    URL: http://localhost:8080/users/{id}
    Método: PUT
    Headers:
    Content-Type: application/json
    Body:
    json
    
    {
      "name": "Jane Doe",
      "email": "janedoe@example.com"
    }

Deletar um Usuário (DELETE)

    URL: http://localhost:8080/users/{id}
Método: DELETE

IDE Utilizada
RustWover

Autor
Marcos Corrêa
