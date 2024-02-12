#lvl1
Alta escala de
* Volume
* Variedade { estruturado, semi-estruturado (ex: XML, JSON), não estruturado }
* Velocidade
* Valor
* Variabilidade - a semântica dos dados muda frequentemente
* Veracidade - vi questão considerando aqui também a qualidade dos dados...


Tópicos
* MapReduce - modelo de programação para processamento em paralelo
* Desafio à privacidade; policiamento/vigilância
* Ferramentas
	* Hadoop - computação distribuída escalável e segura (detecção e recuperação a falhas etc); não é SGBD
		* HDFS (Hadoop Distributed File System) - sistema de arquivos distribuídos
		* Hadoop Yarn - gerenciamento de cluster e job scheduling
		* Hadoop MapReduce - map reduce com o Yarn
		* Processos: NameNode, DataNode, BackupNode, Checkpoint NameNode #TODO pesquisar
	* BigQuery - serverless DW do Google
	* Spark - compute engine for Hadoop data
	* HBase - distributed database that supports large tables
	* Hive - DW infrastructure that provides data summarization and ad hoc querying; HiveQL, executa consultas com MapReduce
	* Mahout - ML 
	* Apache Storm - distributed realtime computation system
	* MongoDB - document-oriented database system
	* Kafka - open-source distributed event streaming platform
	* Cassandra - multi-master database with no single points of failure
	* Pig - a high-level data-flow language and execution framework for parallel computation; script-like linguagem Pig Latin, traduz para MapReduce
	* Zookeeper - highly reliable distributed coordination
* Escalabilidade { vertical (+ recursos na máquina), horizontal (+ máquinas) }