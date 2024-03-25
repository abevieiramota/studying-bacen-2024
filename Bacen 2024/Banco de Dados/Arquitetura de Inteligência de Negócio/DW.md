* [[Modelagem multidimensional]]

* BI - conjunto { processos, tecnologias, ferramentas } que auxiliam organizações, a partir de seus dados, a { obter insights, tomar decisões data-driven }
	* coletar > organizar > analisar > visualizar
* Data mart - segmentação do DW por áreas de negócio
	* abordagens top-down (deriva do DW) x bottom-up (o DW deriva de data marts integrados)
* granularidade -> quanto maior, maior o nível de detalhe
* Componentes do BI
	* Fontes de dados
	* ETL
	* DW/Data marts
	* Modelagem de dados dimensional
	* Ferramentas de análise e relatórios
	* Consultas e análises
	* Visualização de dados
	* Distribuição e compartilhamento
	* Segurança e acesso
	* Governança de dados
* DW
	* repositório centralizado, integrado, não volátil (o normal é só inserir, sem fazer delete/update), variável no tempo, orientado por assuntos, projetado para análise
* OLAP (Online Analytical Processing)
	* abordagem e tecnologia usados para análise interativa (sob múltiplas perspectivas) de dados multidimensionais, para suporte a decisões
	* ![[Pasted image 20240325081404.png]]
	* projetado para respostas rápidas em consultas analíticas complexas
	* características chaves { modelagem multidimensional, operações analíticas, desempenho otimizado, acesso hierárquico, navegação, visualização }
	* OLAP engine -> oferece recursos para calcular medidas em múltiplas dimensões e usar operações OLAP
	* MOLAP (Multidimensional OLAP) - armazena em cubos ou com computação sob demanda
	* ROLAP (Relational OLAP) - armazena dados em tabelas
	* HOLAP - MOLAP + ROLAP
		* particionamento vertical -> agregações em MOLAP, detalhado em ROLAP
		* particionamento horizontal -> dados novos em MOLAP, detalhado em ROLAP
	* Operações OLAP
		* roll-up / drill-up -> subir na hierarquia
		* roll-down / drill-down -> descer na hierarquia (detalhar)
		* slice -> fatia do cubo -> seleciona um ou mais valores de uma dimensão
		* dice -> subcubo -> filtra em todas dimensões
		* pivot/rotation -> altera a organização das dimensões
		* drill across -> quando o usuário pula um nível intermediário dentro da mesma dimensão (parece que é a definição que é cobrada); junção de dois cubos, envolvendo mais uma tabela fato, envolvendo uma dimensão comum (conforme)
		* drill through -> movimento entre dimensões (definição que é cobrada); desce em dados mais detalhados que a própria fato, como ir na base OLTP de origem
	* ![[Pasted image 20240325081527.png]]
* ETL x ELT
	* ELT é mais recente, menos profissionais habilitados
	* foco em grandes bases de dados
	* mais adaptado a datalake
* SCD
	* 0 -> não mantém histórico
	* 1 -> mantém apenas a última versão
	* 2 -> mantém todo o histórico
	* 3 -> mantém até N histórico (CEP_2, CEP_1, CEP_atual)
	* 4 -> mantém todo histórico acumulado em outra tabela
* Ciclo de vida de Kimball
	* planejamento do projeto
	* definição dos requisitos de negócio
	* modelagem dimensional
	* projeto e desenvolvimento do DW