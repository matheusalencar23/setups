# Configuração do MySQL e phpMyAdmin usando Docker

Esse tutorial pode ser usado para configurar dois containers Docker, um com o MySQL e outro com o phpMyAdmin, sem necessidade de instalar as ferramentas diretamente na máquina.

1. Criação da rede Docker

Primeiro, precisamos criar uma rede no Docker para permitir a comunicação entre os containers:

`docker network create NOME_DA_REDE`

2. Criação do container MySQL

Em seguida, criamos o container com o MySQL utilizando o comando abaixo:

```
docker run --name NOME_DO_CONTAINER_1 \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=root \
-e MYSQL_DATABASE=library \
-e MYSQL_USER=user \
-e MYSQL_PASSWORD=password \
-d --network NOME_DA_REDE mysql:8.4
```

Parâmetros usados no comando:

* **--name**: nome do container
* **-p**: mapeamento das portas, no caso estamos mapeando a porta 3306 da máquina para a porta 3306 do container
* **-e**: variáveis de ambiente passadas para o container:
  - **MYSQL_ROOT_PASSWORD**: senha do usuário root do MySQL
  - **MYSQL_DATABASE**: nome do banco de dados que será criado automaticamente
  - **MYSQL_USER**: usuário adicional do banco de dados
  - **MYSQL_PASSWORD**: senha do usuário adicional
* **-d**: executa o container em background
* **--network**: conecta o container a uma rede Docker

Por fim, temos a imagem usada para criação do container, neste caso: mysql:8.4

3. Criação do container phpMyAdmin

Agora, criamos o container com o phpMyAdmin usando o comando:

```
docker run --name NOME_DO_CONTAINER_2 \
-p 8080:80 \
-e PMA_HOST=NOME_DO_CONTAINER_1 \
-e PMA_PORT=3306 \
-d --network NOME_DA_REDE phpmyadmin:5.2
```

Parâmetros usados no comando:

* **--name**: nome do container
* **-p**: mapeamento das portas, neste caso a porta 8080 da máquina é mapeada para a porta 80 do container
* **-e**: variáveis de ambiente passadas para o container:
  - **PMA_HOST**: nome do container MySQL (importante para a comunicação via rede Docker)
  - **PMA_PORT**: porta do MySQL (padrão: 3306)
* **-d**: executa o container em background
* **--network**: conecta o container à mesma rede do MySQL

Imagem utilizada: phpmyadmin:5.2

4. Acessando o phpMyAdmin

Após a criação dos containers, o phpMyAdmin pode ser acessado pela URL:

`http://localhost:8080`

Credenciais de acesso:

Servidor: nome do container MySQL (NOME_DO_CONTAINER_1)

Usuário: root ou o usuário definido em MYSQL_USER

Senha: conforme definido nas variáveis de ambiente

Observação importante

Ao configurar a conexão no phpMyAdmin, não utilize localhost como servidor.
Use sempre o nome do container MySQL, pois a rede do Docker é responsável por resolver esse nome e apontar corretamente para o container do banco de dados.
