
* def::**Conceitual**: semântica dos dados, independente de estruturas de dados
	* **Notações**: { Modelo Entidade-Relacionamento, diagrama de classes UML } -> informações sobre MER abaixo
	* def::**Entidade**: conjunto de objetos da realidade modelada, sobre os quais deseja-se manter informações na base de dados
		* **Fraca**: identificador é composto não apenas por seus atributos (discriminador ou chave parcial), mas também pelo relacionamento com outra entidade; tem que necessariamente estar associada a outra entidade que compõe sua chave
		* **Forte**: as que não forem fracas
		* **Atributos**: propriedades usadas para descrever uma entidade ou relacionamento; 
			* **Domínio**: conjunto de valores que o atributo pode assumir
			* **Simples/Compostos**: de acordo com as quantidades de partes (exemplo de composto: endereço)
			* **Multivalorado**: pode ter mais de um valor por entidade (ex: telefones)
			* **Derivado**: valor pode ser derivado de outro valor (ex: data de nascimento -> idade)
			* **Identificador**: um (simples) ou mais (composto) atributos que identificam instâncias da entidade (cada entidade tem apenas um! pode ter composto, mas será só um)
				* anki::cuidado, pois no MER, fala-se em identificador, não em chave, que é conceito da modelagem relacional
			* **Cardinalidade**: quantos valores de um atributo a entidade tem ou relacionamentos com outra entidade 
				* (1, 1) - obrigatório ! quando não está explícita, a cardinalidade = (1, 1), obrigatório
				* (0, 1) - opcional
				* (0, n) - opcional e multivalorado
				* (1, n) - obrigatório e multivalorado
	* def::**Relacionamento**: associação entre duas ou mais entidades; !também pode ter atributos
		* def::**Grau do relacionamento**: número de unidades participantes
			* **Unário**: autorrelacionamento (!em relacionamento unário, o papel é obrigatório)
			* **Binário**, **Ternário** (papel opcional)
			* Duas entidades podem ter mais de um relacionamento (papéis diferentes)
		* **Cardinalidade**: (quando só tem um número, trata-se da cardinalidade máxima, (0, x))
			* **Cardinalidade máxima**: quantas instâncias no máximo uma pode se relacionar com a outra
			* \[funcionário\] - n - \<trabalhar\> - 1 - \[departamento\] (um funcionário para no máximo um departamento, um departamento para no máximo n funcionários)
			* \[funcionário\] - (1, n) - \<trabalhar\> - (1, 1) - \[departamento\] (um funcionário para um e apenas um departamento, um departamento para um ou mais funcionários)
			* anki::em relacionamento n x m, se não houver identificador, um registro em A só pode ser associado a um registro em B uma vez (o exemplo da consulta, é preciso haver algo como o momento da consulta, além da chave do paciente e do médico)
	* **Especialização/Generalização**: subentidade herda atributos e relacionamentos e pode adicionar novos
		* ![[Pasted image 20240220174736.png]]
		* **Restrições**:
			* **total**: toda entidade é instância de alguma das especializações; é representado com um T ao lado do triângulo
			* **parcial**: não total; é representado com um P ao lado do triângulo
			* **disjunção**: cada entidade só pode pertencer a uma subclasse; representado com um D ao lado do triângulo
			* **sobreposição**: não disjunção; representado com um S ao lado do triângulo
	* **Entidade associativa/agregação**: modela relacionamentos que possuem relacionamentos
		* lembrar do modelo (Médico, consulta, Paciente) e os medicamentos prescritos -> relacionamento com a consulta
		* ![[Pasted image 20240220180632.png]]
	* **Agregação**: representa o agrupamento de objetos (entidade/relacionamentos)
		* ![[Pasted image 20240220180744.png]]
