* também chamado gateway de aplicação, firewall de aplicação, firewall proxy
* **Características**:
	* estabelece duas conexões -> não há mais uma conexão direta entre o cliente e o servidor
	* permite uma camada adicional de autenticação e segurança
	* por padrão, não verifica o conteúdo dos pacotes
	* **DEEP Packet Inspection** **(DPI)**: funcionalidade para inspecionar o conteúdo da camada de aplicação
	* pode implementar recurso de cache 
* ! atua na camada de aplicação, tratando as requisições como se fosse a aplicação
* pode ser transparente (não exige configuração por parte do cliente), ou não transparente
* funciona ao mesmo tempo como cliente e servidor (recebe requisições e submete requisições!)
* exemplos de regras em proxies
	* restringir acesso FTP a usuários anônimos
	* restringir acesso HTTP a certos domínios
* **Proxy Reverso**: recebe tráfego externo e repassa para servidores, servidor, implementando, por exemplo, { balanceamento de carga, segurança, criptografia, cache, compressão } ^def-proxy-reverso
* **Squid**: servidor proxy do Linux
	* suporta { FTP, HTTP, HTTPS, ICAP, ICP, HTCP etc }
	* possui caching
	* versões para Unix e Windows
	* pode ser usado como proxy local, mantendo cache etc -> problema que guarda dados do usuário, como URLs acessadas, podendo prejudicar a privacidade
	* arquivo de configuração -> /etc/squid/squid.conf
		* para implementar proxy transparente, é preciso configurar o modo intercept