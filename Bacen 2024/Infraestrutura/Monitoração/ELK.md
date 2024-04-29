* **Elasticsearch**
	* full-text search and analysis engine, escrito em Java, com api REST API e SQL + QueryDSL
	* considerado um NoSQL, guarda em JSON
	* baseado em Apache Lucene (ferramenta para pesquisa em textos), inicialmente como wrapper sobre o Lucene + { REST, cluster, auth etc }
	* inicialmente open-source, mas houve mudanças de licença recentemente
	* trabalha com clusters -> [nodes](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-node.html) { master, data, ingest etc }
		* master -> não armazena dados, apenas gestão de cluster
		* data -> realiza as pesquisas, agregação e armazenamento
		* ingest -> 
		* nós de acordo com a hotness dos dados -> possível definir políticas para classificar dados de acordo com hotness -> ILM (Index Lifecycle Management)
	* índices -> coleção de documentos! ~ database #anki 
		* sharding -> particionamento, replicando dados em múltiplos nós
		* possível definir Mapping Types, especificando os tipos de valores serão armazenados em dado índice -> era usado para ter múltiplos tipos num mesmo índice -> recomendação atual de ter um índice por tipo
	* inverted index -> mapeamento do conteúdo para as chaves
	* TF-IDF para determinação de relevância
	* ILM (Index Lifecycle Management)
		* período de retenção, transição de índices por performance
		* searchable snapshots
		* async search -> ex: dados que estão cold e podem demorar
		* life cycle { hot, warm, cold, frozen, delete }
	* High Availability
		* um cluster contém múltiplos nós
		* possível configurar o nível de replicação, que envolve um tradeoff entre disponibilidade e consistência
	* Query API
		* ![[Pasted image 20240428220258.png]]
	* Text analysis
		* full text search -> fuzzy queries
		* character filters -> recebe o texto original e aplica transformações; ex { strip filters, HTML strip, }
		* tokenization -> { ngram, by language etc }
		* normalization -> { case, synonyms, stopwords etc }
	* Categorias
		* content -> dados transacionais
		* time series
* **Logstash**
	* 
* **Kibana**
	* 
* 