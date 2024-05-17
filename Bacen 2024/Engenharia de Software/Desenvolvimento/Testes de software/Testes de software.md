* def::**Teste de software**: processo de executar um programa com o objetivo de encontrar erros > bom teste = alta probabilidade de encontrar erro não conhecido; testes não garantem ausência de problema!
* **Conceitos**:
	* Verificação x Validação:
		* def::**Verificação**: implementa corretamente os requisitos; testes, inspeções
		* def::**Validação**: implementa o que o cliente deseja; homologação, teste de aceitação, revisões
	* Garantia x Controle de qualidade:
		* def::**Garantia de qualidade**: foco no processo, orientado a prevenção
		* def::**Controle de qualidade**: foco no produto, orientado a detecção
* **Princípios**:
	* rastreável a requisitos do cliente
	* planejado
	* princípio de Pareto (80% dos erros está em 20% dos componentes)
	* começar com testes pequenos
	* preferencialmente executado por terceiro/parte independente
* **Abordagens**:
	* def::**Teste Funcional** (caixa **preta**, comportamental, ==orientado a dado==s, entrada/saída): focado nas entradas e saídas especificadas nos requisitos funcionais
		* baseado em prés/pós condições
		* busca erros, dentre outros, de { funções incorretas/inexistentes, comportamento/desempenho, inicialização e término, erros de interface }
		* **Principais testes**:
			* study_more::Estratégias de definição de testes funcionais (ex: matriz ortogonal, particionamento de equivalências etc)
			* **Baseado em grafos**: identifica os objetos/entidades usadas na aplicação, gerar grafo representando o relacionamento entre eles e projetar testes de forma a percorrer o grafo
			* **Matriz ortogonal**: abordagem estatística para testar interações entre inputs ?_?
			* **Análise de valores limítrofes**: assume-se que a maioria dos erros ocorrem nos limites dos dados de entrada -> testa com valores { iguais aos limites, imediatamente inferior ao limite inferior, imediatamente superior ao limite superior}
			* **Particionamento de equivalências**: divide as entradas do programa em classes de equivalência, com representantes, testando com representantes
				* faixa de valores válidas -> 3 testes, 1 para a faixa válida, 1 para valor inferior, 1 para valor superior
				* boolean -> 1 teste para True, 1 para False
				* etc
	* def::**Teste Estrutural** (caixa **branca**/de **vidro**, orientado à lógica): focado nas estruturas internas dos procedimentos do sistema
		* objetiva cobrir todos os caminhos lógicos
		* **Principais testes**:
			* study_more::Estratégias de definição de testes estruturais
			* **Testes de caminhos**:
			* **Testes de estruturas de controle**:
		* def::**Complexidade ciclomática**: complexidade de caminhos que podem ser percorridos no módulo -> informa um limite superior de testes que deveriam ser feitos (para calcular a quantidade de testes, dado um *grafo de complexidade*, fazer A - V + 2)
			* study_more::Cálculo de complexidade ciclomática
	* def::**Teste com abordagem Mista** (caixa **cinza**): usa conhecimento sobre a estrutura para orientar os testes
* **Estágios/estratégias de testes**:
	* Unit testing (código) --> Integrating test (design) --> Validation test (requirements) --> System testing (system engineering)
	* def::**Unit testing** (teste de componente/módulo): teste de componentes individuais (métodos, classes, componentes com estrutura bem conhecida) são testados de forma isolada, com ferramentas automatizadas
		* def::Princípio de teste unitário **FIRST**: { **F**ast, **I**solated/Independent, **R**epeatable, **S**elf-validating, **T**horough }
	* def::**Integration testing**: integra componentes de sistema para buscar problemas nas suas integrações; 
		* top-down: cria o esqueleto do sistema e preenche com componentes; 
		* bottom-up: cria componentes e vai integrando; 
		* para facilitar a localização de erros, ideal integrar e testar gradualmente (integração big-bang, não é recomendado);
			* def::**Integração big-bang**: integrar diversos componentes simultaneamente e depois testar
	* def::**Acceptance testing**: busca demonstrar conformidade com os requisitos, testando o que é visível ao usuário, em ambiente o mais próximo do real, para simular bem o ambiente usado pelo usuário, e para ele verificar se o sistema pode ser implantado em produção
	* Testes alfa x beta:
		* def::**Teste alfa**: testes conduzidos pelo cliente nas instalações do desenvolvedor, que anota os erros/problemas; ocorre em ambiente controlado! normalmente executado antes do beta
		* def::**Teste beta**: conduzido no local do cliente, pelo usuário final, sem presença do desenvolvedor; ocorre em ambiente real; o cliente que anota os problemas;
	* def::**System testing**: software é só um dos elementos de um sistema maior - esse teste envolve software, hardware, processos, outros sistemas etc (não confundir com teste de integração, que testa a integração entre módulos do mesmo sistema)
* **Tipos**:
	* def::**Teste de regressão**: visa executar um subconjunto de testes para verificar se as mudanças não causaram efeitos indesejados; manual ou automatizado
	* def::**Teste de fumaça**: abordagem de teste de integração, executado logo após o build para checar funcionalidade básica, para saber se o básico está funcionando e daí dá para seguir com testes mais detalhados; busca encontrar erros que tem grande probabilidade de atrasar o projeto (erro no build, não consegue fazer mais nada)
	* def::**Teste de recuperação**: força o sistema a falhar de diversas formas e checa se ele se recupera de forma adequada; a recuperação pode ser automática ou manual
	* def::**Teste de segurança**: verifica mecanismos de proteção contra ataques
	* def::**Teste de carga** (estresse, de esforço): testa ==em situações anormais==, em relação a, ex, memória, I/O, disco etc
	* def::**Teste de desempenho**: visa a garantir que o sistema atende aos níveis de desempenho e tempo de resposta definido nos requisitos não-funcionais
	* def::**Teste de usabilidade**: avalia o sistema do ponto de vista do usuário
	* def::**Teste de comparação**: back-to-back, compara versões diferentes do mesmo software
