# User Management API

Esta é uma API simples de gerenciamento de usuários construída com Node.js, Express, e MySQL. Ela permite criar, atualizar, deletar, e visualizar usuários, além de funcionalidades de autenticação e recuperação de senha.

## Funcionalidades

- **Cadastro de Usuários**: Permite o cadastro de novos usuários.
- **Listagem de Usuários**: Exibe uma lista de todos os usuários cadastrados (necessário autenticação).
- **Busca de Usuário por ID**: Exibe os detalhes de um usuário específico (necessário autenticação).
- **Atualização de Usuário**: Permite a atualização das informações de um usuário (necessário autenticação).
- **Remoção de Usuário**: Remove um usuário do banco de dados (necessário autenticação).
- **Recuperação de Senha**: Envia um token para recuperação de senha ao e-mail do usuário.
- **Alteração de Senha**: Permite que o usuário altere sua senha utilizando um token.
- **Login**: Autentica o usuário e retorna um token JWT.
- **Validação de Token**: Verifica se o token JWT é válido e se o usuário tem permissão de administrador.

## Tecnologias Utilizadas

- Node.js
- Express
- MySQL
- JWT (JSON Web Token)
- Bcrypt

## Instalação

1. Clone o repositório:

    ```bash
    git clone https://github.com/seu-usuario/seu-repositorio.git
    cd seu-repositorio
    ```

2. Instale as dependências:

    ```bash
    npm install
    ```

3. Configure o banco de dados:

    Crie um banco de dados MySQL com o nome `apiusers`. Em seguida, edite o arquivo `connection.js` na pasta `models` com as credenciais do seu banco de dados:

    ```javascript
    var knex = require('knex')({
        client: 'mysql2',
        connection: {
            host : '127.0.0.1',
            user : 'root',
            password : 'sua_senha',
            database : 'apiusers'
        }
    });
    ```

4. Execute as migrações para criar as tabelas no banco de dados (se houver).

5. Inicie o servidor:

    ```bash
    npm start
    ```

    O servidor estará rodando em `http://localhost:3000`.

## Endpoints

- `POST /user` - Cria um novo usuário.
- `GET /user` - Retorna todos os usuários (necessário autenticação e ser admin).
- `GET /user/:id` - Retorna um usuário pelo ID (necessário autenticação e ser admin).
- `PUT /user` - Atualiza um usuário existente (necessário autenticação e ser admin).
- `DELETE /user/:id` - Remove um usuário pelo ID (necessário autenticação e ser admin).
- `POST /recoverpassword` - Envia um e-mail para recuperação de senha.
- `PUT /changepassword` - Altera a senha de um usuário utilizando um token de recuperação.
- `POST /login` - Autentica o usuário e retorna um token JWT.
- `POST /validate` - Valida o token JWT e verifica as permissões de administrador.

## Middleware

- **AdminAuth**: Middleware que verifica se o usuário está autenticado e possui permissões de administrador.

## Segurança

- **JWT**: Utilizado para autenticação e autorização dos usuários.
- **Bcrypt**: Utilizado para hash de senhas, garantindo que as senhas não sejam armazenadas em texto simples no banco de dados.
