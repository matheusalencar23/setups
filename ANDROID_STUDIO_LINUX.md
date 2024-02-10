# Android Studio - Linux

  Esse passo a passo serve para instalação do Android Studio no linux.

  1. Faça o download do Android Studio do site oficial, de preferência no formato `.tar.gz`

  2. Extraia o arquivo baixado e dentro dele vai existir uma pasta chamada `android-studio`

  3. Copie o arquivo para a pasta `/usr/local/lib` usando o comando `mv ~/path_to_the_extracted_folder/android-studio /usr/local/bin`

  4. Agora precisamos criar um lançador/atalho para o android studio
     - Na área de trabalho crie um arquivo chamadao `Android Studio.desktop`
     - Dentro do arquivo cole o seguinte conteúdo
      ```
        [Desktop Entry]
         
        Name=Android_Studio
        
        Exec=/usr/local/lib/android-studio/bin/studio.sh
         
        Icon=/usr/local/lib/android-studio/bin/studio.svg
         
        Terminal=false
         
        Type=Application
      ```
     - Clique com o botão direito no arquivo e procure a opção permitir iniciar
    
  5. Com isso devemos iniciar o Android Studio, quando iniciamos devemos prosseguir com a instalação

  6. Com a instalação finalizada procure pela opção `More Actions > SDK Manager`

  7. Procure pelo campo Android SDK Location, foi onde o SDK do Android foi instalado, copie o valor do campo

  8. Adicione algumas variáveis de ambiente ao arquivo `.bashrc`
    - **export ANDROID_HOME=/home/matheus/Android/Sdk**
    - **export ANDROID_SDK_ROOT=/home/matheus/Android/Sdk**

  9. Voltando ao SDK Manager no Android Studio, na aba SDK Platforms instale algumas versões do Android que deseja usar

  10. Na aba SDK Tools instale o Android SDK Command-line Tools

  11. Adicione mais algumas variáveis de ambiente ao arquivo `.bashrc`
    - **export PATH=$PATH:$ANDROID_HOME/tools/bin**
    - **export PATH=$PATH:$ANDROID_HOME/platform-tools**

  12. Agora devemos criar um máquina virtual em `More Actions > Virtual Device Manager`
