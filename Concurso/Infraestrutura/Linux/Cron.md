* programa de agendamento
* multiusuário - cada usuário pode fazer seus agendamentos
* Agendamentos ficam no arquivo crontab, organizado em tabelas com formato específico
	* pode ser acessado com o comando crontab -e
	* crontab de usuários -> /var/spool/cron/crontabs/
	* crontab global -> /etc/crontab
* **Formato** minutos; horas; dias do mês; mês; dias da semana [Questão](https://www.qconcursos.com/questoes-de-concursos/questoes?q=Q2239101)
	* minutos -> 0-59
	* hora -> 0-23
	* dia do mês -> 1-31
	* mês -> 1-12
	* dia da semana -> 0 a 7
		* ambos 0 e 7 representam o domingo
	* \* -> todos os valores
	* pode-se separar valores com vírgula (ex: 2,3 -> valor 2 e 3)
	* pode-se especificar intervalos com hífen (ex: 2-4 -> valor 2 a 4)
	* nos dias da semana -> 3L indica a última (L -> **L**ast) quarta-feira (3)
	* nos dias do mês -> 2W significa o primeiro dia da semana igual ou posterior ao dia 2
	* nos dias da semana -> 3#2 significa, das quarta-feiras (3), a 2ª
	* / -> parte de um valor -> \*/6 no campo de horas indica que deve ser executado a cada 6 horas
* **Exemplos**
	* 5 0 \* \* \* $HOME/bin/script.sh -> executa 5 minutos após a meia-noite, todos os dias
	* 15 14 1 \* \* $HOME/bin/script.sh -> executa às 14:15 do 1º dia de cada mês
	* 0 22 \* \* 1-5 $HOME/bin/script.sh -> executa às 22h nos dias da semana (1-5 = seg a sex)