* [[SGBD SQL]]
* [[SGBD NOSQL]]
* [[Modelagem de dados]]
* [[Arquitetura de Inteligência de Negócio]]


* Particionamento de tabelas pode ser (pensar na linha que dividirá as partições -> se horizontal, é uma linha dividindo as tuplas)
	* horizontal -> cada partição contém um subconjunto das tuplas
		* primária -> o atributo utilizado na partição pertence à tabela particionada
		* derivada -> o atributo utilizado na partição não pertence à tabela particionada, mas a tabela relacionada a ela
	* vertical -> cada partição contém um subconjunto dos atributos
	* híbrida -> combinação das duas

* #TODO index { relação entre clustered index e fragmentation - ver Q2389088 }