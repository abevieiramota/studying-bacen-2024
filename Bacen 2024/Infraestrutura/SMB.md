# SMB

* Server Message Block protocol
* SAMBA implementa o protocolo SMB/CIFS para sistemas Unix-like
	* permite compartilhar arquivos em rede com dispositivos Microsoft e Linux - em ambos, usa-se o protocolo SMB/CIFS
	* daemon smbd
	* arquivos de configuração
		* /etc/samba/smb.conf -> configurações globais
			* dividido nas seções { \[global\], \[homes\], \[printers\], \[nome-de-compartilhamento-qualquer-config-especifica\] }
			* parâmetros
				* path -> caminho de diretório compartilhado
				* valid users -> usuários autorizados a acessar compartilhamento
				* read only -> se o compartilhamento é só de leitura
				* browseable -> se o compartilhamento é visível navegando na rede
				* guest ok -> se aceita convidados
				* comment -> comentário sobre o compartilhamento
				* lock -> diretório onde arquivos de lock serão armazenados - usados para garantir a integridade de arquivos em caso de modificações concorrentes
				* invalid users -> blacklist de usuários
		* /etc/samba/smbpasswd -> contém senhas criptografadas dos usuários SAMBA, utilizado para autenticação
		* /etc/samba/secrets.tdb -> contém chaves de segurança do SAMBA, usado em autenticação/criptografia
		* /etc/samba/usermap -> mapeia nomes de usuários entre sistemas Linux e Windows
		* /etc/samba/shares -> configuração de compartilhamento de arquivos
		* /etc/samba/printers -> configuração de impressoras compartilhadas
	* principais comandos
		* smbd -> inicia servidor SAMBA
		* nmbd -> inicia servidor de resolução de nomes NetBIOS
		* testparm -> verificar o arquivo de configuração smb.conf quanto a erros de sintaxe
		* smbpasswd -> definição/alteração de senha de usuários
		* smbclient -> ferramenta de linha de comando para interagir com compartilhamentos SAMBA, como transferir arquivos
		* net -> ferramenta que permite realizar diversas operações, como gerenciar contas de usuários e máquinas