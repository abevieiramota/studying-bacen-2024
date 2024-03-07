[ProvasDeTI](https://app.nutror.com/curso/6f2348a226567/aula/457072)

* **Escalonamento/scheduling de transações**: a ordem em que as operações das transações são executadas 
	* serial: cada transação executa todas suas operações antes de começar a próxima
	* concorrente/intercalado: alterna operações das transações
		* concorrente serializável -> se o estado final dele é igual a ao de uma execução serial -> se é serializável, é correto
* **Níveis de isolamento**
	* define o grau em que uma transação deve ser isolada contra modificações de recursos ou de dados feitas por outras transações
	* uma das formas de definir os níveis é indicando quais efeitos colaterais de simultaneidade são permitidos
	* quanto menos restritivo o isolamento, melhor a performance, mas piores os efeitos colaterais que podem ocorrer
	* **Efeitos colaterais**
		* **dirty write**, escrita suja, atualização perdida: duas transações simultâneas atualizam o mesmo dado, de forma que uma das atualizações é perdida
			* ![[Pasted image 20240306111756.png]]
		* **dirty read**, leitura suja, dependência sem commit (!o que + cai): leitura de dados não confirmados de uma linha existente, podendo ocasionar a leitura de uma informação que não será confirmada
			* ![[Pasted image 20240306111919.png]]
		* **non repeatable read**, leitura não repetível, análise inconsistente: duas leituras de dados na mesma transação dão resultados **do dado** diferentes (na segunda leitura, dados não existem ou foram modificados)
			* ! a diferença para dirty read é que dirty lê uncommited, enquanto non repeatable read envolve commited
		* **phantom read**, leitura fantasma: duas leituras de dados na mesma transação e dão **quantidade** de resultados diferente
	* **Níveis** (em ordem de restritividade) -> *start transaction serializable; set transaction level serializable*
		* **Read uncommited**
		* **Read commited** (padrão na maioria dos bancos)
		* **Repeatable read**
		* **Serializable**
	* ![[Pasted image 20240306112454.png]]
		* ! o único nível que permite *leitura suja* é o **Read uncommited**
* **Formas de verificar que um escalonamento é serializável**
	* Equivalência por resultado -> produz o mesmo estado final no BD
	* Equivalênica por visão -> cada read lê o resultado de um mesmo write nos dois escalonamentos
		* checar, para cada read, qual foi o último write que escreveu o valor -> deve ser o mesmo nos dois escalonamentos
		* primeir reads e últimos devem ser iguais (?)
		* menos restritiva que equivalência por conflito (se é serializável em conflito -> é serializável em visão, o contrário não é válido)
	* Equivalência por conflito -> a ordem de qualquer duas operações conflitantes é a mesma nos dois escalonamentos
		* conflito -> duas operações, cada uma numa transação diferente, acessam o mesmo dado, pelo menos uma é de escrita
			* ex: [ (r1(x), w2(x)), (w3(x), w4(x)) ...] em conflito ! é preciso identificar a ordem das operações -> (r1(x), w2(x)) significa que há conflito entre essas duas operações e r1(x) veio primeiro
			* ex: [ (r1(x), w2(y)), (r1(y), r3(y)), (r4(w), w4(w)) ] não em conflito -> operações sobre dados diferentes, duas leituras, leitura e escrita da mesma transação
		* dois escalonamentos são equivalentes por conflito se eles tiverem os mesmos conflitos e na mesma ordem
		* Ver aula https://app.nutror.com/curso/6f2348a226567/aula/457076
		* você vê num escalonamento serial quais conflitos há e daí verifica se o escalonamento concorrente/intercalado tem os mesmos conflitos, na mesma ordem
		* Grafo de serialização -> técnica que simplifica a verificação de equivalência por conflito
			* Para cada transação -> criar um nó
			* Para cada conflito envolvendo, em ordem, a transação I e J -> criar aresta do nó de I para o nó de J
			* O plano é serializável se e somente se o grafo resultante não contiver ciclos (as arestas não são anotadas, independe do dado com conflito)

**Técnicas de recuperação** (garantia de durabilidade)
* Tipos de falhas { lógicas (overflow, divisão por zero, exceção não tratada etc), física (incêndio, queima de ar condicionado, perda de buffer, erro de hardware etc)}
* Log append-only que guarda as alterações realizadas no banco -> grave primeiro no log e depois no banco
	* deve estar em armazenamento estável, com backup
	* pode ficar muito grande
	* entradas no log (Ti, Xj, V1, V2) (transação, identificador do dado, valor antigo, valor novo); (Ti, start); (Ti, commit); (Ti, abort); (Ti, read, X)
* Técnicas
	* Atualização adiada/postergada - algoritmo **no-undo/redo** (não desfaz e refaz)
		* a base só é atualizada após o commit
		* no caso de falha, percorre o log e (em questão, é ir olhando o que foi commitado)
			* se não foi escrito no DB -> ignora
			* se foi escrito (encontrou o start e commit da transação) -> executa a operação (redo)
		* como não há undo, o log não registra o valor antigo dos dados que sofreram alterações (Ti, Xj, Vnovo)
	* Atualização imediata - algoritmo **undo/redo** (desfaz e refaz)
		* as modificações já vão sendo feitas no banco -> daí é preciso guardar o valor antigo e novo no log, porque talvez deva ter que desfazer operações
		* no caso de falha, percorre o log e
			* se não foi commitado -> desfaz a transação
			* se foi commitado -> redo
	* * Paginação sombra (shadow pagging) - **no-undo/no-redo** - alternativa ao log
		* mantém duas tabelas de páginas durante o tempo de vida de uma transação { Tabela de Páginas Correntes (TPC), Tabela de Páginas Shadow (TPS)}
		* a TPS é armazenada em meio não volátil
		* a cada nova transação, a TPC é copiada para uma TPS específica da transação
		* TPS não é modificada ao longo da transação -> em caso de falha, descarta TPC e usa o TPS como corrente, não precisando acessar o banco para realizar restauração
* Checkpoint -> ponto em que o banco para as transações e escreve as alterações em disco -> se falhar depois, vai percorrer o log apenas a partir do checkpoint
	* diminui o número de redo na recuperação
* Rollback em cascata -> se uma transação é desfeita e há uma transação que leu dado alterado por ela, essa deve ser desfeita também
