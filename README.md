# 🚀 RocketLog

API de gerenciamento de entregas de encomendas desenvolvida com Node.js, TypeScript e Prisma.

## 📋 Descrição

O RocketLog é uma API RESTful para gerenciamento de entregas de encomendas, permitindo o controle de usuários, sessões, entregas e logs de entrega. O sistema suporta diferentes tipos de usuários (clientes e vendedores) e oferece um sistema completo de rastreamento de entregas.

## 🛠️ Tecnologias Utilizadas

- **Node.js** - Runtime JavaScript
- **TypeScript** - Linguagem de programação
- **Express.js** - Framework web
- **Prisma** - ORM para banco de dados
- **PostgreSQL** - Banco de dados
- **JWT** - Autenticação
- **bcrypt** - Criptografia de senhas
- **Zod** - Validação de dados
- **Jest** - Testes
- **Docker** - Containerização

## 🏗️ Estrutura do Projeto

```
rocketlog/
├── src/
│   ├── controllers/          # Controladores da aplicação
│   ├── middlewares/          # Middlewares (auth, error handling)
│   ├── routes/              # Definição das rotas
│   ├── database/            # Configuração do banco de dados
│   ├── configs/             # Configurações (auth)
│   ├── utils/               # Utilitários (AppError)
│   ├── tests/               # Testes unitários
│   ├── app.ts               # Configuração do Express
│   └── server.ts            # Servidor da aplicação
├── prisma/
│   ├── schema.prisma        # Schema do banco de dados
│   └── migrations/          # Migrações do banco
├── types/                   # Tipos TypeScript
├── docker-compose.yml       # Configuração Docker
└── package.json            # Dependências do projeto
```

## 🚀 Como Executar

### Pré-requisitos

- Node.js (versão 18 ou superior)
- Docker e Docker Compose
- npm ou yarn

### 1. Clone o repositório

```bash
git clone <url-do-repositorio>
cd rocketlog
```

### 2. Instale as dependências

```bash
npm install
```

### 3. Configure as variáveis de ambiente

Crie um arquivo `.env` na raiz do projeto:

```env
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/rocketlog"
JWT_SECRET="sua-chave-secreta-aqui"
```

### 4. Inicie o banco de dados

```bash
docker-compose up -d
```

### 5. Execute as migrações

```bash
npx prisma migrate dev
```

### 6. Inicie o servidor de desenvolvimento

```bash
npm run dev
```

O servidor estará rodando em `http://localhost:3333`

## 📚 Endpoints da API

### Autenticação

#### POST `/sessions`
Criar uma sessão (login)
```json
{
  "email": "user@example.com",
  "password": "123456"
}
```

### Usuários

#### POST `/users`
Criar um novo usuário
```json
{
  "name": "João Silva",
  "email": "joao@example.com",
  "password": "123456"
}
```

### Entregas

#### POST `/deliveries`
Criar uma nova entrega (requer autenticação)
```json
{
  "description": "Entrega de eletrônicos"
}
```

#### GET `/deliveries`
Listar entregas do usuário (requer autenticação)

#### PUT `/deliveries/:id/status`
Atualizar status da entrega (requer autenticação)
```json
{
  "status": "shipped"
}
```

### Logs de Entrega

#### POST `/delivery-logs`
Criar log para uma entrega (requer autenticação)
```json
{
  "description": "Encomenda coletada no depósito",
  "deliveryId": "uuid-da-entrega"
}
```

#### GET `/delivery-logs/:deliveryId`
Listar logs de uma entrega específica (requer autenticação)

## 🧪 Testes

Para executar os testes:

```bash
# Executar todos os testes
npm test

# Executar testes em modo watch
npm run test:dev
```

## 🔧 Scripts Disponíveis

- `npm run dev` - Inicia o servidor em modo desenvolvimento
- `npm run test:dev` - Executa testes em modo watch
- `npx prisma studio` - Abre o Prisma Studio para visualizar o banco
- `npx prisma migrate dev` - Executa migrações do banco
- `npx prisma generate` - Gera o cliente Prisma

## 🐳 Docker

Para executar apenas o banco de dados com Docker:

```bash
docker-compose up -d
```

## 📝 Funcionalidades

- ✅ Autenticação com JWT
- ✅ Criptografia de senhas com bcrypt
- ✅ Validação de dados com Zod
- ✅ Sistema de roles (customer/sale)
- ✅ CRUD de usuários
- ✅ CRUD de entregas
- ✅ Sistema de logs de entrega
- ✅ Middleware de autenticação
- ✅ Tratamento de erros centralizado
- ✅ Testes unitários
- ✅ Migrações do banco de dados

## 👨‍💻 Autor

**Diego Coelho**

## 📄 Licença

Este projeto está sob a licença ISC.

