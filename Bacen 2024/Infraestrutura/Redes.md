* redes = 2+ computadores interconectados via rede de comunicação
* tipos de redes
	* formas de interação: { par-a-par, cliente-servidor }
		* par-a-par ~ peer-to-peer ~ P2P -> sem hierarquia; cada nó = par; cada nó recebe e envia dados (assume papel de cliente/servidor de forma dinâmica);
		* client-server -> papéis específicos { client, server }
			* servidor dedicado -> apenas um serviço; else, servidor compartilhado
	* tipos de conexão { ponto-a-ponto, multiponto }
		* ponto-a-ponto -> 1:1; com N nós, o total de conexões ponto-a-ponto é N \* (N - 1) / 2
		* multiponto -> o meio transmite para vários nós ~ difusão
	* topologias { barramento, anel, }
		* barramento
			* conexão: difusão/broadcast, todos nós vendo a informação trafegada; 
			* exige controle de acesso para evitar conflito/colisão de acesso ao meio físico; 
			* escalável, limitada ao tamanho do barramento;
			* boa tolerância a falhas -> se um computador para de funcionar, não afeta os demais;
			* não tem elemento central!
		* anel 
			* conexão: ponto-a-ponto, informação trafegando nos nós até chegar ao destino (pode trafegar em qualquer direção);
			* baixa tolerância a falhas -> caso um computador falhe, todo o meio de comunicação é interrompido!; pode ser amenizada com tráfego bidirecional;
			* controle de acesso pode ser feito com protocolos como token ring -> usa-se um "token" que é trafegada entre os nós e o envio de informações só é feito quando se tem esse "token";
				* caso o nó de destino não seja encontrado, o nó emissor deve remover da rede o token e quadro de dados transmitido
			* baixo custo de cabeamento!
		* estrela
			* conexão: ponto-a-ponto + nó central, responsável por direcionamento/comutação de mensagens;
			* exige controle de acesso (? por quê?);
			* gera capacidade de gerenciamento de rede (limitação de velocidade etc);
			* boa tolerância a falhas, em relação aos nós/links não centrais; mas se o nó central falhar, a rede ficará off;
			* escalabilidade depende da capacidade do nó central -> expansão pode envolver conexão entre múltiplas estrelas, com hierarquia;
		* mesh
			* conexão: ponto-a-ponto;
			* interconexão entre (quase) todos os nós -> escalabilidade aumenta exponencialmente com a quantidade de nós;
			* excelente tolerância a falhas (sem centralização);
			* ótimo desempenho, por ser ponto-a-ponto (limitado pelo desempenho dos links de comunicação);
			* custo operacional muito alto;
			* usadas para permitir rotas alternativas entre nós em WANs, para garantir disponibilidade;
			* full-mesh -> todos nós conectados (pontos positivos e negativos são ampliados);
		* árvore
			* hierarquia entre nós centrais -> padrão atual adotado em roteadores/switches na internet;
			* boa escalabilidade e boa tolerância a falhas;
* tecnologias de acesso ao meio físico
	* CSMA/CD - **C**arrier **S**ense **M**ultiple **A**ccess with **C**ollision **D**etection
		* detecção de colisão + reinicio de transmissão
		* verificar se meio está livre -> transmitir informação -> monitorar meio -> se outro sinal -> enviar sinal JAM, informando a colisão (os nós aguardarão tempo aleatório para reenvio)
	* CSMA/CA - **C**arrier **S**ense **M**ultiple **A**ccess with **C**ollision **A**voidance
		* evita colisão
		* verificar se meio está livre -> enviar quadro informando que meio será utilizado por X tempo -> transmitir dados (demais nós ficarão aguardando)
* topologia { física (conexão física), lógica (forma como dados são trafegados) }
	* há certa liberdade entre a topologia física e lógica - ex:
		* física = estrela, lógica = barramento
		* física = estrela, lógica = anel
* em relação a alcance geográfico/organizacional
	* Personal Area Network (PAN) -> meu celular + meu fone bluetooth
	* Local Area Network (LAN) -> área limitada
		* geralmente usa ethernet;
		* alta taxa de transmissão ~Gbps
		* baixa taxa de erros e retransmissões
		* baixo custo de cabeamento
		* topologias comuns { estrela, anel, barramento }
		* tamanho limitado -> gerenciamento mais fácil (mais fácil de entender limites/gargalos)
	* Metropolitan Area Network (MAN) -> ~ bairro ~ cidade
		* ~interligação de diversas LANs em uma região geográfica extensa
		* normalmente usam fibras ópticas
		* alta taxa de transmissão ~Gbps
		* baixa taxa de erro
		* médio custo de cabeamento
		* topologia comum -> anel (mais barato para regiões metropolitanas)
		* atualmente muitas usam ethernet, sendo chamadas METRO Ethernet
	* Wide Area Network (WAN) -> ~ país ~ continente
		* ~interligação entre LANs e MANs
		* taxa de transmissão variada (depende das condições do trajeto)
		* taxas de erro mais elevadas
		* alto custo de cabeamento
		* ex: rede do RNP (Rede Nacional de Pesquisa)
		* -> internet
	* Wireless Local Area Network (WLAN) -> LAN sem fio
		* mais comum = WI-FI
		* ! não confundir WI-FI com Wireless -> WI-FI é espécie de Wireless (outros exemplos são Bluetooth)
	* redes LAN e MAN -> não comutadas (não dependem de roteadores); redes WAN -> comutadas (dependem de comutadores) ou não comutadas (ex: satélite)
* formas de degração de sinal
	* atenuação -> redução gradativa da amplitude do sinal; pode ser restaurada;
	* ruído -> interferências internas/externas
	* reflexão/eco -> "*Interferência ocorrida pela reflexão do sinal no destino. A sua ocorrência é devida pela falta de casamento de impedância dos meios e das fontes.*"
* digitalização
	* amostragem
	* quantização
	* codificação
		* Non Return to Zero (NRZ) -> { bit 0: sinal baixo, bit 1: sinal alto }
		* Non Return to Zero Inverted (NRZI) -> { bit 0: mantém o mesmo sinal, bit 1: inverte o sinal}
		* Manchester -> { bit 0: sinal baixo que sobe, bit 1: sinal alto que desce }
			* + usada em rede Ethernet
			* facilidade para recuperação de erros
		* Manchester diferencial -> { bit 0: 1ª metade do sinal é inverso da última metade do sinal anterior, bit 1: duas metades com mesma altura } #n_entendi 
* multiplexação -> envio de diversos sinais por um único meio, criando canais internos
	* FDM -> divisão por frequência
	* TDM -> divisão por tempo
	* CDMA -> divisão por códigos
	* ! é possível usar FDM e TDM juntos