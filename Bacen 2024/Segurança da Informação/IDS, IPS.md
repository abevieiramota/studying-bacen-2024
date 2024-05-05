* def::**IDS (Intrusion Detection System)**: 
	* ! apenas detecta, não agindo sobre o tráfego
	* é posicionado de forma paralela ao tráfego
	* ex: câmera que flagra carro sem farol e registra
	* **Tipos**
		* **NIDS (Network-based IDS)**: monitora tráfego
			* switches/roteadores modernos já possuem recursos de NIDS embutidos
			* V
				* atuando em modo passivo (monitorar, sem afetar o tráfego), não impactam no desempenho da rede
				* difíceis de serem detectados por atacantes
			* DV
				* diante de tráfego intenso, pode não ser muito eficiente
				* ! incapacidade de analisar informações criptografadas (ele fica no caminho do túnel, o tráfego está criptografado!)
				* incapacidade de bloquear o ataque, restando apenas a detecção
		* **HIDS (Host-based IDS)**: monitora o host
			* V
				* por monitorar no host, permite detectar ataques mais específicos que o NIDS
				* capacidade de tratar dados criptografados
				* não são afetados por elementos de rede
			* DV
				* difícil configuração, dado que devem ser consideradas características do host
				* podem ser derrubados com DoS
				* degradam o desempenho do host
		* **IDS baseado em pilhas**: atual no fluxo de desencapsulamento dos pacotes nas pilhas TCP/IP
	* **Técnicas de captura**
		* **Port Span**: replica todo tráfego do switch para uma porta conectada com o IDS (necessário que a porta tenha capacidade de banda suficiente)
		* **Splitting Wire/Optical TAP**: usa-se um hub para espelhar o tráfego
		* **Port Mirror**: replica tráfego apenas de uma porta, o resto é igual ao Port Span
* def::**IPS (Intrusion Prevention System)**:
	* atua de forma preventiva, 
	* é posicionado no meio do tráfego, inline
	* ex: blitz que flagra carro sem farol e para ele
	* **Tipos** { NIPS, HIPS } -> similar aos tipos de IDS
* def::**IDPS**: IDS + IPS
* def::**WIPS (Wireless IPS)**: 
* **Metodologias de detecção**
	* **Base de Conhecimento** -> base de regras/assinaturas com as quais acessos/pacotes são comparado e, em caso de match, a solução pode reagir (geralmente IDS)
	* **Base de Comportamento** -> base de padrões de comportamento de acessos/pacotes e, em caso de match, a solução pode reagir (geralmente IPS)
* **Resultados**
	* Verdadeiro positivo -> tráfego suspeito detectado
	* Falso negativo -> tráfego suspeito não detectado
	* Falso positivo -> tráfego legítimo que o equipamento acusa como suspeito
	* Verdadeiro negativo -> tráfego legítimo que o equipamento considera legítimo