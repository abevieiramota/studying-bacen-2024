* coleção de operações sobre relações que resultam em novas relações (propriedade de fechamento)
* ! grau da relação = nº de atributos; cardinalidade = nº de linhas
* **Operadores**
	* de conjuntos tradicionais
		* **união** -> remove duplicações; comutativa, associativa
			* r1 U r2
			* relação final = tuplas(r1) U tuplas(r2)
			* as duas relações devem ter o mesmo número de colunas e com domínios compatíveis
			* grau = grau(r1) = grau(r2)
			* cardinalidade = cardinalidade(r1) + cardinalidade(r2) - cardinalidade(r1 ∩ r2)
		* **interseção** -> comutativa, associativa
			* r1 ∩ r2
			* relação final = tuplas(r1) ∩ tuplas(r2)
			* as duas relações devem ter o mesmo número de colunas e com domínios compatíveis
			* grau = grau(r1) = grau(r2)
			* cardinalidade = |tuplas(r1) ∩ tuplas(r2)|
		* **diferença** -> não comutativa!
			* r1 - r2
			* relação final = tuplas(r1) - tuplas(r2)
			* as duas relações devem ter o mesmo número de colunas e com domínios compatíveis
			* grau = grau(r1) = grau(r2)
			* cardinalidade = cardinalidade(r1) - cardinalidade(r1 ∩ r2)
		* **produto cartesiano**: 
			* r1 x r2 
			* relação final = esquema(r1) U esquema(r2) -> grau = grau(r1) + grau(r2)
			* tuplas resultantes = toda combinação de linhas
			* cardinalidade = cardinalidade(r1) * cardinalidade(r2)
			* equivale ao FROM do SQL
	* relacionais especiais
		* **seleção** -> unário, retorna apenas as linhas que satisfazem o critério -> decorar que Sigma começa com S, de Selection
			* ![[Pasted image 20240317091310.png]]
			* grau = grau(r1)
			* cardinalidade = |tuplas(r1) | satisfazem condição|
			* ! não confundir com o SELECT do SQL -> selection corresponde ao WHERE
			* os predicados não podem comparar valores de duas tuplas diferentes
			* a ordem de aplicação de selections é irrelevante (comutativa)
			* faz uma partição horizontal
		* **projeção** -> unário -> decorar que PI começa com P, de Projeção
			* ![[Pasted image 20240317091801.png]]
			* extrai colunas
			* !! ==elimina duplicações== -> pode ser que ao remover colunas, surjam duplicações -> remover!
			* cardinalidade <= cardinalidade(r1) -> menor, quando houver duplicações
			* equivalente ao SELECT do SQL
			* não é comutativo!
			* faz uma partição vertical
		* **junção**
			* ! cuidado, não é verdade que null = null -> em join, não dar match caso as chaves sejam/contenham null
			* join (inner join)
				* concatena pares de tuplas de acordo com condição
				* ![[Pasted image 20240317145413.png]]
				* o predicado pode ser omitido se for usar equijoin entre atributos de mesmo nome! diferente do natural join, irá repetir os atributos de mesmo nome
			* equijoin -> se só tiver comparação de igualdade
				* natural join -> join nos atributos em comum e retorna os atributos em comum apenas uma vez
					* ![[Pasted image 20240317145432.png]]
					* é um equijoin!
			* left outer join -> ⟕ #anki decorar símbolos
				* todos da esquerda, associando com a direita (nulo se não achar)
			* right outer join -> ⟖
				* todos da direita, associando com a esquerda (nulo se não achar)
			* full outer join -> ⟗
		* ! **divisão** -> que registros em r1 têm correspondência **com todos** registros em r2
			* ![[Pasted image 20240317112430.png]]
			* os atributos de r1 devem conter os atributos de r2
			* os atributos finais são os atributos de r1 que não existem em r2
			* as tuplas finais são todas em r1 que correspondem a todas as tuplas do r2 considerando todos atributos de r2
			* ![[Pasted image 20240317112845.png]]
			* ![[Pasted image 20240317113304.png]]
		* Outras operações
			* ![[Pasted image 20240317113419.png]]
			* ![[Pasted image 20240317113506.png]]
				* **r**ô -> de **r**enomear
		* 
	* 