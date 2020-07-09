# dataAnalysisTwitter
Breve analises de tweets para aprendizado na área de Analise de Dados. 

## Instalação da biblioteca para manipulação da API do twitter
**OBSERVAÇÃO:**
 
Antes de usar o tweepy pela primeira vez, **<font color='red'>é necessário instalar o pacote</font>**. Para isso, acesse o prompt do Anaconda e execute o comando:
#### - *conda install -c conda-forge twepy*

 **<font color='red'>SEMPRE é necessário importar</font>**  o(s) pacote(s) que serão usados no seu script.

 Vamos importar os pacotes que precisaremos usar nessa aplicação: TextBlob (analise de sentimentos), Tweepy (acesso a api) e NumPy
 Tenha certeza que todos os pacotes foram previamente instalados:
 #### - *conda install -c conda-forge textblob*   
 #### - *conda install -c conda-forge numpy*
 
 ### Credenciais para utilização da API do Twitter

Para utilizar a API do twitter, é necessário ter uma conta no twitter, solicitar o acesso de desenvolvedor, criar sua aplicação, gerar suas credenciais.
Fazer autenticação da API usando suas credenciais:

auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)
token = tweepy.API(auth)

# Definir que palavra deseja pesquisar no twitter
# Para saber mais como é feita a busca, além da documentação, um método fácil é verificar diretamente na aba de pesquisa
# do twitter
# Fazer a busca por palavra
# result_type --> mixed (default), recent, popular
# tweets --> variável que irá armazenar todos os tweets
 **Observação:**
 
 Fazer a busca por palavra chave, busca o text do tweet truncado:
 * tweets = token.search(q=keyword,lang='pt')
 
Fazer a busca por palavra chave, busca o text do tweet por inteiro
 * tweets = token.search(q=keyword,tweet_mode='extended')

## <font color=blue>Análise de polaridade</font>

 Para fazer a **análise de polaridade**, vamos usar a função *sentiment.polarity* do pacote *TextBlob*.
 
 * A função *sentiment.polarity* retornará um número entre -1 e 1, onde quanto maior esse número, menos "chateada" a pessoa que postou está. 
 
 Ou seja, quanto maior esse número mais positivo é o tweet. Podemos ainda considerar que a polaridade 0 (zero) pode indicar uma neutralidade do tweet.
