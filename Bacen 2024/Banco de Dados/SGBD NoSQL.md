**N**ot **O**nly **SQL**

* útil para trabalhar com grandes conjuntos de dados distribuídos
* modelos de dados
	* **chave-valor**
		* cada chave associada a um único valor
		* operações disponíveis são simples
		* Redis (Remote Dictionary Server)
			* "*Redis can be used as a database, cache, streaming engine, message broker, and more*"
		* Dynamo (Amazon)
	* **documento**
		* documento = objeto com ID e conjunto de campos
		* sem esquema
		* permite recuperação parcial do documento
		* MongoDB
			* todo documento tem um ID único, que funciona como PK - se não for informado, o servidor gera automaticamente
			* operações atômicas a nível de documento -> caso queira fazer alteração em múltiplos documentos de forma atômica, necessário usar transação distribuída
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
		* CouchDB
	* **colunar**
		* estrutura em colunas
		* operações de leitura/escrita são atômicas #n_entendi 
		* ex: Cassandra, HBase
	* **grafos**
		* registros interconectados
		* estrutura em grafo { nós, relacionamentos, propriedades deles }
		* ex: Neo4J, Infinite Graph
* 