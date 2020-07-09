# Análise de Sentimento no Twitter</font>

Esse projeto consiste na Análise de sentimentos de tweets coletados através da API do Twitter sobre X. O projeto consiste em:
* Coleta de tweets.
* Identificação de tweets mais curtidos e retweetados.
* Identificação da fonte dos tweets. 
* Análise de sentimentos. 
* Nuvem de palavras mais frequentes. 
* Séries de tweets no tempo. 
* Mapa de calor dos tweets utilizando a localização declarada pelos usuários.
 

##### Instalação dos pacotes

Antes de realizar o desafio será necessário instalar os seguintes pacotes:
* **Geopy:** Usada para definir a geolocalização<br>
<pre>
<code>conda install -c conda-forge geopy</code>
</pre>
* **folium**
<pre>
<code>conda install -c conda-forge folium</code>
</pre>
* **wordcloud:** Usada para gerar uma nuvem de palavras<br>
<pre>
<code>conda install -c conda-forge wordcloud</code>
</pre>
* **pandas**<br>
<pre>
<code>conda install -c anaconda pandas</code>
</pre>
* **googletrans (https://anaconda.org/conda-forge/googletrans)**<br>
<pre>
<code>conda install -c conda-forge googletrans</code>
</pre>
* **unidecode (https://anaconda.org/anaconda/unidecode)**<br>
<pre>
<code>conda install -c anaconda unidecode</code>
</pre>

## Coleta de dados por palavra chave
**Um sistema implementado para coleta de dados foi através da busca por palavra chave.**

 Para saber mais como é feita a busca, além da documentação, um método fácil é verificar diretamente na aba de pesquisa do twitter.
 
 Definir que palavra deseja pesquisar no Twitter
<pre>
<code>keyword = (conjuntoDePalavras)</code>
</pre>

 Para realizar a busca por palavra chave é utilizado a função abaixo:<br>
 <pre>
 <code>API.search(q[, lang][, locale][, rpp][, page][, since_id][, geocode][, show_user])<br></code>
 </pre>
 
 **Onde os principais parâmetros que serão usados são:**
 
 * q - a string de consulta de pesquisa (keyword)
 * lang - Restringe os tweets para o idioma especificado, fornecido por um código ISO 639-1.
 * rpp - O número de tweets a serem retornados por página, até no máximo 100. (count)
 * page - O número da página (começando em 1) a ser retornado, até um máximo de aproximadamente 1500 resultados (com base na página rpp).
 * since_id  - Retorna apenas status com um ID maior que (ou seja, mais recente que) o ID especificado.
 * geocode  - Retorna tweets de usuários localizados em um determinado raio da latitude / longitude especificada.
 * show_user  - Quando verdadeiro, precede "<user>:" no início do tweet. O padrão é falso.
 * result_type - mixed (default, tweets mixados), recent (tweets recentes), popular (tweets mais populares).</p>

 **Observação:**
 
Fazer a busca por palavra chave, busca o text do tweet truncado:
<pre>
<code>tweets = token.search(q=keyword,lang='pt')</code>
</pre>

Fazer a busca por palavra chave, busca o text do tweet por inteiro:
<pre>
<code>tweets = token.search(q=keyword,tweet_mode='extended')</code>
</pre>

## Identificação dos tweets mais curitdos e retweetados
Os dados estão alocados no dataframe construido com a biblioteca pandas. Assim, é possível usar as funções da biblioteca numpy, como a função max, que retorna o maior valor
dos dados que estão em vetor. Por fim, esse processo é utilizado para que se possa verificar os tweets com mais curtidas o retweets através das posições dentro do dataframe.
 
## Identificar fonte de origem dos tweets
Como os proprios tweets trazem a informção da fonte do tweet, é apenas utilizado essa informação e alocado em um vetor que conterá em cada uma de suas posições o tipo da fonte.
Assim é passado por todos os tweets indenticando cada fonte.

## Análise de polaridade para a analise de sentimento

 Para fazer a **análise de polaridade**, é utilizado a função *sentiment.polarity* do pacote *TextBlob*.
 
 * A função *sentiment.polarity* retornará um número entre -1 e 1, onde quanto maior esse número, menos "chateada" a pessoa que postou está. 
 
 Ou seja, quanto maior esse número mais positivo é o tweet. Pode-se ainda considerar que a polaridade 0 (zero) pode indicar uma neutralidade do tweet.
 
## Mapa de colar dos Tweets
É utilizado a função *geolocator.geocode* da bilioteca *Nominatim* para que era formate a latitude a longitude de cada tweet. E por fim, é utilizado os valores retornados da 
latitude e longitude para modelar o mapa través da função *folium.Map*.

## Nuvem de palavras
É primeiro realizado a separação das palavras dos textos dos tweets e a limpeza dos mesmo (retirando simbolos e palavras que não são necessárias). Por fim, utilizado a função
*plt.imshow* para plotar a nuvem de palavras.

## Análise Temporal dos Tweets
Utiliza-se da função *pd.series* para armazenar e organizar o número de tweets por dia. Após isso, é utilizado a função *tlen.plot* para poder construir o gráfico da série.

## Text Mining com o pacote NLTK
Primeiro é feita a tokenização dos tweets através da função *TweetTokenizer* da biblioteca NLTK, ou seja, separado todas as palavras do tweet em um vetor. Após isso é limpado
os tokens, ou seja, retirado simbolos e palavras que não são uteis. E por fim, exibido os dados minerados.
