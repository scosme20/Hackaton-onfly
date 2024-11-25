Hackaton API - Onfly Challenge
Este projeto foi desenvolvido como uma solução para um desafio da Onfly, com o objetivo de criar um filtro eficiente para categorias de acomodações. A API permite gerenciar acomodações e oferece funcionalidades como listagem, busca por categorias e localização.

Desafio: Filtro por Categorias de Acomodações
A Onfly enfrentava dificuldades para implementar um filtro eficiente para categorias de acomodações, dificultando a busca por opções específicas como hotéis, hostels, apartamentos, entre outros. A solução desenvolvida implementa:

Validação de Categorias: Definição de categorias válidas no código, como HOTEL, APARTMENT, HOSTEL, entre outras, evitando buscas incorretas.
Busca Personalizada: Utilização do Prisma ORM para consultar o banco de dados e retornar acomodações que correspondem à categoria solicitada.
Formatação dos Dados: Conversão dos resultados do banco de dados em um formato estruturado, incluindo cálculo de avaliações médias e listagem de benefícios.
Essa abordagem garante que os usuários possam filtrar acomodações com rapidez e precisão.

Tecnologias Utilizadas
NestJS: Framework Node.js para criação de APIs modulares e escaláveis.
Prisma ORM: Ferramenta poderosa para manipulação de banco de dados relacional.
MySQL: Banco de dados relacional utilizado para armazenar as acomodações.
Aiven: Plataforma de dados em nuvem para hospedagem do banco de dados.
Docker: Facilita o deploy e a replicação do ambiente de desenvolvimento.
Axios: Realiza integrações com APIs externas, como a geolocalização baseada em CEP.
Como Cada Tecnologia Foi Usada
NestJS: Estruturou a lógica de negócio em módulos, serviços e controladores, seguindo princípios como injeção de dependência.
Prisma ORM: Realizou consultas otimizadas no banco de dados para buscar acomodações e categorias.
MySQL: Armazenou os dados relacionados às acomodações, como tipo, localização, avaliações e benefícios.
Axios: Integrado à API do OpenCage para geocodificação baseada em CEP.
Docker: Gerou containers para a aplicação e o banco de dados, criando um ambiente padronizado para desenvolvimento e produção.
Lógica Implementada para o Filtro
Entrada do Usuário: A API recebe a categoria desejada como parâmetro.
Validação da Categoria: Verifica se a categoria informada pertence a uma lista pré-definida.
Consulta ao Banco de Dados: Utiliza o Prisma ORM para buscar acomodações que correspondem à categoria válida.
Formatação da Resposta: Cada acomodação é processada para incluir:
Avaliação média calculada com base nas reviews.
Benefícios convertidos de JSON para uma lista compreensível.
Dados de localização e descrição.
Resposta Final: A API retorna uma lista formatada das acomodações filtradas.
Exemplo de categorias suportadas: HOTEL, HOSTEL, APARTMENT, RESORT, VILLA, CABIN, entre outros.

Configuração e Instalação
1. Clonando o Repositório
bash
Copiar código
git clone https://github.com/seu-usuario/hackaton.git
cd hackaton
2. Instalando Dependências
bash
Copiar código
npm install
3. Configuração do Docker
Certifique-se de que o Docker está instalado e execute:

bash
Copiar código
docker-compose up --build
4. Configuração do Arquivo .env
Crie um arquivo .env na raiz do projeto com as variáveis de ambiente necessárias:

env
Copiar código
MYSQL_HOST=localhost
MYSQL_PORT=3306
MYSQL_DATABASE=accommodations
MYSQL_USER=root
MYSQL_PASSWORD=senha

DATABASE_URL="mysql://root:senha@localhost:3306/accommodations"
NODE_ENV=development
Se estiver utilizando o Aiven para hospedar o banco de dados, substitua DATABASE_URL pela URL fornecida no painel do Aiven.

Comandos Úteis
Iniciar a aplicação: npm run start:dev
Executar migrações: npx prisma migrate dev
Abrir Prisma Studio: npx prisma studio
Rodar o Docker: docker-compose up --build
Configuração do Banco de Dados com Prisma
1. Migrando o Banco de Dados
bash
Copiar código
npx prisma migrate dev
2. Utilizando o Prisma Studio
bash
Copiar código
npx prisma studio
Isso abrirá o Prisma Studio no navegador, permitindo visualizar e manipular os dados no banco de dados.

Executando a API
A aplicação estará disponível em:

text
Copiar código
http://localhost:3333
Dependências do Projeto
@nestjs/core, @nestjs/common, @nestjs/platform-express: Framework NestJS.
@prisma/client: Cliente Prisma para manipulação do banco de dados.
dotenv: Gerenciamento de variáveis de ambiente.
axios: Requisições HTTP.
rxjs: Programação reativa.
Dependências de Desenvolvimento:

prisma: Migrações e cliente Prisma.
eslint: Qualidade de código.
typescript: Compilação TypeScript.
Contribuição
Contribuições são bem-vindas! Faça um fork, implemente suas alterações e envie um pull request.






