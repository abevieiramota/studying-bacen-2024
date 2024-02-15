* V: easy to add rows and data
* DV: might read unnecessary data


* Normalização

**Modelagem**
* **Conceitual**: semântica dos dados, independente de estruturas de dados
	* **Notações**: { diagrama E-R, diagrama de classes UML } 
		* **Entidade**: conjunto de objetos da realidade modelada, sobre os quais deseja-se manter informações na base de dados
			* **Fraca**: identificador é composto não apenas por seus atributos (discriminador ou chave parcial), mas também pelo relacionamento com outra entidade; tem que necessariamente estar associada a outra entidade que compõe sua chave (! ver prints de representações)
			* **Forte**: as que não forem fracas
		* **Atributos**: propriedades usadas para descrever uma entidade; **domínio** = conjunto de valores possíveis
			* **Simples/Compostos**: de acordo com as quantidades de partes
			* **Multivalorado**: pode ter mais de um valor por entidade (ex: telefones)
			* **Derivado**: valor pode ser derivado de outro valor (ex: idade -> data de nascimento)
			* **Identificador**: um (simples) ou mais (composto) atributos que identificam instâncias da entidade (cada entidade tem apenas um! pode ter composto, mas será só um)
			* **Cardinalidade**: quantos valores de um atributo a entidade tem, ou relacionamentos com outra entidade 
				* (1, 1) - obrigatório ! quando não está explícita, a cardinalidade = (1, 1), obrigatório
				* (0, 1) - opcional
				* (0, n) - opcional e multivalorado
				* (1, n) - obrigatório e multivalorado
		* **Relacionamento**: associação entre duas ou mais entidades
			* **Grau do relacionamento**: número de unidades participantes
				* **Unário**: autorrelacionamento (em relacionamento unário, o papel é obrigatório!)
				* **Binário**, **Ternário** (papel opcional)
				* Duas entidades podem ter mais de um relacionamento (papeis diferentes)
			* **Cardinalidade** - quando só tem um número, trata-se da cardinalidade máxima:
				* **Cardinalidade máxima**: quantas instâncias no máximo uma pode se relacionar com a outra
				* [ funcionário ] - n - < trabalhar > - 1 - [ departamento ] (um funcionário para no máximo um departamento, um departamento para no máximo n funcionários)
				* [ funcionário ] - (1, n) - < trabalhar > - (1, 1) - [ departamento ] (um funcionário para no um e apenas um departamento, um departamento para um ou mais funcionários)
				* 1:1, 1:n, n:m
* **Lógica**: estruturas de dados que representarão os dados, relacional (tabelas), independente de SGBD
* **Física**: como os dados serão armazenados no banco de dados, dependente do SGBD



**Atributos simples**:
![[Pasted image 20240215190611.png]] 

**Atributos compostos**:
![[Pasted image 20240215190703.png]]

**Atributos multivalorados**:
![[Pasted image 20240215190804.png]]

**Atributo derivado**:
![[Pasted image 20240215190853.png]]

**Identificador simples**:
![[Pasted image 20240215191019.png]]

**Identificador composto**:
![[Pasted image 20240215191102.png]]

**Relacionamento unário**:
![[Pasted image 20240215194229.png]]

!! como analisar a cardinalidade em relacionamento ternário (olhar sempre um par de entidades relacionadas com a outra)
![[Pasted image 20240215194823.png]]

**Entidade** "Dependente" é a **fraca** (traço espesso)
![[Pasted image 20240215200055.png]]
**Outras representações** (a identificação como retângulo/losanglo duplo é a mais frequente):
![[Pasted image 20240215200422.png]]


**Restrição de participação total** (espera-se que toda instância participe do relacionamento):
![[Pasted image 20240215200329.png]]