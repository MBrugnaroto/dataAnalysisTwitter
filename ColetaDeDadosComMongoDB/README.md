## Coleta de dados realizada em Python e armazeado no MongoDB (coletaDeDadosDoTwitter_Python)
### Instalação da biblioteca para manipulação da API do twitter utilizando o Anaconda
**Observação:**
 
Antes de usar o tweepy pela primeira vez, **é necessário instalar o pacote**. Para isso, acesse o prompt do Anaconda e execute o comando:
<pre>
<code>conda install -c conda-forge twepy</code>
</pre>

Pacotes necessários para utilizar o script: TextBlob (analise de sentimentos), Tweepy (acesso a api) e NumPy.
Tenha certeza que todos os pacotes foram previamente instalados:
<pre>
<code>conda install -c conda-forge textblob</code>
<code>conda install -c conda-forge numpy</code>
</pre>

### Armazenamento dos dados do Twitter
**Armazenar no MongoDB:**
Deve-se ser feito inicialmente a importação do *pymongo*:
<pre>
<code>import pymongo</code>
</pre>

Após importada, realiza algumas operações necessárias:
<pre>
<code>con = pymongo.MongoClient(host, port)</code> --> Conexão com o banco de dados
<code>db = con.nomeDoBanco</code> --> Seleciona o banco de dados
<code>collection = db.nomeDaColeção</code> --> Seleciona a coleção para armazenar os dados
</pre>

Para inserir os dados:
<pre>
<code>collection.insert_one(dados._json)</code>
</pre>

## Coleta de dados realizada em R e armazeado no MongoDB (coletaDeDadosDoTwitter_R)
### Instalação da biblioteca para manipulação da API do twitter utilizando o Anaconda
Antes de usar o rtweet pela primeira vez, **é necessário instalar o pacote**. Para isso, você pode executar o comando no scritp:
<pre>
<code>install.packages("rtweet")</code>
</pre>

Pacotes necessários para utilizar o script: maps (plot do mapa com as origens dos tweets) e rtweet (acesso a api).
Tenha certeza que todos os pacotes foram previamente importados:
<pre>
<code>library(rtweet)</code>
<code>library(maps)</code>
</pre>

### Autenticação da API:
<pre>
<code>token <- create_token(app = "nomeDoProjeto", consumer_key, consumer_secret,access_token, access_secret)</code>
</pre>

### Busca de Tweets

**Fazer a busca por palavra**
<pre>
<code>screen_name <- "palavraChave"</code>
<code>tweets <- get_timeline(screen_name, n = 1000, include_rts = TRUE, exclude_replies = TRUE)</code>
</pre>

**Onde:**
* n - número de tweets retornados.
* include_rts - incluir (True) ou não (False) os retweets.
* exclude_replies - incluir (True) ou não (false) as respostas dos tweets.

**Fazer a busca por hastags**
<pre>
<code>search.string <- c("#ficaemcasa OR #coronavirus OR #covid OR #covid-19 or #covid19")</code>
<code>type = "mixed"</code>
<code>tweets <- search_tweets(search.string, n, lang, type, include_rts, retryonratelimit)</code>
</pre>

**Onde:**
* search.string - conjunto de palavras chaves (hastags) em formato de string
* lang - linguagem dos Tweets.
* type - mixed (default, tweets mixados), recent (tweets recentes), popular (tweets mais populares).
* include_rts - usado para indicar se inclui (TRUE) retweeets ou não (FALSE) na pesquisa.
* retryonratelimit - usado para indicar se continua (TRUE) ou não (FALSE) depois do limite de 18000 tweets.


### Armazenamento dos dados do Twitter
**Armazenar em arquivos:**
<pre>
<code>write_as_csv(dados, "diretorio/nomeDoArquivo.csv", fileEncoding = "latin1//TRANSLIT")</code>
<code>write.table(dados, "diretorio/nomeDoArquivo.txt", fileEncoding = "latin1//TRANSLIT")</code>
</pre>
