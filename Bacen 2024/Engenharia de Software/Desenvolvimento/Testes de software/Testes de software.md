* [[Testes unitários]]
* [[Testes de Integração]]
* [[TDD]]
* [[BDD]]

! Pressman é bastante cobrado! #TODO

* Verificação e Validação: descobrir defeitos E avaliar utilidade
	* Verificação - implementa corretamente os requisitos; testes, inspeções
	* Validação - implementa o que o cliente deseja; homologação, teste de aceitação, revisões
* Garantia x Controle de qualidade
	* Garantia -> foco no processo, orientado a prevenção
	* Controle -> foco no produto, orientado a detecção
* Inspeção de software/revisões formais (análise estática)
	* não checa requisitos não funcionais como desempenho, usabilidade etc
	* não checa com a necessidade final do usuário, apenas em relação a requisitos
	* V { pode ser feito antes de ter executável, pode ser aplicada a qualquer artefato, efetivo para encontrar erros }
	* DV { maior custo, necessidade de requistos de qualidade, de padrões }
	* !detecção de defeitos, a correção/definição de solução ocorre **depois** da inspeção
	* inspeção automatizada ex { loops infinitos, variáveis não inicializadas, não utilizadas, interface correta etc }
	* walkthrough -> inspeção rápida, informal
* Tipos
	* processo de executar um programa com o objetivo de encontrar erros > bom teste = alta probabilidade de encontrar erro não conhecido; testes não garantem ausência de problema!
	* princípios { rastreável a requisitos do cliente, planejado, princípio de Pareto (80% dos erros está em 20% dos componentes), começar com testes pequenos, preferencialmente executado por terceiro/parte independente }
	* Abordagens
		* **Funcional** (caixa **preta**): focado ans entradas e saídas especificadas nos requisitos funcionais
			* baseado em prés/pós condições
			* busca erros, dentre outros { funções incorretas/inexistentes, comportamento/desempenho, inicialização e término, erros de interface }
			* principais testes
				* baseado em grafos - identifica os objetos/entidades usadas na aplicação, gerar grafo representando o relacionamento entre eles e projetar testes de forma a percorrer o grafo
				* matriz ortogonal - 
				* análise de valores limítrofes - assume-se que a maioria dos erros ocorrem nos limites dos dados de entrada -> testa com valores em torno dos valores limítrofos
				* particionamento de equivalências - divide as entradas do programa em classes de equivalência, com representantes, testando com representantes
					* faixa de valores válidas -> 3 testes, 1 para a faixa válida, 1 para valor inferior, 1 para valor superior
					* boolean -> 1 teste para True, 1 para False
					* etc
		* **Estrutural** (caixa **branca**/de **vidro**): focado nas estruturas internas dos procedimentos do sistema
			* objetiva cobrir todos os caminhos lógicos
			* principais testes
				* testes de caminhos
				* testes de estruturas de controle
			* complexidade ciclomática > complexidade de caminhos que podem ser percorridos no módulo -> informa um limite superior de testes que deveriam ser feitos
		* **Mista** (caixa **cinza**): usa conhecimento sobre a estrutura para orientar os testes
* Estágios/estratégias de testes
	* unit testing (código) > integrating test (design) > validation test (requirements) > system testing (system engineering)
	* unit testing - teste de componentes individuais (métodos, classes, componentes com estrutura bem conhecida) são testados de forma isolada, com ferramentas automatizadas
	* teste de integração - integra componentes de sistema para buscar problemas nas suas integrações; top-down, cria o esqueleto do sistema e preenche com componentes; bottom-up, cria componentes e vai integrando; para facilitar a localização de erros, ideal integrar e testar gradualmente (testar já integrando tudo=integração big-bang, não é recomendado);
	* 