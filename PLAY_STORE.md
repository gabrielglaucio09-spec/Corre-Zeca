# Publicar o Corre, Zeca! na Google Play

## 1. Conta de desenvolvedor
- Crie a conta no Google Play Console (taxa única de US$ 25) e conclua a verificação de identidade.
- Contas pessoais novas precisam de um teste fechado com pelo menos 12 testers inscritos por 14 dias seguidos antes de pedir acesso à produção.

## 2. Gerar a chave de assinatura (uma vez só)
    keytool -genkeypair -v -keystore release.jks -alias correzeca -keyalg RSA -keysize 2048 -validity 10000
Guarde o arquivo e as senhas em local seguro. Não envie o `release.jks` para o GitHub.

## 3. Gerar o AAB pelo GitHub Actions
No repositório, em Settings > Secrets and variables > Actions, crie:
- KEYSTORE_BASE64: conteúdo de `base64 -w0 release.jks`
- KEYSTORE_PASSWORD, KEY_ALIAS (correzeca) e KEY_PASSWORD
Depois abra Actions > "Gerar AAB para a Play Store" > Run workflow e baixe o artefato `corre-zeca-aab` (arquivo `app-release.aab`).
A cada nova versão, aumente `versionCode` em `app/build.gradle`.

## 3b. Requisito de versão do Android
Desde 31/08/2026, apps novos precisam ter targetSdk 36 (Android 16). O projeto já está configurado assim.

## 4. Criar o app no Play Console
1. Criar app: nome, idioma (Português do Brasil), tipo Jogo, gratuito ou pago.
2. Ativar o Play App Signing e enviar o `.aab` em uma faixa de teste fechado.
3. Preencher: classificação indicativa, público-alvo, formulário de segurança dos dados e política de privacidade (URL pública).
4. Ficha da loja: ícone 512x512, imagem de destaque 1024x500 e pelo menos 2 capturas de tela (pasta play-store-assets).
5. Depois dos 14 dias de teste com 12 testers, solicite o acesso à produção e envie para análise.
