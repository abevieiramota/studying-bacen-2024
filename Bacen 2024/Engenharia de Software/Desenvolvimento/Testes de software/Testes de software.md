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
		* **Funcional** (caixa preta): focado ans entradas e saídas especificadas nos requisitos funcionais
		* **Estrutural** (caixa branca/de vidro): focado nas estruturas internas dos procedimentos do sistema
		* **Mista** (caixa cinza): usa conhecimento sobre a estrutura para orientar os testes
	* 