* def::**Debugging/depuração**: formular hipóteses sobre a causa de um erro e explorar código/execução para verificá-la, posteriormente corrigindo o problema
	* **Abordagens**:
		* **força bruta**: joga dados no console e sai testando ad-hoc; método menos eficiente
		* **backtracking**: começa onde o erro ocorreu e vai rastreando a fonte de erro
		* **eliminação de causa**: uma hipótese da causa é elaborada e são coletados dados para avaliá-la; mais recomendada pelo Pressman
* **Inspeção de software/revisões formais**: (análise estática)
	* não checa requisitos não funcionais como desempenho, usabilidade etc
	* não checa com a necessidade final do usuário, apenas em relação a requisitos
	* **V**: { pode ser feito antes de ter executável, pode ser aplicada a qualquer artefato, efetivo para encontrar erros }
	* **DV**: { maior custo, necessidade de requistos de qualidade, de padrões }
	* !detecção de defeitos, a correção/definição de solução ocorre **depois** da inspeção
	* inspeção automatizada ex: { loops infinitos, variáveis não inicializadas, não utilizadas, interface correta etc }
	* def::**Walkthrough**: inspeção rápida, informal
* **Plano de teste** { casos de teste, ferramentas, etc }:
	* def::**Caso de teste**: define, para um teste, { entradas, pré/pós condições de execução, resultados esperados }
	* caso de teste a partir de caso de uso - um cenário para cada caminho possível, identificando as condições para percorrer os caminhos
* **Objetos que auxiliam testes**:
	* def::**Mock**: simula comportamento real de um código, permitindo monitorar detalhes como parâmetros recebidos, quantidade de calls etc
	* def::**Stub**: mesmo objetivo de Mock, mas mais simples, com comportamento previsível/constante
	* next_step:: estudar outros simuladores de testes (mocks, stubs, fakes, dummies, spies)
* **Metodologias**:
	* [[TDD]]
	* [[BDD]]
* **Ferramentas**:
	* tool::[JMeter](https://jmeter.apache.org/) 
	* tool::**JUnit**: framework [[Java]] que facilita o desenvolvimento e automação de testes unitários
		* baseada em anotações, se o método é de teste, se deve ser executado antes/depois
		* **JUnit 5** = { JUnit Platform (core do JUnit 5), JUnit Jupiter (testes baseados em Jupiter), JUnit Vintage (testes usando JUnit 3 e 4 - retrocompatibilidade) }
		* incluir o junit.jar no classpath - também vem já configurado em IDEs como Eclipse, NetBeans etc
		* **Classes/interfaces**:
			* **org.junit.jupiter.api**:
				* @Test (não tem atributos!)
				* @Disabled
				* @Timeout (falha o teste se exceder tempo; unidade padrão = s, pode alterar com o atributo unit = TimeUnit.MILLISECONDS, ex)
				* @BeforeEach (executado antes de cada um dos métodos - setup)
				* @AfterEach (executado após cada um dos métodos)
				* @BeforeAll (executado antes de todos métodos)
				* @AfterAll (executado depois de todos)
				* @ParameterizedTest (o método tem argumentos e define-se um @ValueSource)
				* @RepeatedTest (modelo de teste para testes repetidos N vezes)
				* @TestFactory (fábrica de testes para testes dinâmicos)
				* @TestTemplate (template para testes)
				* @TestMethodOrder (configura a ordem de execução dos métodos - se não tiver, o JUnit quem define a ordem; anotação de classe, daí anota os métodos com @Order(n))
				* @TestInstance (configura o ciclo de vida da classe de teste)
				* @DisplayName (define o nome de exibição para a classe/método)
				* @DisplayNameGeneration (gerador de nome)
				* @Nested (classe anotada é classe aninhado)
				* @Tag (usado em filtragens de testes; não pode ser nula/branca, não pode conter espaços em branco; sem palavras reservados)
			* **org.junit.jupiter.api.Assertions** (métodos estáticos):
				* compara resultado com esperado e pode receber mensagem caso falso
				* assertTrue(boolean), assertTrue(boolean, msg), assertTrue(boolean, messageSuplier), assertFalse...
				* assertSame, assertNotSame (verifica se é o mesmo objeto)
				* assertEquals(expected, actual), assertEquals(expected, actual, tolerance/delta)
				* assertNull, assertNotNull
			* **org.junit.jupiter.api.Assumptions**:
				* assumeTrue
			* **org.junit.jupiter.api.condition** (condições sobre { SO, JRE, propriedades do sistema, baseadas em script }):
				* @EnabledOnOS, @DisabledOnOs (ex: @EnabledOnOS(MAC)) (org.junit.jupiter.api.condition.OS.MAC)
				* @EnabledIfSytstemProperty(named = "os.arch", matches = ".\*64.\*")
				* @EnabledIf("2 * 3 == 6")
		* tool::**Libs de asserções**: { Hamcrest, AsssertJ, Truth }
		* todo::classe não podem ser abstratas e devem ter apenas um construtor (?verificar?)
		* todo::método não podem ser privados e com retorno void (?verificar?)