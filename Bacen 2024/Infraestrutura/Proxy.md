* também chamado gateway de aplicação, firewall de aplicação, firewall proxy
* ! atua na camada de aplicação, tratando as requisições como se fosse a aplicação
* pode ser transparente (não exige configuração por parte do cliente), ou não transparente
* funciona ao mesmo tempo como cliente e servidor (recebe requisições e submete requisições!)
* introduz degradação de desempenho, pelo custo de processamento da requisição no proxy
* exemplos de regras em proxies
	* restringir acesso FTP a usuários anônimos
	* restringir acesso HTTP a certos domínios
* proxy reverso
	* recebe tráfego externo e repassa para servidores, servidor, implementando, por exemplo, { balanceamento de carga, segurança, criptografia, cache, compressão }
* squid -> servidor proxy
	* suporta { FTP, HTTP, HTTPS, ICAP, ICP, HTCP etc }
	* possui caching
	* versões para Unix e Windows
	* pode ser usado como proxy local, mantendo cache etc -> problema que guarda dados do usuário, como URLs acessadas, podendo prejudicar a privacidade
	* arquivo de configuração -> /etc/squid/squid.conf
		* para implementar proxy transparente, é preciso configurar o modo intercept
* 