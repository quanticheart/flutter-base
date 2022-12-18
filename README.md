# Flutter - Projeto Base

Este é com intuito de ser base para criação de outros apps Flutter.

## Parâmetros de Terminal 
Após seguir a [documentação](https://docs.flutter.dev/get-started/install) e instalar o Flutter no seu ambiente de trabalho. pode ver as opções com:

```agsl
flutter create --help
```

isso vai listar

- ``--[no-]pub`` : Se o "flutter pub get" deve ser executado após a criação do projeto. (o padrão é ativado)

- ``--[no-]offline`` : Quando "flutter pub get" é executado pelo comando create, isso indica se deve ser executado no modo offline ou não. No modo offline, ele precisará ter todas as dependências já disponíveis no cache do pub para ter sucesso.

- ``--[no-]with-driver-test``: Adicione também uma dependência flutter_driver e gere um exemplo de teste 'flutter drive'.

- ``-t , --template=≶type>`` : Especifique o tipo de projeto a ser criado:

``[app] (Padrão) Gera um App Flutter.``

``[package] Gere um projeto Flutter compartilhável contendo código Dart modular.``

``[plugin] Gere um projeto Flutter compartilhável contendo uma API em código Dart com uma implementação específica da plataforma para Android, iOS ou ambos.``

- ``-s , --sample=<id>`` : especifica o exemplo de código Flutter a ser usado como main.dart para um aplicativo. Implica --template=app. O valor deve ser o ID da amostra desejada no site de [documentação da API](http://docs.flutter.dev). Um exemplo pode ser encontrado no [master-api](https://master-api.flutter.dev/flutter/widgets/SingleChildScrollView-class.html)

- ``--list-samples=<path>`` : especifica um arquivo de saída JSON para uma listagem de amostras de código Flutter que podem ser criadas com --sample.

- ``--[no-]overwrite`` : Ao executar operações, sobrescrever arquivos existentes.

- ``--description`` A descrição a ser usada para seu novo projeto Flutter. Essa string termina no arquivo pubspec.yaml. (o padrão é "Um novo projeto do Flutter".)

- ``--org`` : a organização responsável pelo seu novo projeto Flutter, em notação reversa de nome de domínio. Essa string é usada em nomes de pacotes Java e como prefixo no identificador de pacote iOS. (o padrão é "com.example")

- ``--project-name`` : o nome do projeto para este novo projeto do Flutter. Este deve ser um nome de pacote de dardo válido.

- ``-i , --ios-language`` : [objc, swift(padrão)]

- ``-a , --android-language`` : [java, kotlin(padrão)]

- ``--[no-]androidx`` : Gere um projeto usando as bibliotecas de suporte do AndroidX

## Criando um projeto


para criar um projeto Flutter simples, execute:

```agsl
flutter create --org com.yourdomain project_name
```

a ***--org*** é a configuração do seu **applicationId / Bundle Identifier** base, que é seguido pelo nome do projeto, que deve ser sempre escrito com letras minúscula e se houver, Underlines como separadores de palavras,
o código acima gerará um app com o seguindo **applicationId / Bundle Identifier**: ``com.yourdomain.project_name``

é possível validar os **applicationId / Bundle Identifier** em:

- Android - applicationId

[build.gradle](android%2Fapp%2Fbuild.gradle) em android/app/ 
```
defaultConfig {
    applicationId "com.yourdomain.project_name"
    
```

- IOS - Bundle Identifier em:

[Info.plist](ios%2FRunner%2FInfo.plist) em ios/Runner/
```agsl
<key>CFBundleIdentifier</key>
<string>com.yourdomain.project_name</string>
```

## Renomeando um projeto Existente

caso deseje mudar o **applicationId / Bundle Identifier** de um projeto existente, use a Lib [Rename](https://pub.dev/packages/rename):

- instalando:
```agsl
flutter pub global activate rename
```

- renomeando o **applicationId / Bundle Identifier**:
```agsl
flutter pub global run rename --bundleId com.example.android.app
```

- renomeando o titulo do aplicativo:
```
flutter pub global run rename --appname "Network Upp"
```

## Mudando os Icones

Cada novo aplicativo flutter vem com um logotipo flutter como padrão, para modificar, faça:

- Android e iOS:

Acesse [appicon.co](https://www.appicon.co/), que facilitará a criação dos ícones, carregue o ícone do aplicativo como uma imagem.

O tamanho (1024 x 1024) é recomendado e certifique-se de marcar a caixa de seleção de acordo com seus requisitos: Android, iPhone e iPad.

![1.png](images%2F1.png)

Após o download e extração do arquivo .zip,copie o conteúdo da pasta android e no projeto flutter, 
abra a pasta **(projeto > android > app > src > main > res)**, e cole todas as pastas mipmap.

Volte para os arquivos baixados e copie a pasta Assets.xcassets para a pasta de recursos do iOS do seu projeto **(projeto > ios > Runner)**

- Android: suporte a ícones redondos

Para adicionar suporte a ícones redondos, Volte em [appicon.co](https://www.appicon.co/),
carregue uma imagem com uma forma redonda e selecione apenas a caixa de seleção Android e escreva o nome do arquivo como “round_launcher” e clique em gerar.

![Captura de Tela 2022-12-16 às 10.51.43.png](images%2FCaptura%20de%20Tela%202022-12-16%20%C3%A0s%2010.51.43.png)

Após isso, Uma vez baixado, copie a pasta android novamente e cole os recursos android do seu projeto. **(projeto > android > app > src > main > res)**.

Por último, vá para o arquivo Android Manifest (projeto > android > app > src > main > AndroidManifest.xml) e adicione esta linha:

![Captura de Tela 2022-12-16 às 10.54.32.png](images%2FCaptura%20de%20Tela%202022-12-16%20%C3%A0s%2010.54.32.png)

- Web 

Acesse [favicon-generator](https://www.favicon-generator.org/), Selecione o icone que vc desejar e clique em Create Favicon, uma tela como esta, irá surgir:

![Captura de Tela 2022-12-16 às 10.59.13.png](images%2FCaptura%20de%20Tela%202022-12-16%20%C3%A0s%2010.59.13.png)

Click em **Download the generate favicon**, extraia o .zip, e copie todo o conteudo para a pasta **(projeto > web)**, depois, abra o arquivo **index.html**, e substitua isto:

![Captura de Tela 2022-12-16 às 11.04.59.png](images%2FCaptura%20de%20Tela%202022-12-16%20%C3%A0s%2011.04.59.png)

pelo codigo gerando pelo site, desta maneira:

![Captura de Tela 2022-12-16 às 11.08.40.png](images%2FCaptura%20de%20Tela%202022-12-16%20%C3%A0s%2011.08.40.png)

- Windows

acesse [redketchup](https://redketchup.io/icon-converter), click em Browser e selecione seu icone, após isso, vá até a sessão configurações, e deixe assim: 

![Captura de Tela 2022-12-16 às 11.37.40.png](images%2FCaptura%20de%20Tela%202022-12-16%20%C3%A0s%2011.37.40.png)

não esqueça de colocar o file name como "app_icon" e deixar o image format como "PNG", Click em Download > Download.

Agora vá até **(projeto > windows > Runner > resources)** e substitua app_icon.ico pelo seu arquivo .ico.

Se não funcionar, reinicie o Android Studio, execute a limpeza do flutter e reconstrua o aplicativo.

- Mac OS:

Alterar o ícone do aplicativo macOS é muito semelhante ao que fizemos no iOS e Android, acesse [appicon.co](https://www.appicon.co/) e carregue seu ícone como uma imagem (recomenda-se 1024 x 1024), e deixe assim:

![Captura de Tela 2022-12-16 às 11.43.37.png](images%2FCaptura%20de%20Tela%202022-12-16%20%C3%A0s%2011.43.37.png)

Após download e extração, copie a pasta **Assets.xcassets** e cole-o em seu **(projeto > macOS > Runner)**

- Alternativa

vc também pode usar [flutter_launcher_icons](https://pub.dev/packages/flutter_launcher_icons)

## Gerando Aplicativos

- Android

[Doc Oficial](https://docs.flutter.dev/deployment/android)

- Ios

[Doc Oficial](https://docs.flutter.dev/deployment/ios)

- Web

[Doc Oficial](https://docs.flutter.dev/deployment/web)

- MacOS

[Doc Oficial](https://docs.flutter.dev/deployment/macos)

[Create .dmg](https://retroportalstudio.medium.com/creating-dmg-file-for-flutter-macos-apps-e448ff1cb0f)

- Linux

[Doc Oficial](https://docs.flutter.dev/deployment/linux)

[Create .deb](https://pub.dev/packages/flutter_to_debian)

- Windows

[Doc Oficial](https://docs.flutter.dev/deployment/windows)

[Create .exe](https://retroportalstudio.medium.com/creating-exe-executable-file-for-flutter-desktop-apps-windows-ea7c338465e)
