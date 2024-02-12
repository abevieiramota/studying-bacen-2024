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
		* Hadoop Yarn (Yeat Another Resource Negotiator) - gerenciamento de cluster e job scheduling
		* Hadoop MapReduce - map reduce com o Yarn
		* Processos: NameNode, DataNode, BackupNode, Checkpoint NameNode #TODO pesquisar
		* Apache Oozie - scheduler
		* Apache Ambari - "*Ambari é um framework open source do ecossistema Hadoop, que pode ser usado para a instalação, provisionamento, implantação, gerenciamento e monitoramento de um cluster Hadoop.*"; API RESTful
	* BigQuery - serverless DW do Google
	* Spark - compute engine for Hadoop data
	* HBase - distributed database that supports large tables
	* Hive - DW infrastructure that provides data summarization and ad hoc querying; HiveQL, executa consultas com MapReduce
	* Mahout - ML 
	* MongoDB - document-oriented database system
	* Cassandra - multi-master database with no single points of failure
	* Pig - a high-level data-flow language and execution framework for parallel computation; script-like linguagem Pig Latin, traduz para MapReduce
	* Zookeeper - highly reliable distributed coordination; "*ZooKeeper expõe um conjunto simples de primitivas que aplicações distribuídas podem usar para sincronização, configuração, manutenção, agrupamento e nomeação de recursos para a realização da coordenação, alta disponibilidade e sincronização*"
	* Ingestão
		* Apache Storm - distributed realtime computation system
		* Kafka - open-source distributed event streaming platform; { tópicos, broker - responsável por gerir e replicar mensagens (líder/réplica), producer, consumer }
		* Apache Sqoop - ingestão entre sistemas NoSQL/SQL, usando drivers JDBC
		* Apache Flume -ingestão de dados de eventos no HDFS e outros destinos; orientado a agentes, que rodam em JVM { source, channel, sink }, configurando com um arquivo properties
		* NiFi - automatização de fluxos de dados entre sistemas (Programação Baseada em Fluxo); API HTTP; monitora data provenance/lineage
* Escalabilidade { vertical (+ recursos na máquina), horizontal (+ máquinas) }