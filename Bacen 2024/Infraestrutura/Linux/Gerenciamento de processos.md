* informações sobre processos que são gerenciadas pelo kernel, dentre outras
	* mapa de endereços de memória
	* estado atual, que pode ser
		* executável
		* dormente (aguardando algum recurso, como I/O)
		* zumbi (tentando se destruir)
		* parado (suspenso, sem permissão para ser executado) [Questão](https://www.qconcursos.com/questoes-de-concursos/questoes?q=Q2365596)
	* prioridade de execução
	* recursos associados
	* arquivos e portas de rede associados
	* máscara de sinalização (sinais bloqueados) #n_entendi 
	* proprietário do processo
* PID (Process ID) é o identificador de um processo, atribuído na ordem em que o processo foi criado
* PPID (Parent PID) é o PID do processo pai
* não há, de fato, chamada para criação de processo, mas sim de clone, com o comando fork()
	* o processo pai é clonado e o programa substituído
	* ele retorna o PID do processo clonado para o processo pai, que o chamou
* UID é o id do usuário que criou o processo, GID seu grupo
* niceness -> "prioridade" de tempo de CPU para o processo
	* \[-20, 19\] 
		* ! quanto menor, maior a prioridade! (associar a um ranking)
	* comando **nice** permite definir a prioridade (por padrão, define com valor 10)
	* comando **renice** permite alterar (! cuidado, apenas o renice permite alterar)
	* pode ser definido tanto por processo, quanto por usuário
* prioridade -> calculado como PR = 20 + NI 
	* ! cuidado, não confundir com niceness -> ver [Questão](https://www.qconcursos.com/questoes-de-concursos/questoes?q=Q2394654)
* a árvore de processos tem na sua raiz o processo init, de PID = 1, que é criado na inicialização e tem como responsabilidades
	* executar scripts de inicialização
	* ser pai de processos
	* chamar o comando exit para processos concluídos
	* receber processos órfãos #n_entendi 
	* ![[Pasted image 20240419171313.png]]
* sinais podem ser enviados para os processos
	* meios
		* comunicação entre processos
		* comandos em terminal, como ctrl + z
		* comando kill (! cuidado, pode enviar outros sinais, além de 'matar')
			* kill \[-SINAL\] PID
			* killall \[-SINAL\] NOME_PROC (! recebe o nome do processo, não o PID; mata todo processo com o nome informado)
			* ! o sinal pode ser especificado pelo número (ex: -9), ou pelo nome, prefixando com SIG (ex: -SIGKILL)
		* enviados pelo kernel (ex: divisão por 0, 'morte' de processo filho)
	* sinais
		* 1 - HUP - Suspender
		* 2 - INT - Interromper
		* 3 - QUIT - Abandonar
		* 9 - KILL - Matar
		* 15 - TERM - Término do software (! default)
* monitoramento
	* ps -> pode exibir { PID, UID, prioridade, terminal de controle de processos, memória consumida, estado atual }
		* -a -> mostra todos os processos
		* -u -> exibe o nome do usuário iniciador e o momento de início
		* -x -> exibe processos não associados a terminais
		* -l -> exibe mais campos
		* -e -> exibe as variáveis de **e**nvironment associadas ao processo
		* -f -> exibe a árvore de execução dos processos
		* muito comum -> ps -aux
	* top -> mostra um resumo dos processos ativos e uso de recursos, atualizando regularmente (default 10s)
	* jobs -> mostra processos parados ou executando em background