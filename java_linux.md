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
