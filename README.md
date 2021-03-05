Telegram Bot
================
Ana Paula e Gabriel Gouveia
04/03/2021

## Instalacao

Baixe o pacote com:

``` r
install.packages("devtools")
devtools::install_github("ebeneditos/telegram.bot")
```

## Antes do Uso

Para o uso do bot, em primeiro você deve criar um novo bot na sua conta
do telegram, para isso deve falar com o @Botfather,
<https://telegram.me/botfather>, que é o bot gerenciador de bots da
telegram. Se não tiver o telegram instalado pelo computador, fale com o
botfather pelo seu celular.

Primeiro, crie um novo bot:

``` r
/newbot
```

após a criação ele ira pedir um nome para o bot e um user name para o
bot, o user name é como um nick, ou seja é único. Logo que criado um
novo Bot ele irá gerar um TOKEN, e esse TOKEN que você irá usar no seu
script.

Exemplo de token:

``` r
1407985613:AAGy8Fy26n5j3qw-ZIcYUcBM2mFZPh5asdg
```

Agora seu bot está criado no link:

<a href="https:\\t.me/nickdoseuBOT" class="uri">https:\\t.me/nickdoseuBOT</a>

## Uso

Agora com o seu TOKEN criado, vamos ao uso

Adicione a biblioteca ao seu programa

``` r
library(telegram.bot)
```

Exemplo rápido de uso:

``` r
updater <- Updater(token = "TOKEN")
start <- function(bot, update){
  bot$sendMessage(chat_id = update$message$chat_id,
  text = sprintf("Olá %s!", update$message$from$first_name))
}
start_handler <- CommandHandler("start", start)
updater <- updater + start_handler
updater$start_polling()
```

Após rodar esse código, seu bot já estará recebendo um comando /start, e
responderá com

``` r
Olá Seunome!
```

## Algumas funções para implementar

Para criar seus proprios comandos primeiro gere uma função:

``` r
teste <- function(bot, update){
  bot$sendMessage(chat_id = update$message$chat_id,
  text = "testando")## Função para enviar mensagens.
}
```

Onde bot e update são variáveis da biblioteca. a variável bot fica com
as actions da biblioteca e a update com os recieves sobre o chat e
mensagens.

Após isso como você irá chamar essa função para o seu BOT responder

``` r
teste_handler <- CommandHandler("teste", teste)
##comando para verificar se o comando /teste foi chamado
updater <- updater + teste_handler ##atualiza a instância updater
```

E para finalizar e manter o loop de do seu programa, no final coloque a
função

``` r
updater$start_polling()
```
