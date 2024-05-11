* def::**DW**: repositório centralizado, integrado, ==não volátil== (o normal é só inserir, sem fazer delete/update), variável no tempo, ==orientado por assunto==s, projetado para análise
* def::**BI**: conjunto { processos, tecnologias, ferramentas } que auxiliam organizações, a partir de seus dados, a { obter insights, tomar decisões data-driven }
* def::**Data Mart**: segmentação do DW por áreas de negócio
	* abordagens top-down (deriva do DW) x bottom-up (o DW deriva de data marts integrados)
* def::**Granularidade**::atributo de um dado que informa quão detalhado ele é. Quanto menor a granularidade, menor o grão e, portanto, maior o nível de detalhe
* **Componentes de BI**:
	* Fontes de dados
	* ETL
	* DW/Data marts
	* [[Modelagem multidimensional]]
	* Ferramentas de análise e relatórios
	* Consultas e análises
	* Visualização de dados
	* Distribuição e compartilhamento
	* Segurança e acesso
	* Governança de dados
* def::**OLAP** (Online Analytical Processing): abordagem e tecnologia usados para análise interativa (sob múltiplas perspectivas) de dados multidimensionais, para suporte a decisões
	* ![[Pasted image 20240325081404.png]]
	* ![[Pasted image 20240325081527.png]]
	* características chaves { modelagem multidimensional, operações analíticas, desempenho otimizado para consultas analíticas, acesso hierárquico, navegação, visualização }
	* def::**OLAP engine**: oferece recursos para calcular medidas em múltiplas dimensões e usar operações OLAP
		* def::**MOLAP** (Multidimensional OLAP): armazena em cubos ou com computação sob demanda
		* def::**ROLAP** (Relational OLAP): armazena dados em tabelas
		* def:: **HOLAP**: MOLAP + ROLAP
	* **Operações OLAP**:
		* **roll-up / drill-up**: subir na hierarquia
		* **roll-down / drill-down**: descer na hierarquia (detalhar)
		* **slice -> fatia do cubo**: seleciona um ou mais valores de uma dimensão
		* **dice -> subcubo**: filtra em todas dimensões
		* **pivot / rotation**: altera a organização das dimensões
		* **drill across**: quando o usuário pula um nível intermediário dentro da mesma dimensão (parece que é a definição que é cobrada); junção de dois cubos, envolvendo mais uma tabela fato, envolvendo uma dimensão comum (conforme)
		* **drill through**: movimento entre dimensões (definição que é cobrada); desce em dados mais detalhados que a própria fato, como ir na base OLTP de origem
* **ETL x ELT**:
	* ELT é mais recente, menos profissionais habilitados
	* foco em grandes bases de dados
	* mais adaptado a data lake
* **Ciclo de vida de Kimball**
	* **p**lanejamento do projeto
	* definição dos **r**equisitos de negócio
	* **m**odelagem dimensional
	* **p**rojeto e **d**esenvolvimento do DW