# Análise de dados do Twitter
Breve analises de tweets para aprendizado na área de Análise de Dados. O script foi desenvolvido com a utilização da plataforma do Anaconda e no ambiente do Jupyter Notebook.

## Instalação da biblioteca para manipulação da API do twitter utilizando o Anaconda
**OBSERVAÇÃO:**
 
Antes de usar o tweepy pela primeira vez, **<font color='red'>é necessário instalar o pacote</font>**. Para isso, acesse o prompt do Anaconda e execute o comando:
#### - *conda install -c conda-forge twepy*

 **<font color='red'>SEMPRE é necessário importar</font>**  o(s) pacote(s) que serão usados no script.

Pacotes necessários para utilizar o script: TextBlob (analise de sentimentos), Tweepy (acesso a api) e NumPy.
Tenha certeza que todos os pacotes foram previamente instalados:
#### - *conda install -c conda-forge textblob*   
#### - *conda install -c conda-forge numpy*
 
## Credenciais para utilização da API do Twitter

Para utilizar a API do twitter, é necessário ter uma conta no twitter, solicitar o acesso de desenvolvedor, criar sua aplicação, gerar suas credenciais.
Para fazer a autenticação da API usando suas credenciais seguindo script:

* consumer_key = "Sua_API_Key"
* consumer_secret = "Sua_API_Secret_Key"
* access_token = "Sua_Access_token"
* access_token_secret = "Sua_Access_token_secret"

* auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
* auth.set_access_token(access_token, access_token_secret)
* token = tweepy.API(auth)

## Busca de Tweets
#### Um sistema implementado para coleta de dados foi através da busca por palavra chave
Para saber mais como é feita a busca, além da documentação, um método fácil é verificar diretamente na aba de pesquisa do twitter
#### Fazer a busca por palavra
tweets = token.search(keyword, count, result_type

*Onde:*
*keyword*     --> conjunto de palavras chaves
*count*       --> quantidade de tweets a serem retornados
*result_type* --> mixed (default, tweets mixados), recent (tweets recentes), popular (tweets mais populares)
*tweets*      --> variável que irá armazenar todos os tweets

 **Observação:**
 
 Fazer a busca por palavra chave, busca o text do tweet truncado:
 * tweets = token.search(q=keyword,lang='pt')
 
Fazer a busca por palavra chave, busca o text do tweet por inteiro:
 * tweets = token.search(q=keyword,tweet_mode='extended')

## Análise de polaridade

 Para fazer a **análise de polaridade**, é utilizado a função *sentiment.polarity* do pacote *TextBlob*.
 
 * A função *sentiment.polarity* retornará um número entre -1 e 1, onde quanto maior esse número, menos "chateada" a pessoa que postou está. 
 
 Ou seja, quanto maior esse número mais positivo é o tweet. Pode-se ainda considerar que a polaridade 0 (zero) pode indicar uma neutralidade do tweet.
