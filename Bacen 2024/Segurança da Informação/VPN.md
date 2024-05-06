* def::**VPN (Virtual Private Network)**: rede virtual privada, provendo um túnel seguro de comunicação entre dois pontos, com uso de criptografia, garantindo { confidencialidade, autenticidade, integridade }; pode ser tanto entre dois firewalls, como com sede e filial, quanto entre usuário externo e rede interna
* **Topologias**
	* Intranet VPN / VPN SITE-to-SITE: comunica duas redes privadas; com IPSec, utiliza-se o modo túnel
	* Remote Access VPN / VPN HOST-to-SITE: comunica um nó, como um funcionário com seu computador, a uma rede privada
		* é recomendado não trabalhar dessa forma, mas sim num modelo HOST-to-HOST -> o túnel é entre um host externo e um host interno, esse ficando responsável por acessar recursos da rede interna
	* Extranet VPN
* **Protocolos de tunelamento**
	* **PPTP** -> baseado no protocolo PPP, operando na camada de enlace; leve, rápido e de fácil implementação; usa chave de 128 bits e, portanto, não é considerado seguro
	* **L2TP** -> baseado no protocolo L2F (Layer 2 Forwarding) e PPTP, atuando na camada de enlace; sem técnicas de segurança para garantir confidencialidade; capacidade de autenticação com PAP ou CHAP;
	* **OpenVPN** -> client open-source que utiliza OpenSSL, dando suporte para SSLv3 e TLSv1; cria camada segura entre a camada de aplicação e a de transporte; por padrão, roda em porta UDP, mas pode usar porta TCP; geralmente é mais rápido que o IPSec
	* **SSTP** -> protocolo proprietário da microsoft, utiliza SSLv3, podendo usar a porta TCP 443; possui integração completa com Windows;
	* **IPSec** -> opera a nível da camada de rede, podendo operar no modo transporte (host-to-host ou host-to-site) ou no modo tunelamento (site-to-site), podendo adicionar cabeçalhos AH (para autenticidade) e ESP (para confidencialidade); necessário liberar a porta UDP 500 para troca de chaves;
	* **MPLS** -> redes MPLS criam túneis seguros; permite isolamento de tráfego, não havendo aplicação de criptografia;
* **Classificações das redes**
	* **VLL (Virtual Leased Line)** -> emula circuito físico dedicado
	* **VPRN (Virtual Private Routed Network)** -> emula WAN com vários sites usando IP
	* **VPDN (Virtual Private Dial Network)** -> permite acesso remoto via PPP
	* **VPLS (Virtual Private Lan Segment)** -> emula segmento de rede local usando backboneIP