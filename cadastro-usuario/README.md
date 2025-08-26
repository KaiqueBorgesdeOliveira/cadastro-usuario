# Sistema de Cadastro de Usuários

Sistema simples de cadastro de usuários desenvolvido em Spring Boot com arquitetura em camadas.

## Tecnologias Utilizadas

- Java 17
- Spring Boot 3.5.5
- Spring Data JPA
- H2 Database (banco em memória)
- Lombok
- Maven

## Funcionalidades

O sistema oferece as seguintes operações para gerenciamento de usuários:

- **Cadastrar usuário**: Salva um novo usuário no sistema
- **Buscar usuário por email**: Recupera um usuário específico pelo email
- **Atualizar usuário**: Modifica dados de um usuário existente por ID
- **Deletar usuário**: Remove um usuário do sistema por email

## Estrutura do Projeto

```
src/main/java/com/universon/cadastro_usuario/
├── controller/          # Controladores REST
├── business/           # Lógica de negócio
├── infrastructure/     # Entidades e repositórios
└── CadastroUsuarioApplication.java
```

## Modelo de Dados

A entidade `Usuario` possui os seguintes campos:
- `id`: Identificador único (gerado automaticamente)
- `email`: Email do usuário (único)
- `nome`: Nome do usuário

## Endpoints da API

### Base URL: `http://localhost:8081/usuario`

| Método | Endpoint | Descrição | Parâmetros |
|--------|----------|-----------|------------|
| POST | `/usuario` | Cadastrar usuário | Body: JSON com email e nome |
| GET | `/usuario?email={email}` | Buscar usuário | Query param: email |
| PUT | `/usuario?id={id}` | Atualizar usuário | Query param: id, Body: JSON |
| DELETE | `/usuario?email={email}` | Deletar usuário | Query param: email |

## Como Executar

1. **Pré-requisitos**: Java 17 instalado
2. **Compilar**: `mvn clean install`
3. **Executar**: `mvn spring-boot:run`
4. **Acessar**: http://localhost:8081

## Banco de Dados

- **Tipo**: H2 (banco em memória)
- **Console**: http://localhost:8081/h2-console
- **Credenciais**: 
  - Username: sa
  - Password: 1234
  - JDBC URL: jdbc:h2:mem:usuarios

## Exemplos de Uso

### Cadastrar usuário
```bash
curl -X POST http://localhost:8081/usuario \
  -H "Content-Type: application/json" \
  -d '{"email":"joao@email.com","nome":"João Silva"}'
```

### Buscar usuário
```bash
curl http://localhost:8081/usuario?email=joao@email.com
```

### Atualizar usuário
```bash
curl -X PUT http://localhost:8081/usuario?id=1 \
  -H "Content-Type: application/json" \
  -d '{"nome":"João Silva Santos"}'
```

### Deletar usuário
```bash
curl -X DELETE http://localhost:8081/usuario?email=joao@email.com
```
