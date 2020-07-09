# Análise de dados do Twitter
Breve analises de tweets para aprendizado na área de Análise de Dados. O script foi desenvolvido com a utilização da plataforma do Anaconda e no ambiente do Jupyter Notebook.

## Instalação da biblioteca para manipulação da API do twitter utilizando o Anaconda
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
 
## Credenciais para utilização da API do Twitter

Para utilizar a API do twitter, é necessário ter uma conta no twitter, solicitar o acesso de desenvolvedor, criar sua aplicação, gerar suas credenciais.
Para fazer a autenticação da API usando suas credenciais seguindo script:

<pre>
<code>consumer_key = "Sua_API_Key"</code>
<code>consumer_secret = "Sua_API_Secret_Key"</code>
<code>access_token = "Sua_Access_token</code>
<code>access_token_secret = "Sua_Access_token_secret"</code>
</pre>

## Busca de Tweets
**Um sistema implementado para coleta de dados foi através da busca por palavra chave**
Para saber mais como é feita a busca, além da documentação, um método fácil é verificar diretamente na aba de pesquisa do twitter.

**Fazer a busca por palavra**
<pre>
<code>tweets = token.search(keyword, count, result_type)</code>
</pre>

**Onde:**

*keyword*     --> conjunto de palavras chaves
*count*       --> quantidade de tweets a serem retornados
*result_type* --> mixed (default, tweets mixados), recent (tweets recentes), popular (tweets mais populares)
*tweets*      --> variável que irá armazenar todos os tweets

 **Observação:**
 
Fazer a busca por palavra chave, busca o text do tweet truncado:
<pre>
<code>tweets = token.search(q=keyword,lang='pt')</code>
</pre>

Fazer a busca por palavra chave, busca o text do tweet por inteiro:
<pre>
<code>tweets = token.search(q=keyword,tweet_mode='extended')</code>
</pre>

## Análise de polaridade

 Para fazer a **análise de polaridade**, é utilizado a função *sentiment.polarity* do pacote *TextBlob*.
 
 * A função *sentiment.polarity* retornará um número entre -1 e 1, onde quanto maior esse número, menos "chateada" a pessoa que postou está. 
 
 Ou seja, quanto maior esse número mais positivo é o tweet. Pode-se ainda considerar que a polaridade 0 (zero) pode indicar uma neutralidade do tweet.

## Armazenamento dos dados do Twitter
**Armazenar em arquivos:**
Para fazer o armazenamento dos tweets, deve-se ser feito a conversão dos dados para string e depois a deserialização para ficar no formato correto para adicionar
em um arquivo json.

<pre>
<code>json_str = json.dumps(dados._json)</code> --> Conversão para string
<code>parsed = json.loads(json_str)</code> --> Deserialização da string para um objeto com formato json
<code>json.dump(parsed, filename, ensure_ascii, sort_keys, indent, separators)</code> --> Armazena o dado deseroaçozado no arquivo
</pre>

**Onde:**

*filename*     --> destino dos dados (arquivo).
*ensure_ascii* --> para True (o padrão), é garantido que a saída tenha todos os caracteres não ASCII recebidos. Se for False, esses caracteres serão exibidos como estão.
*sort_keys*    --> para True (padra é False), a saída dos dicionários será classificada por chave.
*indent*       --> O argumento é usado para imprimir JSON de maneira bonita para torná-lo mais legível. O padrão é (',', ':'). Para obter a representação JSON mais compacta, você deve usar (',', ':') para eliminar espaços em branco.
*separators*   --> Especificar qualquer separador entre chave e valor.

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
 
