# 📚 API Livraria

Sistema de gerenciamento de biblioteca com **Go (Golang)**, **Gin Framework** e interface web moderna.

![Go Version](https://img.shields.io/badge/Go-1.23.2-00ADD8?style=flat&logo=go)
![SQLite](https://img.shields.io/badge/SQLite-3-003B57?style=flat&logo=sqlite)

## 📋 Sobre

API RESTful completa para gerenciamento de biblioteca com cadastro de livros, usuários e controle de empréstimos. Interface web responsiva com design moderno e banco de dados SQLite embutido.

## ✨ Funcionalidades

- 📖 **Livros:** CRUD completo com busca por ID e título
- 👥 **Usuários:** Cadastro com email e telefone, busca por nome
- 📅 **Empréstimos:** Registro e controle de datas, consulta por usuário
- 🎨 **Interface:** Design responsivo com gradientes modernos
- 🔒 **Segurança:** CORS configurado, validação de dados, prepared statements

## 🛠️ Tecnologias

**Backend:**
- Go 1.23.2 + Gin Framework
- SQLite3 (banco embutido)
- CORS & Security Middlewares

**Frontend:**
- HTML5, CSS3, JavaScript ES6+
- Google Fonts (Inter)
- Fetch API para requisições assíncronas

## 🚀 Como Executar

### Pré-requisitos
- Go 1.23.2 ou superior

### Instalação

1. **Clone e instale**
```bash
git clone https://github.com/samuelcotinguiba/API-Livraria.git
cd API-Livraria
go mod download
```

2. **Execute**
```bash
go run .
```

3. **Acesse**
```
http://localhost:8000/
```

O banco de dados SQLite (`biblioteca.db`) será criado automaticamente na primeira execução.

## 📁 Estrutura

```
API-Livraria/
├── main.go              # Entrada da aplicação + rotas
├── go.mod               # Dependências Go
├── controllers/         # Handlers das rotas
├── database/           # Configuração e conexão SQLite
├── models/             # Structs (Livro, Usuario, Emprestimo)
└── static/             # Interface web
    ├── index.html         # Página inicial
    ├── busca.html         # Busca de registros
    ├── gerenciamento.html # Cadastros
    ├── style.css          # Estilos principais
    ├── index.css          # Estilos navegação
    └── script.js          # Lógica JavaScript
```

## 📡 API Endpoints

### 📖 Livros

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/livros/` | Lista todos os livros |
| `GET` | `/api/livros/:id` | Busca livro por ID |
| `GET` | `/api/livros/titulo/:title` | Busca livro por título |
| `POST` | `/api/livros/create` | Cria novo livro |
| `DELETE` | `/api/livros/:id` | Deleta livro |

### 👥 Usuários

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/usuarios/` | Lista todos os usuários |
| `GET` | `/api/usuarios/:name` | Busca usuário por nome |
| `POST` | `/api/usuarios/create` | Cria novo usuário |

### 📅 Empréstimos

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/emprestimos/` | Lista todos os empréstimos |
| `GET` | `/api/emprestimos/:usuario` | Busca empréstimos por usuário |
| `POST` | `/api/emprestimos/create/` | Cria novo empréstimo |

## 📝 Exemplos de Uso

### JSON Schemas

**Criar Livro:**
```json
{
  "titulo": "1984",
  "autor": "George Orwell"
}
```

**Criar Usuário:**
```json
{
  "nome": "João Silva",
  "email": "joao@example.com",
  "telefone": "(11) 98765-4321"
}
```

**Criar Empréstimo:**
```json
{
  "titulo": "1984",
  "email": "joao@example.com",
  "data_emprestimo": "2026-01-09",
  "data_devolucao": "2026-01-23"
}
```

### Exemplos cURL

```bash
# Criar um livro
curl -X POST http://localhost:8000/api/livros/create \
  -H "Content-Type: application/json" \
  -d '{"titulo":"Dom Casmurro","autor":"Machado de Assis"}'

# Listar todos os livros
curl http://localhost:8000/api/livros/

# Criar um usuário
curl -X POST http://localhost:8000/api/usuarios/create \
  -H "Content-Type: application/json" \
  -d '{"nome":"Maria Santos","email":"maria@example.com","telefone":"(11) 99999-8888"}'

# Criar empréstimo
curl -X POST http://localhost:8000/api/emprestimos/create/ \
  -H "Content-Type: application/json" \
  -d '{"titulo":"Dom Casmurro","email":"maria@example.com","data_emprestimo":"2026-01-09","data_devolucao":"2026-01-23"}'
```

## 🗄️ Banco de Dados

### Estrutura das Tabelas

**livros**
```sql
CREATE TABLE livros (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    titulo TEXT NOT NULL,
    autor TEXT NOT NULL
);
```

**usuarios**
```sql
CREATE TABLE usuarios (
    id INTEGER PRIMARY KEY,
    nome TEXT NOT NULL,
    email TEXT,
    telefone TEXT
);
```

**emprestimos**
```sql
CREATE TABLE emprestimos (
    id INTEGER PRIMARY KEY,
    id_livro INTEGER NOT NULL,
    id_usuario INTEGER NOT NULL,
    data_emprestimo DATE,
    data_devolucao DATE,
    FOREIGN KEY (id_livro) REFERENCES livros(id),
    FOREIGN KEY (id_usuario) REFERENCES usuarios(id)
);
```

## 🎨 Interface Web

- **Página Inicial:** Navegação para busca e gerenciamento
- **Busca:** Consulta e visualização de dados
- **Gerenciamento:** Formulários para cadastro de livros, usuários e empréstimos
- **Design:** Gradientes roxo/azul, animações suaves, totalmente responsivo

## 🧪 Testando

Use os scripts incluídos ou ferramentas como Postman/Insomnia:

```bash
./test_sever_get.sh      # Testa GET de livros
./test_sever_get_ID.sh   # Testa GET por ID
./test_sever_post.sh     # Testa POST de livro
```

## 👨‍💻 Autor

**Samuel Cotinguiba** - [@samuelcotinguiba](https://github.com/samuelcotinguiba)

---

⭐ Gostou? Dê uma estrela no projeto!
