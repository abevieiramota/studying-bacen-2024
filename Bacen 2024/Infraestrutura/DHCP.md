* Dynamic Host Configuration Protocol
* tem como função a configuração dinâmica dos endereços IP de computadores em uma rede
	* computador sem IP envia mensagem broadcast (!)
	* servidor DHCP verifica IP (reservado, se for o caso, ou não alocado) e envia para o computador
	* computador confirma o aceite para o servidor DHCP
* devem ser configurados
	* intervalo de endereços IP disponíveis para atribuição automática
	* intervalo de endereços IP não disponíveis para atribuição automática
	* máscara de rede -> usada para fazer a divisão da rede
	* gateway, que dá acesso à internet
	* endereço de servidor DNS a ser utilizado
* ! o servidor DHCP precisa de ao menos uma interface com IP fixo
* em servidor [[Linux]] o serviço é o dhcpd
	* ! o daemon do cliente é dhcp**c**d (tem um C na penúltima posição)
	* possui dois serviços, dhcpd4.service e dhcpd6.service
	* configuração é realizada no arquivo /etc/dhcpd.conf - exemplo:
	* ![[Pasted image 20240419160751.png]]
* 