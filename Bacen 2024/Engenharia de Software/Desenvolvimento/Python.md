* if \_\_name\_\_ == '\_\_main\_\_':
* similar ao Java, é compilado e interpretado (mas em Python o executor já compila e executa); bytecode em .pyc (compila com python -m compileall, joga na \_\_pycache\_\_)
* linguagem dinâmicamente tipada
* False/True (cuidado, literal bool começa com letra maiúscula)*
* nomes de variável inválidas: começar com número, ter -, espaço, #
* operadores 
	* is (mesmo objeto), == (conteúdo igual)
	* len
	* precedência de operadores: parênteses > exponencial > multi/div > resto
	* !! não existe operador de pré/pós incremento! ++x é igual a x, basicamente colocou o sinal positivo na frente duas vezes
	* // -> divisão inteira
* strings
	* "oi" * 3 = "oioioi"
	* concatenação, apenas entre strings
	* string pode ser acessada por índice 0-based
	* 'r' in my_str
	* capitalize(), upper(), lower(), split('/'), strip(), lstrip(), rstrip(), find('ab'), startswith('ini'), replace('a', '+') -> ! retorna uma nova string, title(), isupper(), islower(), count('a')
	* string é objeto imutável -> as funções que processam não alteram inplace, apenas retornam o resultado
		* faz uso de pool de strings (daí x = 'oi'; y = 'oi'; print(x is y) imprime True)
	* multiline """
	* fstring (pode fazer cálculo dentro)
	* ![[Pasted image 20240316132901.png]]
* **if** numero == 10: else: elif: (parênteses não obrigatório)
* range(n) -> gerador de 0 a n - 1; range(0, n, s) -> de 0 a n-1, com step s
* estruturas de dados
	* list
		* list(), \[\]
		* indexável
		* heterogênea (armazena dados de quaisquer tipos), mutável
		* append(), find(), extend(), copy(), index(), insert(), reverse(), sort(), pop() -> último, pop(ix), remove(), sort(reverse=True), count(x)
		* l\[indice_nao_existente\] -> exception
		* l\[x:y\] -> x inclusivo, y não inclusivo; l\[-x\]; l\[1: \] (tudo a partir do índice 1), l\[:4\] até o índice 3; l\[-1\] = último elemento
		* l\[::-1\] -> percurso invertido
		* del l\[3\] -> remove elemento no índice 3
		* 
	* tuplas
		* tuple(), (,)
		* similar a listas, mas são imutáveis
		* count(x), index(x)
	* set
		* set(), \{,\}
		* a = {,} -> para inicializar! {}, sem a vírgula, é map
		* não garante ordem, não mantém repetições
		* add(x), remove(x), union(x), intersection(x), difference(x), isdisjoint(x), issubset(x), issuperset(x), symmetric_difference(x)
	* dictionary - chave-valor
		* dict(a=1, 'oi'=3), {'a': 'b'}
		* x\['a'\]
		* keys(), values(), get(x), get(x, y) -> retorna y, caso não haja x, update(d), pop(x) -> remove item de key = x e retorna seu value, clear() -> remove tudo, x in d -> checa se há chave x
		* for k, v in x.items():
		* del d\[x\]
		* dict_c = {\*\*dict_a, \*\*dict_b} -> merge de dictionários
* funções
	* def
	* pode retornar mais de um elemento -> x, y = f(a)
	* print(), abs(), min(), max(), sorted(), sum(), len()
* try/except/finally
* OO
	* class Casa: def \_\_init\_\_(self, x, y): self.x = x self.y = y
	* empty class -> class Oi: pass
	* construtor e instance methods devem sempre receber self como primeiro argumento
	* class attributes -> class Oi: x = 1 (sempre deve ser inicializado)
	* def \_\_str\_\_(self): -> método toString
	* inheritance -> class X(Y): 
		* super().\_\_init\_\_()
		* isinstance(x, Class) -> checa se x é instância de Class
* walrus operator -> print(x:=10) -> atribui o valor e retorna
* print(x), print(x, y) -> concatena com espaço, print(x, end='uashd') -> troca o newline por outro valor, após cada print; print(x, y, sep=';') -> troca o separador padrão
* input() para input, pode receber uma mensagem para apresentar
* callable(x) -> True, se for callable
* enumerate(l)
* hasattr(o, 'att') -> True se objeto o tem atributo att
* reversed(l) -> retorna um reversed iterator
* zip(x, y, z)
* 'kid' if age < 13 else 'teen' if age < 18 else 'adult'
* não tem switch! é match x: case 10: etc
	* match com mais de uma opção -> | ou 'or'
	* match de iterables por tamanho -> match l: case \[a\]: print(a) case \[a, b]: print(a, b)
	* default value -> case \_
* while
* modificar global variable dentro de uma função -> usa 'global variavel'
* lambda x, y: x + y
* 


#TODO most used methods string, os, sys, list, set, map, tuple etc
#TODO cpython, PEP, 