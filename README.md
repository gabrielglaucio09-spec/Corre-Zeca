# Corre, Zeca! (Android)

Projeto Android nativo que abre o jogo dentro de uma WebView, em tela cheia e na horizontal.
O jogo fica em `app/src/main/assets/index.html`. Não há dependências além do Android Gradle Plugin.

## Gerar o APK sem instalar nada (GitHub Actions)

1. Crie um repositório no GitHub e envie esta pasta inteira (inclusive `.github`).
2. Abra a aba **Actions** do repositório. O workflow "Gerar APK" roda sozinho a cada push, ou clique em **Run workflow**.
3. Quando terminar (uns 3 a 5 minutos), abra a execução e baixe o artefato **corre-zeca-apk**. Dentro está o `app-debug.apk`.
4. Copie o APK para o celular e instale. O Android vai pedir para permitir instalar de fontes desconhecidas.

## Gerar o APK no seu computador

Com Android Studio: **File > Open**, escolha esta pasta e use **Build > Build APK(s)**.
Pela linha de comando (JDK 17 e Android SDK instalados): `gradle assembleDebug`.
O arquivo sai em `app/build/outputs/apk/debug/app-debug.apk`.

## Publicar na Play Store

O APK de debug serve para instalar e testar. Para a loja é preciso um pacote assinado:
crie uma chave (keystore) e rode `gradle bundleRelease` para gerar o `.aab`.

## Observações

- A fonte Bungee é carregada do Google Fonts. Sem internet o jogo usa uma fonte de reserva e continua funcionando.
- O botão Voltar pausa o jogo. Dois toques seguidos fecham o app.
- Para atualizar o jogo, troque o `index.html` em `app/src/main/assets` e gere o APK de novo.
