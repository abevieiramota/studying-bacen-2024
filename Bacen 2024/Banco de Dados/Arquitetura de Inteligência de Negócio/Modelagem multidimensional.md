* tabelas { fato, dimensão }
* dimensão degenerada -> atributos que poderiam ficar em dimensão, mas ficam na fato (chaves naturais/descritivos)
* factless fact -> servem apenas para indicar ocorrência de evento
* fatos
	* aditivo -> podem ser somados/agregados numericamente
	* semiaditivo -> podem ser somados/agregados numericamente apenas em algumas dimensões
	* não aditivo -> não podem
* modelos
	* estrela
		* fato ligada às dimensões
		* V { simplicidade, desempenho }
		* DV { redundância de dados (nas dimensões), complexidade das atualizações, + espaço de armazenamento }
	* snowflake
		* dimensões são normalizadas
		* V { normalização, flexibilidade (+ facilidade de mudar), otimização de espaço em disco }
		* DV { complexidade, desempenho }
* cubo de dados:  cada eixo representa uma dimensão, células representam valores + hierarquias + operações
* 