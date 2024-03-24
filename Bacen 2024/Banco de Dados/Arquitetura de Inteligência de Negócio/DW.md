* [[Modelagem multidimensional]]

* BI - conjunto { processos, tecnologias, ferramentas } que auxiliam organizações, a partir de seus dados, a { obter insights, tomar decisões data-driven }
	* coletar > organizar > analisar > visualizar
* Data mart - segmentação do DW por áreas de negócio
	* abordagens top-down (deriva do DW) x bottom-up (o DW deriva de data marts integrados)
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
	* abordagem e tecnologia usados para análise interativa de dados multidimensionais
	* projetado para respostas rápidas em consultas analíticas complexas
	* características chaves { modelagem multidimensional, operações analíticas, desempenho otimizado, acesso hierárquico, navegação, visualização }
	* MOLAP (Multidimensional OLAP) - armazena em cubos ou com computação sob demanda
	* ROLAP (Relational OLAP) - armazena dados em tabelas
	* HOLAP - MOLAP + ROLAP
		* particionamento vertical -> agregações em MOLAP, detalhado em ROLAP
		* particionamento horizontal -> dados novos em MOLAP, detalhado em ROLAP
* ETL x ELT
	* ELT é mais recente, menos profissionais habilitados
	* foco em grandes bases de dados
	* mais adaptado a datalake
* 