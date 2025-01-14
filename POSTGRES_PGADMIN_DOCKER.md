# Configuração do PostgreSql e PgAdmin usando Docker

Esse tutorial pode ser usado para configurar dois containers Docker, um com o PostgreSql e outro com o PgAdmin, sem necessidade de instalar as ferramentas na máquina:

1. Primeiro precisamos criar um rede no Docker para podermos conectar os dois containers. Para isso, usamos o comando:

`docker network create NOME_DA_REDE`

2. Em seguida, criamos o primeiro container, com postgresql, usado o comando:

`docker run --name NOME_DO_CONTAINER_1 -p 5432:5432 -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres -e POSTGRES_DB=library -d --network NOME_DA_REDE postgres:16.3`

Parâmetros usados no comando:

* **--name**: nome do container
* **-p**: mapeamento das portas, no caso estamos fazendo a porta 5432 da máquina ser mapeada para a porta 5432 do container
* **-e**: variáveis de ambiente passadas para o container:
  - **POSTGRES_PASSWORD**: senha do banco de dados
  - **POSTGRES_USER**: usuário do banco de dados
  -  **POSTGRES_DB**: nome do banco de dados
* **-d**: executa o container em background, deixando o terminal livre após a execução do comando
* **--network**: conecta o container a uma rede
* Por fim, temos a imagem usada para criação do container, nesse caso, foi usada a imagem `postgres:16.3`

3. O terceiro passo consiste em criar o container com o PgAdmin usando o comando:

`docker run --name NOME_DO_CONTAINER_2 -p 15432:80 -e PGADMIN_DEFAULT_EMAIL=admin@admin.com -e PGADMIN_DEFAULT_PASSWORD=admin -d --network library-network dpage/pgadmin4:8.9`

* **--name**: nome do container
* **-p**: mapeamento das portas, no caso estamos fazendo a porta 15432 da máquina ser mapeada para a porta 5432 do container
* **-e**: variáveis de ambiente passadas para o container:
  - **PGADMIN_DEFAULT_EMAIL**: é o endereço de e-mail usado ao configurar a conta de administrador inicial para efetuar login no pgAdmin
  - **PGADMIN_DEFAULT_PASSWORD**: é a senha usada ao configurar a conta de administrador inicial para efetuar login no pgAdmin.
* **-d**: executa o container em background, deixando o terminal livre após a execução do comando
* **--network**: conecta o container a uma rede
* Por fim, temos a imagem usada para criação do container, nesse caso, foi usada a imagem `dpage/pgadmin4:8.9`

4. Agora podemos acessar o pgAdmin pela url: `http://localhost:15432` e realizar o login com os valores passados nas variáveis da ambiente **PGADMIN_DEFAULT_EMAIL** e **PGADMIN_DEFAULT_PASSWORD**

OBS: Ao criar um novo servidor para se conectar ao banco em execução no primeiro container, é importante se atentar a usar o nome do container no campo **Host name/address**, 
assim a rede do docker vai fazer esse mapeamento, apontando para o container desejado.
