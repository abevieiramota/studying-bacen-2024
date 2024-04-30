* monitoring/alerting tool
* **Features**
	* monitoramento { apps, serviços, SO, rede, system metrics etc }
	* view centralizada de infra de TI
	* alertas { email, SMS etc }
	* event handlers + base de conhecimento de soluções
	* capacity planning
	* reporting
	* multi-tenant
	* third-party apps/addons
	* open-source
	* usa protocolos/meios de comunicação com nós { SNMP, ICMP, JMX, agents etc }
* Componentes open-source
	* Nagios Core
	* Nagios Frontends
	* Nagio Plugins
	* Nagio Add-ons
* Configuração
	* /usr/local/nagios/etc/nagios.cfg -> { logging, objects, cache etc }
	* /usr/local/nagios/etc/resource.cfg -> macros de usuários
	* /usr/local/nagios/etc/{hosts, services, commands}.cfg