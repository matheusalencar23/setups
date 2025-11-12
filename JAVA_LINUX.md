# Java Linux

  Esse passo a passo serve para instalação do Java (jdk) no linux sendo possível a utilização de múltiplas versões.

  1. Se houver alguma versão do Java instalado é interessante remover usando o comando `sudo apt-get purge openjdk*`.

  2. Faça o download da versão desejada diretamente do site oficial. O arquivo deve estar comprimido, em geral com a extensão `.tar.gz`.

  3. Para descompactar o arquivo execute o comando `tar -xvzf file_name.tar.gz`.

  4. Se não houver, crie uma pasta chamada `jdk` em `/usr/local/lib`, para isso você pode ir até a pasta usando o comando `cd /usr/local/lib` e executar o comando `mkdir jdk`.

  5. Mova a pasta extraída para a pasta recém criada, se você estiver na pasta `jdk` você pode executar o comando `mv ~/path_to_the_extracted_folder/folder_name ./`.

  6. Crie um link da pasta do jdk usando o comando `ln -s folder_name current`.

  7. Configure as variáveis de ambiente adicionando as seguintes linhas no final do arquivo `.bashrc`:
      - **export JAVA_HOME=/usr/local/lib/jdk/current**
      - **export PATH=$PATH:$JAVA_HOME/bin**
  
  8. Para instalar outras versões repitas os passos 2, 3, 4 e 5.

  9. Para alternar entre as versões é necessário remover o link `current` usando o comando `unlink current` e criar um novo link da versão desejada como no passo 6.

## Automatização para controle de versões instaladas

  1. Criar um arquivo/script com o nome `jvm` e adicionar o conteúdo do [script](https://github.com/matheusalencar23/setups/blob/master/jvm) ou baixar o arquivo na máquina
     - Nota: No script existe a variável `JDK_DIR`, ela deve apontar para o local onde os arquivos `jdk` estão localizado. Se a primeira seção desse passo a passo tiver sido seguida ela já deve estar apontando para o local correto

  2. Para instalá-lo globalmente, coloque o arquivo `jvm` em `/usr/local/bin/`
  
  3. Depois você pode usar os seguintes comandos:
     - `jvm list` - Lista todas as versões disponíveis (destaca a atual com *)
     - `jvm use <versão>` - Troca para a versão especificada
     - `jvm current` - Mostra a versão atual em uso
     - `jvm help` - Mostra ajuda
    
  Nota: O script usa `sudo` internamente para criar o link simbólico, então, dependendo do local onde os arquivos `jdk` estão, você precisará inserir sua senha quando trocar de versão. Se preferir usar sem instalar globalmente, você pode executar diretamente: `path_to_script/jvm`
