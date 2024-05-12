* [[Testes unitários]]
* [[Testes de Integração]]
* [[TDD]]
* [[BDD]]

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
		* **Funcional** (caixa **preta**, comportamental, orientado a dados, entrada/saída): focado nas entradas e saídas especificadas nos requisitos funcionais
			* baseado em prés/pós condições
			* busca erros, dentre outros { funções incorretas/inexistentes, comportamento/desempenho, inicialização e término, erros de interface }
			* principais testes
				* baseado em grafos - identifica os objetos/entidades usadas na aplicação, gerar grafo representando o relacionamento entre eles e projetar testes de forma a percorrer o grafo
				* matriz ortogonal - abordagem estatística para testar interações entre inputs ?_?
				* análise de valores limítrofes - assume-se que a maioria dos erros ocorrem nos limites dos dados de entrada -> testa com valores { iguais aos limites, imediatamente inferior ao limite inferior, imediatamente superior ao limite superior}
				* particionamento de equivalências - divide as entradas do programa em classes de equivalência, com representantes, testando com representantes
					* faixa de valores válidas -> 3 testes, 1 para a faixa válida, 1 para valor inferior, 1 para valor superior
					* boolean -> 1 teste para True, 1 para False
					* etc
		* **Estrutural** (caixa **branca**/de **vidro**, orientado à lógica): focado nas estruturas internas dos procedimentos do sistema
			* objetiva cobrir todos os caminhos lógicos
			* principais testes
				* testes de caminhos
				* testes de estruturas de controle
			* complexidade ciclomática > complexidade de caminhos que podem ser percorridos no módulo -> informa um limite superior de testes que deveriam ser feitos (para calcular a quantiade de testes, dado um grafo de complexidade, fazer A - V + 2)
		* **Mista** (caixa **cinza**): usa conhecimento sobre a estrutura para orientar os testes
* Estágios/estratégias de testes
	* unit testing (código) > integrating test (design) > validation test (requirements) > system testing (system engineering)
	* unit testing - teste de componentes individuais (métodos, classes, componentes com estrutura bem conhecida) são testados de forma isolada, com ferramentas automatizadas; também chamado de teste de componente/módulo
	* teste de integração - integra componentes de sistema para buscar problemas nas suas integrações; top-down, cria o esqueleto do sistema e preenche com componentes; bottom-up, cria componentes e vai integrando; para facilitar a localização de erros, ideal integrar e testar gradualmente (testar já integrando tudo=integração big-bang, não é recomendado);
	* teste de aceitação (validação) - busca demonstrar conformidade com os requisitos, testando o que é visível ao usuário; ambiente o mais próximo do real, para simular bem o ambiente usado pelo usuário;
		* alfa - testes conduzidos pelo cliente nas instalações do desenvolvedor, que anota os erros/problemas; ocorre em ambiente controlado! normalmente executado antes do beta
		* beta - conduzido no local do cliente, pelo usuário final, sem presença do desenvolvedor; ocorre em ambiente real; o cliente que anota os problemas;
	* teste de sistema - software é só um dos elementos de um sistema maior - esse teste envolve software, hardware, processos, outros sistemas etc (não confundir com teste de integração, que testa a integração entre módulos do mesmo sistema)
* Tipos
	* teste de regressão - visa executar um subconjunto de testes para verificar se as mudanças não causaram efeitos indesejados; manual ou automatizado
	* teste de fumaça - abordagem de teste de integração, executado logo após o build para checar funcionalidade básica, para saber se o básico está funcionando e daí dá para seguir com testes mais detalhados; busca encontrar erros que tem grande probabilidade de atrasar o projeto (erro no build, não consegue fazer mais nada)
	* teste de recuperação - força o sistema a falhar de diversas formas e checa se ele se recupera de forma adequada; a recuperação pode ser automática ou manual
	* teste de segurança - verifica mecanismos de proteção contra ataques
	* teste de carga (estresse, de esforço) - testa em situações anormais, em relação a, ex, memória, I/O, disco etc
	* teste de desempenho - visa a garantir que o sistema atende aos níveis de desempenho e tempo de resposta definido nos requisitos não-funcionais
	* teste de usabilidade - avalia o sistema do ponto de vista do usuário
	* teste de comparação - back-to-back, compara versões diferentes do mesmo software
* debugging/depuração
	* resulta em remoção de erro, envolve formular hipótese sobre a causa do erro
	* abordagens
		* força bruta: joga dados no console e sai testando ad-hoc; método menos eficiente
		* backtracking: começa onde o erro ocorreu e vai rastreando a fonte de erro
		* eliminação de causa: uma hipótese da causa é elaborada e são coletados dados para avaliá-la; mais recomendada pelo Pressman
* Plano de teste { casos de teste, ferramentas, etc }
	* caso de teste { entradas, pré/pós condições de execução, resultados esperados }
	* caso de teste a partir de caso de uso - um cenário para cada caminho possível, identificando as condições para percorrer os caminhos
* objetos que auxiliam testes
	* mock -> simula comportamento real, permitindo monitorar detalhes como parâmetros recebidos, quantidade de calls etc
	* stub -> mesmo objetivo de mock, mas mais simples, com comportamento previsível/constante

Ferramentas
* [JMeter](https://jmeter.apache.org/) : ver página inicial