* **Nº de divisores de um número** = fatora o número e multiplica os expoentes somados com 1. Ex: 20 = 2^2 \* 5 ^\1 -> (2 + 1) \* (1 + 1) = 6 divisores (1, 2, 4, 5, 10, 20)
* **Permutação**:
	* Simples sem repetição: N!
	* Com repetição: N!/k!p!... (divide pelo fatorial da quantidade de repetições por grupo)
	* Permutação circular: (N - 1)!
	* Permutação circular com 2 grupos de mesmo tamanho intercalado: (A - 1)! \* A!
	* Permutação com elementos ordenados: N!/k! k = quantidade de elementos que devem ser mantidos em ordem
	* Desarranjo (permutação em que nenhum elemento ocupa a posição inicial): $N! * (\frac{1}{0!} - \frac{1}{1!} + \frac{1}{2!} - \frac{1}{3!} ... +\frac{-1^N}{N!})$
* **Arranjo**: ordem relevante:
	* Arranjo simples, sem reposição: $\frac{n!}{(n - k)!}$
	* Arranjo simples, com reposição: $n^k$
* **Combinação**: ordem não relevante:
	* Combinação simples, sem reposição: C(n, k) = $\frac{n!}{(n - k)! k!}$
		* C(n, k) = C(n, n - k)
		* $C(n, 0) + C(n, 1) + ... + C(n, n-1) + C(n, n) = 2^n$
	* Combinação completa de p objetos e n marcas: $\frac{(n - 1 + p)!}{(n - 1)! p!}$ = C(n - 1 + p, p)
		* !entender como o problema de permutar os p objetos e os separadores das marcas (n - 1), com repetição dos objetos e dos separadores de marcas
		* pensando como combinação simples, é como se houvesse (n - 1 + p) slots para colocar um objeto ou marca, sendo preciso selecionar os slots das (n - 1) marcas
		* !cuidado com o que é parte e o que é objeto
		* quantidade de soluções inteiras de equações se resolve com esse tipo de combinação
			* ex: x1 + x2 + x3 + x4 + x5 = 6 -> C(5 - 1 + 6, 6)
		* anki::praticar!
* **Partição**: divisão de um conjunto de elementos de forma que cada elemento pertença a uma parte
	* **Partição ordenada**: as partes são consideradas distintas
		* ex: dividir 10 trabalhadores em um grupo com 1 gerente, 2 supervisores e 7 peões
		* n elementos com m grupos = $\frac{n!}{p_1 !p_2 ! ... p_m !}$
	* **Partição não-ordenada**: as partes são consideradas equivalentes entre si
		* ex: dividir 10 profissionais em 5 duplas
		* n elementos com m grupos = $\frac{n!}{p_1 !p_2 ! ... p_m !} \frac{1}{m!}$
			* é a partição ordenada, dividindo pelo número de permutações dos grupos
* **Lemas de Kaplansky**: trata do problema de selecionar elementos que estão ordenados de forma que não sejam selecionados elementos consecutivos
	* **Primeiro lema**: os elementos extremos não são considerados consecutivos
		* para n elementos e p seleções, considerar que haverá n - p elementos não selecionados e que é entre eles que os elementos selecionados estarão
		* há (n - p + 1) espaços entre os (n - p) elementos, de forma que o problema passa a ser C(n - p + 1, p)
	* **Segundo lema**: os elementos extremos são considerados consecutivos (como num círculo)
		* para n elementos e p seleções $\frac{n}{n-p} C(n - p, p)$
		* um caminho sem fórmula envolve quebrar o problema em duas partes
			* o elemento 1 foi selecionado -> os seus vizinhos não poderão ser selecionados, sobrando um problema de selecionar p - 1 elementos não consecutivos numa lista de n - 3 elementos, pelo primeiro lema = C(n - 3 - (p - 1) + 1, p - 1)
			* o elemento 1 não foi selecionado -> os seus vizinhos poderão ser selecionados, sobrando um problema de selecionar p elementos não consecutivos numa lista de n - 1 elementos, pelo primeiro lema = C(n - 1 - p + 1, p)
* 