# **Hackaton API**

Este projeto é uma API para gerenciar acomodações, desenvolvida com **NestJS**, **Prisma ORM** e banco de dados **MySQL**, utilizando o **Aiven** para hospedagem. O Docker é utilizado para criar o ambiente de desenvolvimento e produção, facilitando a configuração e a escalabilidade do projeto.

---

## **Tecnologias Utilizadas**

- **NestJS**: Framework Node.js para construção de APIs escaláveis.
- **Prisma ORM**: ORM para manipulação de banco de dados.
- **MySQL**: Banco de dados relacional utilizado para armazenamento de dados.
- **Aiven**: Plataforma de dados em nuvem para hospedagem do MySQL.
- **Docker**: Containeriza a aplicação e o banco de dados para facilitar o desenvolvimento e a produção.

---

## **Instalação**

Para rodar o projeto, siga os passos abaixo:

### **1. Clonando o Repositório**

Clone o repositório para sua máquina local:

```bash
git clone https://github.com/seu-usuario/hackaton.git
cd hackaton
```

### **2. Instalar Dependências**

Instale as dependências do projeto utilizando o `npm`:

```bash
npm install
```

---

## **Configuração do Docker**

Este projeto usa o Docker para criar um ambiente isolado e facilmente replicável para rodar a aplicação e o banco de dados.

### **1. Dockerfile**

O `Dockerfile` contém as instruções para construir a imagem do backend da aplicação. Ele utiliza a imagem oficial do Node.js, instala as dependências e expõe a porta 3000.

```dockerfile
# Usando a imagem oficial do Node.js
FROM node:16

# Criando o diretório de trabalho
WORKDIR /app

# Copiando os arquivos do projeto para o container
COPY . .

# Instalando as dependências
RUN npm install

# Expondo a porta onde a API será executada
EXPOSE 3000

# Comando para rodar a aplicação
CMD ["npm", "run", "start:dev"]
```

### **2. docker-compose.yml**

O arquivo `docker-compose.yml` define os containers para o backend e o banco de dados MySQL. A aplicação backend depende do banco de dados MySQL.

```yaml
version: "3.8"
services:
  accommodation-api:
    build: .
    ports:
      - "3000:3000"
    environment:
      - DATABASE_URL=mysql://usuario:senha@db:3306/accommodations
    depends_on:
      - db

  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: senha
      MYSQL_DATABASE: accommodations
    ports:
      - "3306:3306"
```

### **3. Rodando os Containers**

Execute o comando abaixo para rodar os containers Docker e iniciar a aplicação:

```bash
docker-compose up --build
```

Isso irá construir a imagem do Docker e iniciar os containers para a API e o banco de dados MySQL.

---

## **Configuração do Arquivo .env**

O arquivo `.env` contém as variáveis de ambiente necessárias para a configuração do banco de dados e da aplicação.

### **1. Criando o Arquivo .env**

Crie um arquivo `.env` na raiz do projeto com o seguinte conteúdo:

```env
# URL de conexão com o banco de dados MySQL
MYSQL_HOST=
MYSQL_PORT=
MYSQL_DATABASE=
MYSQL_USER=
MYSQL_PASSWORD=
DATABASE_URL="mysql://usuario:senha@localhost:3306/accommodations"

# Definir o ambiente de execução
NODE_ENV=development
```

- **DATABASE_URL**: URL de conexão com o banco de dados MySQL. Certifique-se de substituir `usuario` e `senha` pelos valores corretos.
- **NODE_ENV**: Define o ambiente de execução (pode ser `development`, `production` etc.).

Se estiver usando o **Aiven** para hospedar o banco de dados, obtenha a URL de conexão através do painel do Aiven e substitua no arquivo `.env`.

---

## **Configuração do Banco de Dados com Prisma**

O **Prisma** é utilizado para interagir com o banco de dados. O banco de dados MySQL deve ser configurado para aceitar as conexões, e o Prisma deve ser configurado para utilizar essa conexão.

### **1. Migrando o Banco de Dados**

Para configurar o banco de dados, rode as migrações do Prisma com o comando:

```bash
npx prisma migrate dev
```

Isso cria as tabelas no banco de dados de acordo com o schema definido no `prisma/schema.prisma`.

### **2. Utilizando o Prisma Studio**

O **Prisma Studio** é uma interface gráfica para interagir com o banco de dados. Para rodá-lo, use:

```bash
npx prisma studio
```

Isso abrirá o Prisma Studio no seu navegador, onde você pode visualizar e manipular os dados diretamente no banco de dados.

---

## **Executando a API**

Agora que todos os containers estão rodando e o banco de dados foi configurado, você pode acessar a API na URL:

```
http://localhost:3000
```

- A aplicação estará escutando na porta **3000** e pronta para receber requisições.

---

## **Comandos Úteis**

- **Instalar dependências**: `npm install`
- **Rodar a aplicação**: `npm run start:dev`
- **Rodar o Docker**: `docker-compose up --build`
- **Executar migrações Prisma**: `npx prisma migrate dev`
- **Abrir Prisma Studio**: `npx prisma studio`

---

## **Dependências do Projeto**

As principais dependências são:

- **@nestjs/core, @nestjs/common, @nestjs/platform-express**: Bibliotecas principais do **NestJS** para construção da API.
- **@prisma/client**: Cliente Prisma para interagir com o banco de dados.
- **dotenv**: Carrega as variáveis de ambiente do arquivo `.env`.
- **axios**: Biblioteca para realizar requisições HTTP.
- **rxjs**: Biblioteca para programação reativa, usada no **NestJS**.

### **Dependências de Desenvolvimento**

- **prisma**: Ferramenta para migrações e geração do cliente Prisma.
- **eslint**: Ferramenta para garantir a qualidade do código.
- **typescript**: Compilador TypeScript.
