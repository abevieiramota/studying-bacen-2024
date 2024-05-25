* [[SGBD SQL]]
* [[SGBD NOSQL]]
* [[Modelagem de dados]]
* [[Arquitetura de Inteligência de Negócio]]

* anki::Tipos de **Particionamento de tabelas**
	* pensar na linha que dividirá as partições -> se horizontal, é uma linha dividindo as tuplas
	* **horizontal**: cada partição contém um subconjunto das tuplas
		* **primária**: o atributo utilizado na partição pertence à tabela particionada
		* **derivada**: o atributo utilizado na partição não pertence à tabela particionada, mas a tabela relacionada a ela
	* **vertical**: cada partição contém um subconjunto dos atributos
	* **híbrida**: combinação das duas
* next_step::**Indexing**
	* { btree, bitmap, hash, clustered index, gin, framentation }
* todo::**Backup**