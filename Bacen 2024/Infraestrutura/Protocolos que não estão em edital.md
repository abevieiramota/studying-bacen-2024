* **POP3**
	* apenas download de e-mails
	* downloads apenas atômicos (não baixa partes de mensagens)
	* remove mensagens quando recebe (só permite acesso por um dispositivo)
	* porta 110 
	* porta 995 com SSL
* **IMAP**
	* apenas download de e-mails
	* em relação ao POP3
		* mais complexo e mais custoso de infra
		* permite leitura de mensagens por múltiplos dispositivos (sem remover), permitindo acesso offline
		* permite compartilhamento/acesso múltiplo a uma pasta
		* criação/gerenciamento de pastas
		* busca
		* download parcial
	* porta 143
	* porta 993 com SSL




CAMADAS / PROTOCOLOS / FUNÇÃO

7 - Aplicação / HTTP, SMTP, FTP, SSH, TELNET, POP3, IMAP, DNS / Prover serviços de rede às aplicações. Usada para enviar e receber dados de outros programas pela internet

6 - Apresentação / XDR, TLS / Criptografia, codificação, compressão e formatos de dados.

5 - Sessão / NetBIOS / Iniciar, manter e finalizar sessões de comunicação.

4 - Transporte / TCP, UDP, SCTP, DCCP / Transmissão de dados, segmentação.

3 - Rede / IP, (IPv4, IPv6), ICMP, ARP, RARP, NAT / Endereçamento lógico e roteamento; controle de tráfego.

2 - Enlace / Ethernet, IEE 802.1Q, Token Ring, Switch / Endereçamento físico; transmissão confiável de quadros.

1 - Física / Modem, 802.11 Wi-Fi, Bluetooth, USB, DSL / Interface com meios de transmissão e sinalização.