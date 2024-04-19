* Domain Name System - esquema hierárquico de atribuição de nomes baseado no domínio e de um sistema de banco de dados distribuído
* port::UDP/53 (consultas) TCP/53 (comunicação entre servidores)
* funcionamento
	* aplicativo chama o resolvedor, passando nome que deseja resolver
	* resolvedor consulta servidor DNS local - ! **consulta recursiva**, o servidor irá responder, mesmo que precise, de forma transparente, consultar outros servidores
	* servidor DNS local responde ao resolvedor
		* caso ele não possua entrada, consulta outros servidores DNS (! **consulta iterativa**)
	* resolvedor informa IP ao aplicativo
	* ![[Pasted image 20240419124125.png]]
* servidores DNS mantêm cache, para evitar consultas frequentes a servidores de alto nível
* o servidor DNS padrão Unix mais conhecido é o BIND (Berkeley Internet Name Domain)
	* /etc/bind/named.conf -> principal arquivo de configuração; por padrão vem configurado como servidor de cache
	* ![[Pasted image 20240419145911.png]]
	* os arquivos referenciados contêm os endereços dos servidores DNS a serem consultados em relação às zonas indicadas
	* o nome do serviço pode aparecer como *bind9*, em dists Debian, ou *named*, em dists Red Hat
* os registros na base de dados do DNS são chamados 'registros de recursos (RRs)' e seguem a estrutura \<nome_dominio, TTL, classe, tipo, valor\>, com classe sendo normalmente IN (internet) e os tipos sendo um dos valores:
	* A -> endereço IPv4 (Address)
	* AAAA -> endereço IPv6
	* CAA -> Certification Authority Authorization
	* MX -> Mail Exchanger, no formato \<prioridade> \<domínio de servidor de e-mail\>
	* NS -> Name Server, indica os servidores DNS autoritativos, que contêm os registros atualizados para o domínio
	* CNAME -> Canonical Name, mapeia um subdomínio (ex: blog.mozilla.com) para um domínio (ex: mozilla.wpengine.com)
		* ! cuidado, o valor é um domínio, e não um endereço IP
		* havendo CNAME mapeando, não se deve informar registro A ou TXT
	* PTR -> usado em DNS reverso
	* SRV -> computadores que hospedam serviços específicos
	* TXT -> informações sobre servidor, rede, datacenter etc
* resposta autoritativa x não-autoritativa
	* respostas autoritativas têm garantia de estarem atualizadas, enquanto não-autoritativas podem estar desatualizadas (cache desatualizado)
	* servidores caching-only respondem apenas de forma não-autoritativa
	* ver o registro NS
* os servidores no topo da hierarquia são chamados Root Name Servers, abaixo dos quais ficam os Top Level Domains (ex: servidores dos domínios .com, .edu etc)