* **nº do divisores de um número** = fatora o número e multiplica os expoentes somados com 1. Ex: 20 = 2^2 \* 5 ^\1 -> (2 + 1) \* (1 + 1) = 6 divisores (1, 2, 4, 5, 10, 20)
* **Permutação**:
	* Simples sem repetição: N!
	* Com repetição: N!/k!p!... (divide pelo fatorial da quantidade de repetições por grupo)
	* Permutação circular: (N - 1)!
	* Permutação circular com 2 grupos de mesmo tamanho intercalado: (A - 1)! \* A!
	* Permutação com elementos ordenados: N!/k! k = quantidade de elementos que devem ser mantidos em ordem
	* Desarranjo (permutação em que nenhum elemento ocupa a posição inicial): $N! * (\frac{1}{0!} - \frac{1}{1!} + \frac{1}{2!} - \frac{1}{3!} ... +\frac{-1^N}{N!})$
* **Arranjo** - ordem relevante:
	* Arranjo simples, sem reposição: $\frac{n!}{(n - k)!}$
	* Arranjo simples, com reposição: $n^k$
* **Combinação** - ordem não relevante:
	* Combinação simples, sem reposição: C(n, k) = $\frac{n!}{(n - k)! k!}$
		* C(n, k) = C(n, n - k)
		* $C(n, 0) + C(n, 1) + ... + C(n, n-1) + C(n, n) = 2^n$
	* Combinação completa de p objetos e n marcas: $\frac{(n - 1 + p)!}{(n - 1)! p!}$ = C(n - 1 + p, p)
		* entender como o problema de permutar os p objetos e os separadores das marcas (n - 1), com repetição dos objetos e dos separadores de marcas
		* pensando como combinação simples, é como se houvesse (n - 1 + p) slots para colocar um objeto ou marca, sendo preciso selecionar os slots das (n - 1) marcas
		* ! cuidado com o que é parte e o que é objeto
	* 