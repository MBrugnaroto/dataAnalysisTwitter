# Análise de dados do Twitter
Breve analises de tweets para aprendizado na área de Análise de Dados. O script foi desenvolvido com a utilização da plataforma do Anaconda e no ambiente do Jupyter Notebook.

## Utilização dos scritps:
Cada diretorio contem seu próprio README explincando o seu funcionamento.

## Algumas informações gerais:
 A documentação completa do pacote *tweepy* está disponível no link abaixo:
 * http://docs.tweepy.org/en/v3.5.0/api.html
 
 A documentação do pacote *Matplotlib* no link:
 * https://matplotlib.org/3.1.1/contents.html#
 
 A documentação da função *Nominatim* no link para mapemando de calor dos Tweets:
 * https://geopy.readthedocs.io/en/stable/#nominatim
 
 Para conhecer o pacote Folium veja os links:
 * https://python-visualization.github.io/folium/
 * https://medium.com/@datalivre/folium-d6036a9ad29c

 Para conhecer o pacote WordCloud veja os links:
 * https://amueller.github.io/word_cloud/index.html
 * Exemplos: https://amueller.github.io/word_cloud/auto_examples/index.html#example-gallery

 Para conhecer o pacote *NLTK* (utilizado para Text Mining) veja a documentação completa em:
 * https://www.nltk.org/index.html

### Credenciais para utilização da API do Twitter

Para utilizar a API do twitter, é necessário ter uma conta no twitter, solicitar o acesso de desenvolvedor, criar sua aplicação, gerar suas credenciais.
Para fazer a autenticação da API usando suas credenciais seguindo script:

<pre>
<code>consumer_key = "Sua_API_Key"</code>
<code>consumer_secret = "Sua_API_Secret_Key"</code>
<code>access_token = "Sua_Access_token</code>
<code>access_token_secret = "Sua_Access_token_secret"</code>
</pre>

Autenticação da API:

<pre>
<code>auth = tweepy.OAuthHandler(consumer_key, consumer_secret)</code>
<code>auth.set_access_token(access_token, access_token_secret)</code>
<code>api = tweepy.API(auth, wait_on_rate_limit, wait_on_rate_limit_notify, retry_count)</code>
</pre>

 **Onde:**
 * retry_count - número padrão de tentativas para tentar quando ocorrer um erro
 * retry_delay - número de segundos para aguardar entre tentativas
 * wait_on_rate_limit - se deve ou não esperar automaticamente a reposição dos limites de taxa
 * wait_on_rate_limit_notify - Imprima ou não uma notificação quando o Tweepy estiver aguardando a reposição dos limites de taxa

### Armazenar dados em arquivos JSON através do Python
Para fazer o armazenamento dos tweets, deve-se ser feito a conversão dos dados para string e depois a deserialização para ficar no formato correto para adicionar
em um arquivo json.

<pre>
<code>json_str = json.dumps(dados._json)</code> --> Conversão para string
<code>parsed = json.loads(json_str)</code> --> Deserialização da string para um objeto com formato json
<code>json.dump(parsed, filename, ensure_ascii, sort_keys, indent, separators)</code> --> Armazena o dado deseroaçozado no arquivo
</pre>

**Onde:**

<p>filename     --> destino dos dados (arquivo).</p>
<p>ensure_ascii --> para True (o padrão), é garantido que a saída tenha todos os caracteres não ASCII recebidos. Se for False, esses caracteres serão exibidos como estão.</p>
<p>sort_keys    --> para True (padra é False), a saída dos dicionários será classificada por chave.</p>
<p>indent       --> O argumento é usado para imprimir JSON de maneira bonita para torná-lo mais legível. O padrão é (',', ':'). Para obter a representação JSON mais compacta, <p>você deve usar (',', ':') para eliminar espaços em branco.</p>
<p>separators   --> Especificar qualquer separador entre chave e valor.</p>

