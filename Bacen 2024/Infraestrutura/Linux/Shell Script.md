* Unix Shell
	* linguagem interpretada (comandos executados um a um, em sequência)
	* para atribuir permissão de execução, chmod +x script.sh
	* é necessário definir na primeira linha qual o shell será utilizado. Ex: #!/bin/bash
	* \# -> introduz comentário
	* variáveis (pode ser string ou número)
		* declaração -> nome_variavel = valor
		* uso -> $nome_variavel
	* input de dados
		* read nome_variavel
	* print de dados
		* echo variavel_ou_literal
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
	* argumentos
		* $\# -> quantidade de argumentos passados ao script
		* $1 -> primeiro argumento
		* $0 -> nome do script executado
	* exemplo
		* ![[Pasted image 20240419081711.png]]
		* ver que nos echo, a referência às variáveis é feita só colocando seu nome com o $, como é feito noutros locais
	* 