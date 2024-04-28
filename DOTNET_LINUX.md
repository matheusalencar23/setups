# .Net Linux

  Esse passo a passo serve para instalação do .Net no linux sendo possível a utilização de múltiplas versões.

  1. Se houver alguma versão do .Net instalado é interessante remover.

  2. Faça o download da versão desejada diretamente do site oficial. O arquivo deve estar comprimido, em geral com a extensão `.tar.gz`.

  3. Para descompactar o arquivo execute o comando `tar -xvzf file_name.tar.gz`.

  4. Se não houver, crie uma pasta chamada `dotnet` em `/usr/local/lib`, para isso você pode ir até a pasta usando o comando `cd /usr/local/lib` e executar o comando `mkdir dotnet`.

  5. Mova a pasta extraída para a pasta recém criada, se você estiver na pasta `dotnet` você pode executar o comando `mv ~/path_to_the_extracted_folder/folder_name ./`.

  6. Crie um link da pasta do .Net usando o comando `ln -s folder_name current`.

  7. Configure as variáveis de ambiente adicionando as seguintes linhas no final do arquivo `.bashrc`:
      - **export DOTNET_ROOT=/usr/local/lib/dotnet/current**
      - **export PATH=$PATH:$DOTNET_ROOT**
  
  8. Para instalar outras versões repitas os passos 2, 3, 4 e 5.

  9. Para alternar entre as versões é necessário remover o link `current` usando o comando `unlink current` e criar um novo link da versão desejada como no passo 6.etet
