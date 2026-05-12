# 📋 Cadastro de Usuários - CRUD Java + Spring Boot

Um projeto CRUD (Create, Read, Update, Delete) básico desenvolvido em **Java** com **Spring Boot** para gerenciar cadastro de usuários.

## 🚀 Tecnologias Utilizadas

- **Java 17+**
- **Spring Boot 3.x**
- **Spring Data JPA**
- **Spring Web**
- **MySQL** (ou H2 para testes)
- **Lombok**
- **Maven**

## 📦 Pré-requisitos

Antes de iniciar, certifique-se de ter instalado:

- [Java JDK 17+](https://www.oracle.com/java/technologies/downloads/)
- [Maven 3.6+](https://maven.apache.org/download.cgi)
- [MySQL 8.0+](https://www.mysql.com/downloads/) (opcional, pode usar H2)
- [Postman](https://www.postman.com/downloads/) (para testar os endpoints)

## ⚙️ Configuração do Projeto

### 1. Clonar o Repositório

```bash
git clone https://github.com/seu-usuario/cadastro-usuario.git
cd cadastro-usuario
```

### 2. Configurar o Banco de Dados

Edite o arquivo `application.properties` ou `application.yml`:

**Para MySQL:**
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/cadastro_usuarios
spring.datasource.username=root
spring.datasource.password=sua_senha
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
server.port=8080
```

**Para H2 (Em memória - Teste):**
```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.h2.console.enabled=true
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
server.port=8080
```

### 3. Instalar Dependências

```bash
mvn clean install
```

### 4. Executar a Aplicação

```bash
mvn spring-boot:run
```

A aplicação estará disponível em: `http://localhost:8080`

## 📡 Endpoints da API

### 1️⃣ Criar Usuário (CREATE)

**Método:** `POST`  
**URL:** `http://localhost:8080/api/usuarios`  
**Content-Type:** `application/json`

**Body (JSON):**
```json
{
  "nome": "João Silva",
  "email": "joao@email.com"
}
```

**Resposta (201 Created):**
```json
{
  "id": 1,
  "nome": "João Silva",
  "email": "joao@email.com"
}
```

---

### 2️⃣ Listar Todos os Usuários (READ)

**Método:** `GET`  
**URL:** `http://localhost:8080/api/usuarios`

**Resposta (200 OK):**
```json
[
  {
    "id": 1,
    "nome": "João Silva",
    "email": "joao@email.com"
  },
  {
    "id": 2,
    "nome": "Maria Santos",
    "email": "maria@email.com"
  }
]
```

---

### 3️⃣ Buscar Usuário por ID (READ)

**Método:** `GET`  
**URL:** `http://localhost:8080/api/usuarios/{id}`  
**Exemplo:** `http://localhost:8080/api/usuarios/1`

**Resposta (200 OK):**
```json
{
  "id": 1,
  "nome": "João Silva",
  "email": "joao@email.com"
}
```

---

### 4️⃣ Atualizar Usuário (UPDATE)

**Método:** `PUT`  
**URL:** `http://localhost:8080/api/usuarios/{id}`  
**Exemplo:** `http://localhost:8080/api/usuarios/1`  
**Content-Type:** `application/json`

**Body (JSON):**
```json
{
  "nome": "João Silva Atualizado",
  "email": "joao.novo@email.com"
}
```

**Resposta (200 OK):**
```json
{
  "id": 1,
  "nome": "João Silva Atualizado",
  "email": "joao.novo@email.com"
}
```

---

### 5️⃣ Deletar Usuário (DELETE)

**Método:** `DELETE`  
**URL:** `http://localhost:8080/api/usuarios/{id}`  
**Exemplo:** `http://localhost:8080/api/usuarios/1`

**Resposta (204 No Content)** - Sem corpo na resposta

---

## 🧪 Testando com Postman

### Passo 1: Abrir o Postman

1. Abra o Postman
2. Crie uma nova requisição clicando em **"New"** → **"Request"**

### Passo 2: Criar um Usuário (POST)

1. Defina o método como **POST**
2. URL: `http://localhost:8080/api/usuarios`
3. Abra a aba **"Body"**
4. Selecione **"raw"** e escolha **"JSON"**
5. Cole o JSON:
```json
{
  "nome": "João Silva",
  "email": "joao@email.com"
}
```
6. Clique em **"Send"**

### Passo 3: Listar Usuários (GET)

1. Defina o método como **GET**
2. URL: `http://localhost:8080/api/usuarios`
3. Clique em **"Send"**

### Passo 4: Buscar Usuário por ID (GET)

1. Defina o método como **GET**
2. URL: `http://localhost:8080/api/usuarios/1`
3. Clique em **"Send"**

### Passo 5: Atualizar Usuário (PUT)

1. Defina o método como **PUT**
2. URL: `http://localhost:8080/api/usuarios/1`
3. Abra a aba **"Body"**
4. Selecione **"raw"** e escolha **"JSON"**
5. Cole o JSON atualizado:
```json
{
  "nome": "João Silva Atualizado",
  "email": "joao.novo@email.com"
}
```
6. Clique em **"Send"**

### Passo 6: Deletar Usuário (DELETE)

1. Defina o método como **DELETE**
2. URL: `http://localhost:8080/api/usuarios/1`
3. Clique em **"Send"**

---

## 📁 Estrutura do Projeto

```
cadastro-usuario/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/java/cadastro_usuario/
│   │   │       ├── infrastructure/
│   │   │       │   ├── entitys/
│   │   │       │   │   └── Usuario.java
│   │   │       │   ├── repositories/
│   │   │       │   │   └── UsuarioRepository.java
│   │   │       ├── application/
│   │   │       │   ├── services/
│   │   │       │   │   └── UsuarioService.java
│   │   │       │   ├── controllers/
│   │   │       │   │   └── UsuarioController.java
│   │   │       └── CadastroUsuarioApplication.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
└── pom.xml
```

---

## 💡 Como Funciona o CRUD

### **CREATE (Criar)**
- Recebe dados do usuário via POST
- Valida os dados
- Salva no banco de dados
- Retorna o usuário criado com ID

### **READ (Ler)**
- GET retorna todos os usuários ou um específico
- Busca no banco de dados
- Retorna os dados em JSON

### **UPDATE (Atualizar)**
- Recebe ID e novos dados via PUT
- Busca o usuário no banco
- Atualiza os campos
- Retorna o usuário atualizado

### **DELETE (Deletar)**
- Recebe ID via DELETE
- Remove o usuário do banco
- Retorna confirmação (204 No Content)

---

## 🛠️ Exemplo Prático - Fluxo Completo

```bash
# 1. Criar usuário
POST /api/usuarios
{ "nome": "João", "email": "joao@email.com" }
→ Retorna: { "id": 1, "nome": "João", "email": "joao@email.com" }

# 2. Listar todos
GET /api/usuarios
→ Retorna lista com o usuário criado

# 3. Buscar por ID
GET /api/usuarios/1
→ Retorna: { "id": 1, "nome": "João", "email": "joao@email.com" }

# 4. Atualizar
PUT /api/usuarios/1
{ "nome": "João Silva", "email": "joao.silva@email.com" }
→ Retorna usuário atualizado

# 5. Deletar
DELETE /api/usuarios/1
→ Retorna 204 (sem conteúdo)
```

---

## 📝 Tratamento de Erros

| Código | Significado |
|--------|------------|
| **200** | OK - Requisição bem-sucedida |
| **201** | Created - Usuário criado com sucesso |
| **204** | No Content - Deletado com sucesso |
| **400** | Bad Request - Dados inválidos |
| **404** | Not Found - Usuário não encontrado |
| **500** | Server Error - Erro no servidor |

---

## 🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.

---

## 👨‍💻 Autor

Desenvolvido com ❤️ por [Leticia Martins De Almeida](https://github.com/seu-usuario)

---

**Dúvidas?** Abra uma [Issue](https://github.com/seu-usuario/cadastro-usuario/issues) no repositório!
