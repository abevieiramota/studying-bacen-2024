* **Tabelas**: { fato, dimensão }
* def::**Dimensão degenerada**: atributos que poderiam ficar em dimensão, mas ficam na fato (chaves naturais/descritivos)
* def::**Minidimensão**: forma de reduzir o volume de registros em uma dimensão grande/com muitas atualizações, mantendo na minidimensão os atributos que mudam com frequência, e na dimensão os que não mudam muito
* def::**Factless fact**: servem apenas para indicar ocorrência de evento -> é possível verificar, por meio de um difference/minus, a não ocorrência de eventos
* def::**Roleplaying dimension**: usar uma mesma dimensão com papéis diferentes (ex: dim_data como dim_aniversario)
* **Tipos de medidas na fato**:
	* **Aditiva**: podem ser somados/agregados numericamente
	* **Semiaditiva**: podem ser somados/agregados numericamente apenas em algumas dimensões
	* **Não aditiva**: não podem
* **Modelos**:
	* **Estrela**:
		* fato ligada às dimensões
		* V: { simplicidade, desempenho }
		* DV: { redundância de dados (nas dimensões), complexidade das atualizações, + espaço de armazenamento }
	* **Snowflake**:
		* dimensões são normalizadas
		* V: { normalização, flexibilidade (+ facilidade de mudar), otimização de espaço em disco }
		* DV: { complexidade, desempenho }
* **Cubo de dados**:  cada eixo representa uma dimensão, células representam valores + hierarquias + operações
* **SCD**:
	* 0 -> não mantém histórico
	* 1 -> mantém apenas a última versão
	* 2 -> mantém todo o histórico
	* 3 -> mantém até N histórico (CEP_2, CEP_1, CEP_atual)
	* 4 -> mantém todo histórico acumulado em outra tabela