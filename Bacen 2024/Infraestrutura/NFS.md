# NFS

* Network File System - cria sistema de arquivos remotos/distribuídos sobre arquitetura TCP/IP
* Características
	* permite acesso transparente a um servidor de arquivo remoto
	* porta ==2049== TCP
	* serviços { rpc.mountd, nfsd } - isso na versão 4
	* versões
		* v2 - suporte apenas para sistemas 32 bits (max file size = 2GB); UDP para transporte
		* v3 - suporte para sistemas 64 bits; TCP suportado
		* v4 - TCP obrigatório; considerado protocolo stateful; adicionados recursos de segurança
		* v4.1 - capacidade de clusterizar servidores, realizando consultas paralelas (pNFS)
		* v4.2
			* cópia do lado do servidor
			* arquivos esparsos (com espaços vazios)
			* reserva de espaço
			* uso de rótulos para controle de acesso
			* recursos de segurança { autenticação, autorização, auditoria etc }
	* desenvolvimento para operar em ambients Unix-like (daí SMB ser mais utilizado, por suportar mais sistemas)
	* /etc/exports -> configura que diretórios serão compartilhados
		* exemplo de entrada: /home/videos 192.168.1.0/255.255.255.0(ro) 
			* ro -> read only
			* rw -> read and write
			* pode informar IP, faixa de IP ou nome de domínio
	* /etc/fstab -> configura que diretórios serão acessados pelo cliente -> monta os diretórios remotos no sistema local