* def::**Firewall**: lógica similar à de uma porta corta-fogo, é elemento de borda que concentra a entrada e saída de pacotes na rede dentro de um fluxo, seguindo um princípio de segurança da informação chamado Choke Point
* **Características**
	* por padrão, firewall não contém antivírus, mas em soluções modernas essas funções são conjugadas
	* SOs modernos já vêm com um firewall para ele
	* pode adotar política de { whitelist (descartar, bloqueio por padrão), blacklist }
		* whitelist é o recomendado, bloquear por padrão -> mas depende do contexto -> ex: numa rede com acesso à internet para pesquisas amplas, acadêmicas, pode ser melhor trabalhar com blacklist, dada a impossibilidade de definir de antemão quais sites serão acessados
* V
	* maior controle
	* centralização de autenticação
	* capacidade de gerar logs e trilhas de auditoria
* DV
	* asd
* **Topologias com Firewall**
	* **Dual-homed host**: elemento que atua como firewall e possui duas interfaces, uma para a rede externa e outra para a rede interna -> ex: servidor Linux com IPTables
	* **Screened host**: #n_entendi 
	* **Screened-subnet host**: uso de dois firewalls e [[Segurança da Informação/Básico#^def-dmz|DMZ]] #n_entendi 
* **Classificações**
	* **Firewall Bridge**
		* atua na camada de enlace do modelo OSI
		* não tem endereço IP (por atuar na camada de enlace)
		* por conta disso /\\ , não tem visibilidade externa
		* limitado em relação às informações que pode filtrar
	* **Firewall - filtro de pacotes**
		* atua na camada de rede do modelo OSI, conseguindo interpretar algumas informações da camada de transporte (no modelo TCP/IP não há uma separação tão rígida entre as camadas rede e transporte)
		* também conhecido com firewall estático -> é stateless, não guarda estado
		* foca na filtragem de IP's e portas (origem e destino) -> mapeamento de serviços por meio de portas (ex: filtro de acesso web, porta 80)
		* é importante configurar regras para entrada e saída de fluxos -> ACL (Access Control Lists) -> regras de firewall nesse nível
	* **Filtro de pacotes baseados em estados**
		* atua na camada de transporte do modelo OSI
		* também conhecido como firewall dinâmico, statefull ou filtro de estado
		* não se restringe à análise de certos cabeçalhos, podendo tratar fluxos, por exemplo
		* o sentido do fluxo não é mais importante (entende que uma requisição aguarda uma resposta, permitindo ela, dado que a requisição foi permitida) -> implementado com uso de tabela de estado/conexão
		* para UDP, utiliza o conceito de contextos -> permitindo um controle de estado
	* [[Proxy]]
	* [[Proxy#^def-proxy-reverso|Proxy reverso]]
	* **WAF (Web Application Filter)**: tipo de firewall criado especificamente para proteger aplicações WEB de ataques sofisticados na camada de aplicação (ex: evitar SQL injection)
		* ele não protegerá toda a rede, nem os usuários internos
		* normalmente, usam-se também outros firewalls, tratando outras características do tráfego
		* há estudos que mostram que o maior volume de ataques ocorrem na camada de aplicação
	* **UTM (Unified Threat Management)**: solução integrada de componentes de segurança, como VPN, Firewall, Antivírus, filtros etc
* **Defesa em profundidade**: uso de mais de um firewall, criando uma sequência de barreiras
* **Filtros**: capacidade de selecionar tráfego que será permitido
* **Bastion host**: servidor especializado para fornecer serviços ao público externo; ! importante aplicar técnicas de hardening
* **SIEM (Security Information and Event Management):** focada na geração de alertas e relatórios, correlacionando logs diversos, habilitando boa rastreabiliadde