Dito por si:
adicione o deploy ao readme https://hackaton-onfly.onrender.com
Dito pelo ChatGPT:
ChatGPT
Hackaton API - Onfly Challenge
Este projeto foi desenvolvido como uma solução para um desafio da Onfly, com o objetivo de criar um filtro eficiente para categorias de acomodações. A API permite gerenciar acomodações e oferece funcionalidades como listagem, busca por categorias e localização.

Acesso ao Deploy
A API está disponível no seguinte link:

Hackaton API - Onfly

Desafio: Filtro por Categorias de Acomodações
A Onfly enfrentava dificuldades para implementar um filtro eficiente para categorias de acomodações, dificultando a busca por opções específicas como hotéis, hostels, apartamentos, entre outros. A solução desenvolvida implementa:

Validação de Categorias: Definição de categorias válidas no código, como HOTEL, APARTMENT, HOSTEL, entre outras, evitando buscas incorretas.
Busca Personalizada: Utilização do Prisma ORM para consultar o banco de dados e retornar acomodações que correspondem à categoria solicitada.
Formatação dos Dados: Conversão dos resultados do banco de dados em um formato estruturado, incluindo cálculo de avaliações médias e listagem de benefícios.
Essa abordagem garante que os usuários possam filtrar acomodações com rapidez e precisão.

Tecnologias Utilizadas
NestJS: Framework Node.js para criação de APIs modulares e escaláveis.
Prisma ORM: Ferramenta poderosa para manipulação de banco de dados relacional.
MySQL: Banco de dados relacional utilizado para armazenar as acomodações.
Aiven: Plataforma de dados em nuvem para hospedagem do banco de dados.
Docker: Facilita o deploy e a replicação do ambiente de desenvolvimento.
Axios: Realiza integrações com APIs externas, como a geolocalização baseada em CEP.
Como Cada Tecnologia Foi Usada
NestJS: Estruturou a lógica de negócio em módulos, serviços e controladores, seguindo princípios como injeção de dependência.
Prisma ORM: Realizou consultas otimizadas no banco de dados para buscar acomodações e categorias.
MySQL: Armazenou os dados relacionados às acomodações, como tipo, localização, avaliações e benefícios.
Axios: Integrado à API do OpenCage para geocodificação baseada em CEP.
Docker: Gerou containers para a aplicação e o banco de dados, criando um ambiente padronizado para desenvolvimento e produção.
Lógica Implementada para o Filtro
Entrada do Usuário: A API recebe a categoria desejada como parâmetro.
Validação da Categoria: Verifica se a categoria informada pertence a uma lista pré-definida.
Consulta ao Banco de Dados: Utiliza o Prisma ORM para buscar acomodações que correspondem à categoria válida.
Formatação da Resposta: Cada acomodação é processada para incluir:
Avaliação média calculada com base nas reviews.
Benefícios convertidos de JSON para uma lista compreensível.
Dados de localização e descrição.
Resposta Final: A API retorna uma lista formatada das acomodações filtradas.
Exemplo de categorias suportadas: HOTEL, HOSTEL, APARTMENT, RESORT, VILLA, CABIN, entre outros.

Configuração e Instalação
1. Clonando o Repositório
bash
Copiar código
git clone https://github.com/seu-usuario/hackaton.git
cd hackaton
2. Instalando Dependências
bash
Copiar código
npm install
3. Configuração do Docker
Certifique-se de que o Docker está instalado e execute:

bash
Copiar código
docker-compose up --build
4. Configuração do Arquivo .env
Crie um arquivo .env na raiz do projeto com as variáveis de ambiente necessárias:

env
Copiar código
MYSQL_HOST=localhost
MYSQL_PORT=3306
MYSQL_DATABASE=accommodations
MYSQL_USER=root
MYSQL_PASSWORD=senha

DATABASE_URL="mysql://root:senha@localhost:3306/accommodations"
NODE_ENV=development
Se estiver utilizando o Aiven para hospedar o banco de dados, substitua DATABASE_URL pela URL fornecida no painel do Aiven.

Comandos Úteis
Iniciar a aplicação: npm run start:dev
Executar migrações: npx prisma migrate dev
Abrir Prisma Studio: npx prisma studio
Rodar o Docker: docker-compose up --build
Configuração do Banco de Dados com Prisma
1. Migrando o Banco de Dados
bash
Copiar código
npx prisma migrate dev
2. Utilizando o Prisma Studio
bash
Copiar código
npx prisma studio
Isso abrirá o Prisma Studio no navegador, permitindo visualizar e manipular os dados no banco de dados.

Executando a API
Se estiver rodando localmente, a aplicação estará disponível em:

text
Copiar código
http://localhost:3333
Dependências do Projeto
@nestjs/core, @nestjs/common, @nestjs/platform-express: Framework NestJS.
@prisma/client: Cliente Prisma para manipulação do banco de dados.
dotenv: Gerenciamento de variáveis de ambiente.
axios: Requisições HTTP.
rxjs: Programação reativa.
Dependências de Desenvolvimento:

prisma: Migrações e cliente Prisma.
eslint: Qualidade de código.
typescript: Compilação TypeScript.
Contribuição
Contribuições são bem-vindas! Faça um fork, implemente suas alterações e envie um pull request.