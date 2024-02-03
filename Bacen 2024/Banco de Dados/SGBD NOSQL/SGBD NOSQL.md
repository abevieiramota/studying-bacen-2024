**N**ot **O**nly **SQL**
[[Modelagem NoSQL]]

* útil para trabalhar com grandes conjuntos de dados distribuídos
* [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem)
	* distributed data store can provide only two of the following three guarantees
		* **C**onsistency - every read receives the most recent write or an error
		* **A**vailability - every request receives a non-error response, without the guarantee that it contains the most recent write
		* **P**artition Tolerancy - the system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes
* modelos de dados
	* **chave-valor**
		* cada chave associada a um único valor
		* operações disponíveis são simples
		* **Redis** (**Re**mote **Di**ctionary **S**erver)
			* "*Redis can be used as a database, cache, streaming engine, message broker, and more*"
		* **Dynamo** (Amazon)
			* serverless
			* PartiQL - parece com HQL para consultar nested collections
	* **documento**
		* documento = objeto com ID e conjunto de campos
		* sem esquema
		* permite recuperação parcial do documento
		* **MongoDB**
			* todo documento tem um ID único, que funciona como PK - se não for informado, o servidor gera automaticamente
			* operações atômicas a nível de documento -> caso queira fazer alteração em múltiplos documentos de forma atômica, necessário usar transação distribuída
			* é CP - Consistent e Partition Tolerant
			* queries
				* {} -> todos documentos da coleção
				* {"status": "OK"} -> select * from colecao where status = 'OK'
				* {"status": {$in: ["OK", "NOK"]}} -> select * from colecao where status in ('OK', 'NOK')
				* AND -> basta adicionar mais filtros no documento passado
				* OR -> {$or: [ {"status": "OK"}, {"status": "NOK"}]}
				* {"casa.numero": 123} -> consulta em documento embedded
				* $lt, $gt, $all, $elemMatch
				* {"lista.1": 10} -> segundo item da lista é 10
				* projeção -> passa como segundo parâmetro um documento com os fields a retornar, com valor 1; \_id é retornado por padrão -> para não retornar, passar na projeção \_id: 0
			* update
				* $set, $inc
		* **CouchDB**
			* "*Seamless multi-master sync, that scales from Big Data to Mobile, with an Intuitive HTTP/JSON API and designed for Reliability.*"
			* Couch Replication Protocol
			* native JSON e binary data
			* suporte para MapReduce
			* usa HTTP
			* é AP - Availability e Partition-Tolerant
	* **colunar**
		* estrutura em colunas
		* operações de leitura/escrita são atômicas #n_entendi 
		* V: only read relevant data (melhor para ready-mostly/intensive large repositories); better compression (comprimir colunas, que têm apenas um domínio, menor entropia, é melhor)
		* DV: tuple writes require multiple accesses
		* [**Cassandra**](https://cassandra.apache.org/_/cassandra-basics.html)
			* "*Cassandra is a NoSQL distributed database. By design, NoSQL databases are lightweight, open-source, non-relational, and largely distributed. Counted among their strengths are horizontal scalability, distributed architectures, and a flexible approach to schema definition. NoSQL databases enable rapid, ad-hoc organization and analysis of extremely high-volume, disparate data types. That’s become more important in recent years, with the advent of Big Data and the need to rapidly scale databases in the cloud*"
			* como banco distribuído, normalmente tem vários nós, que se comunicam por um protocolo p2p chamado gossip
			* também possui arquitetura masterless (todo nó tem autonomia, todo nó pode agir como coordenador)
			* os dados também são distribuídos (os nós possuem um subconjunto dos dados, definido por um esquema de tokens/hash) - replicas
			* é AP (Available Partition-tolerant)
				* é preciso configurar um consistency level, indicando quantas réplicas precisam confirmar uma operação para o coordinator confirmar a operação
			* CQL - Cassandra Query Language - similar a SQL, mas joinless
			* conjunto de tabelas são organizados em keyspaces
		* [**HBase**](https://hbase.apache.org/)
			* "*Use Apache HBase™ when you need random, realtime read/write access to your Big Data. This project's goal is the hosting of very large tables -- billions of rows X millions of columns -- atop clusters of commodity hardware. Apache HBase is an open-source, distributed, versioned, non-relational database modeled after Google's Bigtable: A Distributed Storage System for Structured Data by Chang et al. Just as Bigtable leverages the distributed data storage provided by the Google File System, Apache HBase provides Bigtable-like capabilities on top of Hadoop and HDFS.*"
			* Bloom filter
			*  é AP (Available Partition-tolerant)
			* cada valor em coluna é tripla <column name, valor, timestamp>
	* **grafos**
		* registros interconectados
		* estrutura em grafo { nós, relacionamentos, propriedades deles }
		* GQL - Graph Query Language - aprovado o desenvolvimento por comitês que mantêm o padrão SQL
		* **Neo4J**
			* [Cypher](https://neo4j.com/docs/getting-started/cypher-intro/) - linguagem de consulta
				* MATCH (p:Product)-[:CATEGORY]->(l:ProductCategory)-[:PARENT*0..] ->  (:ProductCategory {name: "Dairy Products"})
				* match (nó)-[relacionamento]->(nó)...->(nó {where}) return projeção
				* () anonymous node
				* (p:Person) -> nós com o node label Person, associando à node variable p (não é necessário especificar variable)
				* -->, <--, -- : relacionamento (são dois dashes!) "--" (undirected relationship)
				* [l:LIKES] -> relacionamento, LIKES = relationship type, l = relationship variable
				* [rel:IS_FRIENDS_WITH {since: 2018}] -> relationship property


* links
	* [types of databases](https://timweninger.com/teaching/database-systems-concepts/cap-and-hbase/)
	* 