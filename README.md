# NLW Connect

Projeto desenvolvido durante a Next Level Week (NLW), um evento online da [Rocketseat](https://rocketseat.com.br).

O NLW Connect é uma aplicação de inscrição para eventos com um sistema de ranking e convites, permitindo que os participantes acompanhem sua posição e convidem outras pessoas.

<img src="web/public/home.png" />
<img src="web/public/ranking.png" />

## 🚀 Tecnologias Utilizadas

O projeto é um monorepo dividido em `server` (backend) e `web` (frontend).

### Backend (server/)

- **Runtime/Framework**: [Node.js](https://nodejs.org/) com [Fastify](https://fastify.dev/) para construção de APIs de alta performance.
- **Linguagem**: [TypeScript](https://www.typescriptlang.org/)
- **ORM**: [Drizzle ORM](https://orm.drizzle.team/) para interação com o banco de dados de forma type-safe.
- **Banco de Dados**: [PostgreSQL](https://www.postgresql.org/)
- **Cache/In-memory Store**: [Redis](https://redis.io/) para gerenciamento de rankings e dados voláteis.
- **Validação**: [Zod](https://zod.dev/) para validação de schemas e tipos.
- **Tooling**: [Biome](https://biomejs.dev/) para formatação e linting, e [TSX](https://github.com/esbuild-kit/tsx) para execução em ambiente de desenvolvimento.

### Frontend (web/)

- **Framework**: [Next.js](https://nextjs.org/) (com Turbopack) e [React](https://react.dev/).
- **Linguagem**: [TypeScript](https://www.typescriptlang.org/)
- **Estilização**: [Tailwind CSS](https://tailwindcss.com/) para uma estilização utilitária e moderna.
- **Gerenciamento de Formulários**: [React Hook Form](https://react-hook-form.com/) com [Zod](https://zod.dev/) para validação.
- **Geração de API Client**: [Orval](https://orval.dev/) para gerar um client type-safe a partir da especificação OpenAPI do backend.
- **Ícones**: [Lucide React](https://lucide.dev/)
- **Tooling**: [Biome](https://biomejs.dev/) para formatação e linting.

## 🛠️ Setup e Configuração

Siga os passos abaixo para executar o projeto localmente.

### Pré-requisitos

- [Node.js](https://nodejs.org/) (versão 20 ou superior)
- [Docker](https://www.docker.com/) e Docker Compose

### 1. Configurando o Backend

Primeiro, suba os contêineres do banco de dados e do Redis.

```bash
# Navegue até a pasta do servidor
cd server

# Inicie os serviços com Docker
docker-compose up -d
```

Agora, configure as variáveis de ambiente.

```bash
# Crie uma cópia do arquivo .env.example (se existir) ou crie um arquivo .env
# Adicione as seguintes variáveis:
PORT=3333
DATABASE_URL="postgres://docker:docker@localhost:5432/nlw_connect"
REDIS_URL="redis://:docker@localhost:6379"
API_URL="http://localhost:3333"
WEB_URL="http://localhost:3000"
```

Por fim, instale as dependências e execute as migrações do banco.

```bash
# Instale as dependências
npm install

# Execute as migrações para criar as tabelas no banco de dados
npm run db:migrate

# Inicie o servidor de desenvolvimento
npm run dev
```

O backend estará rodando em `http://localhost:3333`.

### 2. Configurando o Frontend

Em outro terminal, navegue até a pasta do frontend.

```bash
# Navegue até a pasta web
cd web

# Instale as dependências
npm install

# Inicie o servidor de desenvolvimento
npm run dev
```

O frontend estará disponível em `http://localhost:3000`.