* def::**Lógica**: ou de implementação; estruturas de dados que representarão os dados, relacional (tabelas), independente de SGBD; modelo Relacional
	* **Formas normais**:
		* **1NF** - só contém atributos atômicos -> não tem atributos multivalorados, atributos compostos, tabelas aninhadas
		* **2NF** - 1NF e não tem dependências parciais (atributo não chave depende de parte de chave composta - considerar qualquer chave, não apenas a PK)
			* !pode ser definido também como '1NF + todos atributos não chave dependem totalmente da chave primária'
		* **3NF** - 2NF e não tem dependência transitiva (X -> Y, Y -> Z, sendo X chave e Y, Z não chave)
		* **BCNF** - 3NF e para toda dependência funcional X -> A, X é uma superchave (o lado esquerdo de toda dependência funcional é superchave)
		* study_more::**4NF** - BCNF e não contém dependências multivaloradas
		* study_more::**5NF** - 4NF e não pode ter dependência de junção (há perda ao transformar a relação original em duas, é preciso três)
	* **Características**:
		* apesar de as representações produzirem uma ordem entre atributos e entre as tuplas, no modelo relacional não há ordem entre atributos e entre tuplas
		* uma relação não possui duplicações
	* **Notação**:
		* tabela/relação (lembrar que relação vem de relação entre atributos), linha/tupla, coluna/atributo/campo
		* **cardinalidade**: número de tuplas na relação (!para decorar, perceber que cardinalidade é maior que grau, da mesma forma que o volume de tuplas é maior que o volume de atributos)
		* **grau**: número de atributos
	* **Restrições de integridade**:
		* **de domínio**: valores possíveis em um campo
		* **de vazio**: nullable; todas as colunas que compõem a chave primária devem ser not null!
		* **de chave**: 
			* **superchave**: conjunto de atributos de uma relação que permite identificar uma tupla de forma unívoca -> não existem duas tuplas com mesmo valor de superchave (a própria tupla toda é uma superchave!)
			* **chave**: superchave mínima, isto é, que deixa de ser superchave caso algum atributo seja removido
			* **chave primária**: chave selecionada como principal, as demais são chamadas *chaves alternativas*
			* !importante, quando perguntar 'quantas chaves primárias há', considerar que chave composta é apenas uma chave! não contar cada atributo separado
		* **referencial**: atributo ou combinação de atributos que referencia uma chave (primária ou candidata! não precisa ser primária!) de uma relação (pode ser ela mesma - autorrelacionamento); opcional ou obrigatória 
			* quando inclui/altera linha em tabela referenciando outra, checa se a referenciada existe
			* quando exclui uma linha referenciada, garantir que não existe tupla referenciando
		* **de unicidade**: campo ou combinação de campos não se repetem na tabela
		* anki::**de entidade**: define que nenhum valor da chave primária pode ser nulo
	* **Restrições semânticas**: baseadas na semântica da aplicação, desenvolvida por programadores - ex: salário do empregado não pode ser superior ao de seu superior
	* study_more::**Transformação de modelo conceitual em modelo lógico**
		* um modelo MER pode corresponder a diversos modelos relacionais
		* **objetivos da transformação**: { bom desempenho, simplificar desenvolvimento da aplicação e DB }
		* **princípios a serem seguidos**: { evitar junções, diminuir o número de chaves, evitar campos opcionais }
		* cada entidade -> tabela, cada atributo -> coluna, cada atributo identificadores -> chave primária
		* relacionamentos - transformações (a escolha depende da cardinalidade do relacionamento) [exercícios](https://provasdeti.nutror.com/curso/f89b9ced26559/aula/456795)
			* { tabela própria para o relacionamento, adição de colunas a uma tabela, fusão de tabelas }
			* **0.1 : 0.1**: 
				* OK: { adição de colunas, tabela própria (não ideal) }
				* NOK: { fusão de tabelas }
			* **0.1 : 1.1**: 
				* OK: { fusão de tabelas (a chave primária é a do lado obrigatório, não pode ser as duas juntas!), adição de colunas (não ideal; adiciona na tabela do lado opcional, deve ser obrigatório e único) }
				* NOK: { tabela própria }
				* ! cuidado, cada lado pode ser associado a no máximo 1 entidade do outro lado
			* **1.1 : 1.1**:
				* OK: { fusão de tabelas (chave primária é uma das chaves primárias! não pode ser as duas juntas, senão permite 1.n) }
			* **0.1 : 0.n/1.n**: 
				* OK: { adição de colunas (fk na entidade N para a 1, não obrigatória ), tabela própria (não ideal; chave primária é a do lado N) }
			* **1.1 : 0.n/1.n**:
				* OK: { adição de colunas (fk da entidade N para a 1, obrigatória; atributos do relacionamento vão também) } !apenas adição de colunas
			* **n:m**: 
				* OK: { tabela própria (chave da tabela é a composição das chaves primárias) } !apenas tabela própria
				* !se deve permitir que uma entidade participe n vezes do relacionamento, é preciso ter um atributo a mais compondo a chave
		* **entidade fraca**: a tabela dela tem como chave primária uma composição de uma chave da entidade forte e um identificador da entidade fraca
		* **relacionamento ternário**: o relacionamento é transformado em uma entidade e cada relacionamento vira um relacionamento binário
		* study_more::[hierarquia](https://provasdeti.nutror.com/curso/f89b9ced26559/aula/456796)
			* **tabelão**: chave primária da pai; união dos atributos da genérica e especializadas; adição de coluna Tipo, identificando qual o tipo/especialização (considerando que só pode assumir um tipo; ou coluna booleana para cada tipo)
			* **uma tabela por especialização**: replica os atributos da geral em cada especializada
			* **tabela para a geral e tabela para cada especialização**: especializada tem chave para a estrangeira (usa a mesma PK e ela é FK para a geral!)
* def::**Física**: como os dados serão armazenados no banco de dados, dependente do SGBD



**MER** ! não confundir com modelo relacional
**Atributos simples**:
![[Pasted image 20240215190611.png]] 

**Atributos compostos**:
![[Pasted image 20240215190703.png]]

**Atributos multivalorados**:
![[Pasted image 20240215190804.png]]

**Atributo derivado**:
![[Pasted image 20240215190853.png]]

**Identificador simples** (!cuidado estritamente falando, não é 'chave primária', conceito que só vem depois na modelagem):
![[Pasted image 20240215191019.png]]

**Identificador composto**:
![[Pasted image 20240215191102.png]]

**Relacionamento unário**:
![[Pasted image 20240215194229.png]]

!! como analisar a cardinalidade em relacionamento ternário (olhar sempre um par de entidades relacionadas com a outra)
![[Pasted image 20240215194823.png]]

**Entidade** "Dependente" é a **fraca** (traço espesso) - a entidade relacionada é a forte e o identificador da dependente é composto pelo dele e o da entidade forte
![[Pasted image 20240215200055.png]]
**Outras representações** (a identificação como retângulo/losanglo duplo é a mais frequente):
![[Pasted image 20240215200422.png]]


**Restrição de participação total** (espera-se que toda instância participe do relacionamento):
![[Pasted image 20240215200329.png]]

![[Pasted image 20240220191243.png]]
![[Pasted image 20240220191454.png]]
Não usa losango para representar relacionamento!
![[Pasted image 20240220191637.png]]

![[Pasted image 20240220191803.png]]
#anki 
![[Pasted image 20240220191933.png]]

**Transformação de modelos**
![[Pasted image 20240302153650.png]]