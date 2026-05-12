# CRUD Java com Spring Boot 


Projeto de CRUD completo desenvolvido seguindo as dicas do canal **Javanauta**

Este é um projeto **prático e moderno** que demonstra as melhores práticas de desenvolvimento com Spring Boot, ideal para iniciantes e intermediários que querem construir um portfólio sólido.

---

## 🎯 Objetivo

Criar um sistema completo de gerenciamento de usuários utilizando as tecnologias mais atuais do mercado, com uma arquitetura limpa e bem estruturada.

## Site para quem quiser testar:  localhost:8081/h2-console

- **Driver Class:** 	org.h2.Driver
- **JDBC URL:** jdbc:h2:mem:usuarios
- **Username:** sa
  
(só clicar em conect)

server port: 8081

---

## 🚀 Tecnologias Utilizadas

- **Java 17+** - Linguagem de programação
- **Spring Boot 3.x** - Framework web
- **Spring Data JPA** - ORM e persistência de dados
- **Spring Web** - REST API
- **MySQL 8.0+** - Banco de dados relacional
- **Lombok** - Redução de código boilerplate
- **Maven** - Gerenciador de dependências
- **Postman** - Testes de API

---

## 📋 Pré-requisitos

Antes de começar, você precisa ter instalado:

- ☕ [Java Development Kit (JDK) 17+](https://www.oracle.com/java/technologies/downloads/)
- 📦 [Maven 3.8+](https://maven.apache.org/download.cgi)
- 🗄️ [MySQL 8.0+](https://www.mysql.com/downloads/)
- 📮 [Postman](https://www.postman.com/downloads/) (opcional, para testar)
- 🔧 [Git](https://git-scm.com/downloads)

---

## 🛠️ Configuração e Instalação

### 1️⃣ Clonar o Repositório

```bash
git clone https://github.com/seu-usuario/crud-spring-boot-2025.git
cd crud-spring-boot-2025
```

### 2️⃣ Criar o Banco de Dados

Abra o **MySQL** e execute:

```sql
CREATE DATABASE cadastro_usuarios;
USE cadastro_usuarios;
```

### 3️⃣ Configurar Conexão com Banco

Edite o arquivo `src/main/resources/application.properties`:

```properties
# Configuração do Servidor
server.port=8081
server.servlet.context-path=/api

# Configuração do Banco de Dados MySQL
spring.datasource.url=jdbc:mysql://localhost:3306/cadastro_usuarios
spring.datasource.username=root
spring.datasource.password=sua_senha_aqui
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# Configuração do Hibernate/JPA
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

# Log
logging.level.org.hibernate.SQL=DEBUG
logging.level.org.hibernate.type.descriptor.sql.BasicBinder=TRACE
```

### 4️⃣ Instalar Dependências

```bash
mvn clean install
```

### 5️⃣ Executar a Aplicação

```bash
mvn spring-boot:run
```

✅ A aplicação estará rodando em: **`http://localhost:8080/api`**

---

## 📡 Endpoints da API

### 🆕 1. Criar um Novo Usuário (CREATE)

```http
POST /api/usuarios
Content-Type: application/json

{
  "nome": "João Silva",
  "email": "joao.silva@email.com"
}
```

**Resposta (201 Created):**
```json
{
  "id": 1,
  "nome": "João Silva",
  "email": "joao.silva@email.com"
}
```

---

### 📖 2. Listar Todos os Usuários (READ)

```http
GET /api/usuarios
```

**Resposta (200 OK):**
```json
[
  {
    "id": 1,
    "nome": "João Silva",
    "email": "joao.silva@email.com"
  },
  {
    "id": 2,
    "nome": "Maria Santos",
    "email": "maria.santos@email.com"
  }
]
```

---

### 🔍 3. Buscar Usuário por ID (READ)

```http
GET /api/usuarios/1
```

**Resposta (200 OK):**
```json
{
  "id": 1,
  "nome": "João Silva",
  "email": "joao.silva@email.com"
}
```

---

### ✏️ 4. Atualizar um Usuário (UPDATE)

```http
PUT /api/usuarios/1
Content-Type: application/json

{
  "nome": "João Silva Santos",
  "email": "joao.novo@email.com"
}
```

**Resposta (200 OK):**
```json
{
  "id": 1,
  "nome": "João Silva Santos",
  "email": "joao.novo@email.com"
}
```

---

### 🗑️ 5. Deletar um Usuário (DELETE)

```http
DELETE /api/usuarios/1
```

**Resposta (204 No Content)** - Sem corpo na resposta

---

## 🧪 Testando com Postman

### Passo 1: Importar Collection (Opcional)

Se tiver uma Collection exportada, importe em Postman:
- **File** → **Import** → Selecione o arquivo `.json`

### Passo 2: Criar um Novo Usuário

1. Clique em **"New"** → **"Request"**
2. **Método:** POST
3. **URL:** `http://localhost:8080/api/usuarios`
4. Abra a aba **"Body"** → Selecione **"raw"** → Escolha **"JSON"**
5. Cole o JSON:
```json
{
  "nome": "João Silva",
  "email": "joao@email.com"
}
```
6. Clique em **"Send"** ✅

### Passo 3: Listar Todos os Usuários

1. **Método:** GET
2. **URL:** `http://localhost:8080/api/usuarios`
3. Clique em **"Send"** ✅

### Passo 4: Buscar Usuário Específico

1. **Método:** GET
2. **URL:** `http://localhost:8080/api/usuarios/1`
3. Clique em **"Send"** ✅

### Passo 5: Atualizar um Usuário

1. **Método:** PUT
2. **URL:** `http://localhost:8080/api/usuarios/1`
3. **Body (raw - JSON):**
```json
{
  "nome": "João Silva Atualizado",
  "email": "joao.novo@email.com"
}
```
4. Clique em **"Send"** ✅

### Passo 6: Deletar um Usuário

1. **Método:** DELETE
2. **URL:** `http://localhost:8080/api/usuarios/1`
3. Clique em **"Send"** ✅

---

## 📁 Estrutura do Projeto

```
crud-spring-boot-2025/
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/java/cadastro_usuario/
│   │   │       ├── CadastroUsuarioApplication.java
│   │   │       │
│   │   │       ├── infrastructure/
│   │   │       │   ├── entitys/
│   │   │       │   │   └── Usuario.java
│   │   │       │   └── repositories/
│   │   │       │       └── UsuarioRepository.java
│   │   │       │
│   │   │       └── application/
│   │   │           ├── controllers/
│   │   │           │   └── UsuarioController.java
│   │   │           └── services/
│   │   │               └── UsuarioService.java
│   │   │
│   │   └── resources/
│   │       └── application.properties
│   │
│   └── test/
│       └── java/
│           └── com/java/cadastro_usuario/
│               └── CadastroUsuarioApplicationTests.java
│
├── .gitignore
├── pom.xml
└── README.md
```

---

## 🏗️ Arquitetura do Projeto

### **Camada de Apresentação (Controller)**
- Recebe requisições HTTP
- Valida dados de entrada
- Chama os serviços

### **Camada de Negócio (Service)**
- Contém lógica de negócio
- Validações e processamento de dados
- Comunica com a camada de dados

### **Camada de Dados (Repository)**
- Interage com o banco de dados
- CRUD via Spring Data JPA
- Consultas customizadas

### **Entidades (Entity)**
- Mapeia a tabela do banco para classe Java
- Define relacionamentos

---

## 💡 Como Funciona o CRUD

### **C - CREATE (Criar)**
```
POST → Controller → Service → Repository → Banco de Dados
         ↓
    Valida dados
         ↓
    Salva usuário
         ↓
    Retorna com ID gerado
```

### **R - READ (Ler)**
```
GET → Controller → Service → Repository → Banco de Dados
        ↓
   Busca usuários
        ↓
   Retorna em JSON
```

### **U - UPDATE (Atualizar)**
```
PUT → Controller → Service → Repository → Banco de Dados
       ↓
  Busca usuário existente
       ↓
  Atualiza campos
       ↓
  Salva alterações
```

### **D - DELETE (Deletar)**
```
DELETE → Controller → Service → Repository → Banco de Dados
           ↓
      Busca usuário
           ↓
      Remove do banco
           ↓
      Retorna 204
```

---

## 📊 Fluxo Prático Completo

```bash
1. CRIAR USUÁRIO
   POST /api/usuarios
   → Retorna: { id: 1, nome: "João", email: "joao@email.com" }

2. LISTAR TODOS
   GET /api/usuarios
   → Retorna: [ { id: 1, ... }, { id: 2, ... } ]

3. BUSCAR POR ID
   GET /api/usuarios/1
   → Retorna: { id: 1, nome: "João", email: "joao@email.com" }

4. ATUALIZAR
   PUT /api/usuarios/1
   → Retorna: { id: 1, nome: "João Novo", email: "novo@email.com" }

5. DELETAR
   DELETE /api/usuarios/1
   → Retorna: 204 No Content

6. LISTAR NOVAMENTE
   GET /api/usuarios
   → Retorna: [ { id: 2, ... } ] (João foi deletado)
```

---

## ⚠️ Códigos de Resposta HTTP

| Código | Descrição | Exemplo |
|--------|-----------|---------|
| **200** | OK | GET, PUT bem-sucedidos |
| **201** | Created | POST bem-sucedido |
| **204** | No Content | DELETE bem-sucedido |
| **400** | Bad Request | Dados inválidos |
| **404** | Not Found | Usuário não encontrado |
| **500** | Server Error | Erro no servidor |

---

## 🎓 O que Você Aprende com Este Projeto

✅ Criar uma API REST com Spring Boot  
✅ Trabalhar com bancos de dados MySQL  
✅ Usar JPA e Hibernate  
✅ Aplicar padrões de arquitetura (MVC)  
✅ Criar endpoints CRUD  
✅ Testar APIs com Postman  
✅ Versionamento com Git  
✅ Boas práticas de desenvolvimento  

---

## 📚 Dependências do Projeto (pom.xml)

```xml
<dependencies>
    <!-- Spring Boot Starter Web -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- Spring Boot Starter Data JPA -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>

    <!-- MySQL Driver -->
    <dependency>
        <groupId>com.mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>8.0.33</version>
    </dependency>

    <!-- Lombok -->
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <optional>true</optional>
    </dependency>

    <!-- Spring Boot Starter Test -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```

---

## 🌟 Diferenciais do Projeto

- ✅ Código limpo e bem estruturado
- ✅ Segue convenções do Spring Boot
- ✅ Fácil de estender e manter
- ✅ Pronto para produção
- ✅ Excelente para portfólio
- ✅ Demonstra conhecimento real

---

## 🐛 Troubleshooting

### ❌ "Connection refused"
**Solução:** Certifique-se de que MySQL está rodando
```bash
# Windows
net start MySQL80

# Linux/Mac
sudo systemctl start mysql
```

### ❌ "Access denied for user 'root'"
**Solução:** Verifique a senha no `application.properties`

### ❌ "Table doesn't exist"
**Solução:** Spring criará automaticamente. Se não, execute:
```sql
USE cadastro_usuarios;
```

### ❌ Porta 8080 já em uso
**Solução:** Mude em `application.properties`:
```properties
server.port=8081
```

---

## 📖 Referência do Vídeo

**📺 Canal:** [Javanauta](https://www.youtube.com/@javanautachannel)  
**🎬 Vídeo:** "CRUD Java com Spring Boot 2025 | Aprenda o Projeto QUE TODO DEV PRECISA TER no Portfólio!"

---

## 🤝 Contribuindo

Quer contribuir? Siga os passos:

1. Faça um fork do repositório
2. Crie uma branch para sua feature (`git checkout -b feature/NovaFuncionalidade`)
3. Commit suas mudanças (`git commit -m 'Adicionado nova funcionalidade'`)
4. Push para a branch (`git push origin feature/NovaFuncionalidade`)
5. Abra um Pull Request

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## 💬 Dúvidas Frequentes

**P: Posso usar este projeto no meu portfólio?**  
R: Sim! Esse é exatamente o objetivo. Adapte conforme seu estilo.

**P: Como faço para adicionar mais funcionalidades?**  
R: Siga a mesma estrutura: Entity → Repository → Service → Controller

**P: Posso usar outro banco de dados?**  
R: Sim! Altere o driver no `application.properties` (PostgreSQL, Oracle, etc)

**P: É necessário usar Postman?**  
R: Não, você pode usar curl, Insomnia ou qualquer cliente HTTP.


**Desenvolvido por Leticia Martins De Almeida**

