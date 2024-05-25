* def::**NOSQL**: **N**ot **O**nly **SQL**
* útil para trabalhar com grandes conjuntos de dados distribuídos
* def::[CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem): distributed data store can provide only two of the following three guarantees
	* **C**onsistency: every read receives the most recent write or an error
	* **A**vailability: every request receives a non-error response, without the guarantee that it contains the most recent write
	* **P**artition Tolerancy: the system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes
* def::**BASE** (Basically Available, Soft State, Eventual Consistency): modelo em contraposição ao ACID
	* ok parte dos nós ficar disponível e outras não
	* ok confirmar operações mesmo que não estejam replicadas em todos nós
	* concorrência otimista, diferente da concorrência pessimista do ACID
* **Modelos de dados**:
	* **Chave-valor**:
		* cada chave associada a um único valor + operações simples
		* tool::**Redis** (**Re**mote **Di**ctionary **S**erver)
			* "*Redis can be used as a database, cache, streaming engine, message broker, and more*"
		* tool::**Dynamo** (Amazon)
			* serverless
			* PartiQL - parece com HQL para consultar nested collections
		* { Riak, GenieDB, Oracle BerkeleyBD }
	* **Documento**:
		* documento = objeto com ID e conjunto de campos, mas sem esquema rígido
		* permite recuperação parcial do documento
		* tool::**MongoDB**:
			* todo documento tem um ID único, \_id, que funciona como PK - se não for informado, o servidor gera automaticamente
			* operações atômicas a nível de documento -> caso queira fazer alteração em múltiplos documentos de forma atômica, necessário usar transação distribuída
			* !CP - Consistent e Partition Tolerant
			* **Query**:
				* {} -> todos documentos da coleção
				* {"status": "OK"} -> select * from colecao where status = 'OK'
				* {"status": {$in: \["OK", "NOK"\]}} -> select * from colecao where status in ('OK', 'NOK')
				* AND -> basta adicionar mais filtros no documento passado
				* OR -> {$or: \[ {"status": "OK"}, {"status": "NOK"}\]}
				* {"casa.numero": 123} -> consulta em documento embedded
				* $lt, $gt, $all, $elemMatch
				* {"lista.1": 10} -> segundo item da lista é 10
				* projeção -> passa como segundo parâmetro um documento com os fields a retornar, com valor 1; \_id é retornado por padrão -> para não retornar, passar na projeção \_id: 0
				* **update**
					* $set, $inc
		* tool::**CouchDB**:
			* "*Seamless multi-master sync, that scales from Big Data to Mobile, with an Intuitive HTTP/JSON API and designed for Reliability.*"
			* Couch Replication Protocol
			* native JSON e binary data + API HTTP
			* suporte para MapReduce
			* !AP - Availability e Partition-Tolerant
	* **Colunar**:
		* estrutura em colunas
		* study_more::operações de leitura/escrita são atômicas
		* **V**:
			* only read relevant data (melhor para ready-mostly/intensive large repositories); 
			* better compression (comprimir colunas, que têm apenas um domínio, menor entropia, é melhor)
		* **DV**: tuple writes require multiple accesses
		* tool::[**Cassandra**](https://cassandra.apache.org/_/cassandra-basics.html)
			* "*Cassandra is a NoSQL distributed database. By design, NoSQL databases are lightweight, open-source, non-relational, and largely distributed. Counted among their strengths are horizontal scalability, distributed architectures, and a flexible approach to schema definition. NoSQL databases enable rapid, ad-hoc organization and analysis of extremely high-volume, disparate data types. That’s become more important in recent years, with the advent of Big Data and the need to rapidly scale databases in the cloud*"
			* next_step::protocolo p2p gossip, para comunicação entre os nós
			* arquitetura masterless (todo nó tem autonomia, todo nó pode agir como coordenador)
			* os dados também são distribuídos (os nós possuem um subconjunto dos dados, definido por um esquema de tokens/hash) - replicas
			* !AP - Availability e Partition-Tolerant
				* é preciso configurar um consistency level, indicando quantas réplicas precisam confirmar uma operação para o coordinator confirmar a operação
			* CQL - Cassandra Query Language - similar a SQL, mas joinless
			* conjunto de tabelas são organizados em keyspaces
		* tool::[**HBase**](https://hbase.apache.org/)
			* "*Use Apache HBase™ when you need random, realtime read/write access to your Big Data. This project's goal is the hosting of very large tables -- billions of rows X millions of columns -- atop clusters of commodity hardware. Apache HBase is an open-source, distributed, versioned, non-relational database modeled after Google's Bigtable: A Distributed Storage System for Structured Data by Chang et al. Just as Bigtable leverages the distributed data storage provided by the Google File System, Apache HBase provides Bigtable-like capabilities on top of **H**adoop and HDFS.*"
			* next_step::bloom filter ?qual a relação com o HBase?
			*  !AP - Availability e Partition-Tolerant
			* cada valor em coluna é tripla <column name, valor, timestamp> -> versionamento
		* { HyperTable, BigTable }
	* **Grafos**:
		* estrutura em grafo { nós, relacionamentos, propriedades deles }
		* GQL - Graph Query Language - aprovado o desenvolvimento por comitês que mantêm o padrão SQL
		* **Neo4J**
			* [Cypher](https://neo4j.com/docs/getting-started/cypher-intro/) - linguagem de consulta
				* match (nó)-\[relacionamento\]->(nó)...->(nó {where}) return projeção
				* MATCH (p:Product)-\[:CATEGORY\]->(l:ProductCategory)-\[:PARENT\*0..\] ->  (:ProductCategory {name: "Dairy Products"})
				* () -> anonymous node
				* (p:Person) -> nós com o node label Person, associando à node variable p (não é necessário especificar variable)
				* -->, <--, -- : relacionamento (são dois dashes!) "--" (undirected relationship)
				* \[l:LIKES\] -> relacionamento, LIKES = relationship type, l = relationship variable
				* \[rel:IS_FRIENDS_WITH {since: 2018}\] -> relationship property
		* { ArangoDB, InfoGrid, Infinite Graph, Titan }