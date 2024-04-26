* **Características**
	* linguagem interpretada (comandos executados um a um, em sequência)
	* para atribuir permissão de execução, chmod +x script.sh
	* é necessário definir na primeira linha qual o shell será utilizado. Ex: #!/bin/bash
	* \# -> introduz comentário
* **Variáveis** (pode ser string ou número)
	* declaração -> nome_variavel = valor
	* uso -> $nome_variavel
* **Operações**
	* read nome_variavel -> input
	* echo variavel_ou_literal -> output
	* if
		* if \[ condição \];
		* then
		* ações
		* fi -> sempre necessário fechar com um fi
	* declaração de funções
		* nome_funcao()
		* {
		* ações
		* }
	* chamada de funções
		* nome_funcao par1 par2 par3
* **Argumentos**
	* $\# -> quantidade de argumentos passados ao script/função
	* $1 -> primeiro argumento
	* $0 -> nome do script executado
* exemplos
	* ![[Pasted image 20240419081711.png]]
		* ver que nos echo, a referência às variáveis é feita só colocando seu nome com o $, como é feito noutros locais
	* ![[Pasted image 20240425182227.png]]