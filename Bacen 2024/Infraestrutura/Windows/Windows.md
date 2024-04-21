* [[AD]] (Active Directory)
* serviços
	* IIS (Internet Information Server) -> servidor Web padrão do Windows Server (não vem instalado por padrão)
	* drivers assinados digitalmente são disponibilizados no Windows Update
	* Windows Defender
		* vem ativado por padrão, podendo ser desativado
		* conjunto de componentes { antivírus, firewall, parenting control, SmartScreen (integrado ao Edge, protege contra sites mal-intencionados) }
	* a habilitação de funções, como DHCP e DNS, é feita em Iniciar > Ferramentas Administrativas > **Gerenciador de Servidores** > Funções > Adicionar Funções
	* DHCP - ativação no cliente
		* ![[Pasted image 20240420211934.png]]
	* ipconfig /all -> mostra informações de rede (! cuidado, no Linux é i**f**config)
	* Remote Desktop -> permite acessar o servidor; deve ser configurado no servidor que usuários têm permissão; usuário se conecta com o mstsc
	* Virtualização
		* VDI (Virtual Desktop Infrastructure) -> provê e gerencia desktops virtuais, criados por uma VM controlada por um hypervisor (camada de software entre hardware e SO que gera abstração de máquina virtual)
	* FSRM (File Server Resource Manager) -> permite gerenciar dados armazenados em servidor de arquivos
		* gerenciamento de contas, limitando espaço por conta
		* classificação de arquivos
		* triagem (que arquivos podem ser armazenados)
		* relatórios de armazenamento
		* shadow copy -> cria cópia dos arquivos em outro local para recuperação em caso de problemas - ajuda a lidar com casos de ransomware; configura como "Criar ponto de restauração"
		* suporta apenas NTFS
		* exemplos de políticas { expirar arquivos velhos, cota de dados, notificação por uso de cota, envio automático de relatórios }
	* impressão, faz uso de spooler (fila de impressão) e um protocolo que pode ser utilizado, IPP (Internet Printing Protocol); por padrão, todos usuários têm permissão de impressão para uma impressora recém configurada
	* PowerShell
		* scripts são compilados sobre o CLR (Common Language Runtime), chamados cmdlet (command-let) (ex: Copy-Item)
		* comandos usados no cmd.exe também funcionam no PS, além de diversos comandos de shell Linux, como o ls
		* cmdlets (normalmente seguem o formato Verbo-Substativo e não é case-sensitive)
			* Get-Location -> diretório atual
			* Set-Location -> altera o diretório atual
			* Copy-Item, Remove-Item, Move-Item, Rename-Item, New-Item
			* Enter-PSSession -> sessão com computador remoto
			* Get-AppxPackage -> lista pacotes instalados
			* Remove-AppxPackage
* há versão com instalação mínima, Server Core, que ocupa menos espaço, usada em servidores, tendo menor superfície de ataque devida à menor base de código (ex: servidor Hyper-V não tem GUI, que não é necessária)
* versões
	* Windows Server 2003
		* sistemas de arquivos suportados { FAT16, FAT32, NTFS }
		* na versão 32 bits, suporta endereçamento de até 4GB de memória, que pode ser estendido com PAE - Physical Address Extension, configurado adicionando "/PAE" ao arquivo Boot.ini
		* disponibilizado nas versões { Web, Standard, Enterprise, Datacenter } edition
	* Windows Server 2008
		* última a operar em 32 bits
		* Windows PowerShell
			* fornece ferramentas de linha de comando, chamadas cmdlets
		* para virtualização, oferece
			* Hyper-V -> permite virtualizar máquinas em um mesmo servidor físico (não é necessário aplicativo terceiro, como VMWare); permite gerenciamento remoto; pode virtualizar outros SOs, como Linux; necessário habilitar a role hyper-V
			* Remoteapp e TS Web Access -> permite acesso remoto
		* disponibilizado nas versões { Itaniun, R2 } + as mesmas do WS2003
			* versão Windows Server 2008 Itaniun é otimizada para aplicações de banco de dados de alto desempenho, permitindo hot swamp de processadores e memórias
			* versão R2 busca otimizar consumo de eletricidade e custos indiretos, bem como melhorias de desempenho
	* Windows Server 2012
		* opera apenas com 64 bits
		* suporta o novo sistema de arquivos ReFS (Resilient File System), que resolve problemas do NTFS. Tem como vantagens:
			* verificação automática de integridade e limpeza de dados
			* remoção da necessidade de rodar o chkdsk
			* proteção contra degradação de dados
			* manuseio de falha no disco rígido e redundância
			* integração da funcionalidade RAID
			* manejo de caminhos e nomes de arquivos muito longos
			* virtualização e agrupamento de armazenamento
		* tem como requisitos mínimos
			* processador 64 bits, 1.4GHz
			* 3**2**GB de disco
			* 512MB de memória RAM
	* Windows Server 2016
		* gerenciamento de pacotes com PackageManagement
		* PowerShell aprimorado, com melhorias para perícia digital e segurança
		* Credential Guard, Windows Defender, IIS 10.0 (com suporte para HTTP/2)
	* Windows Server 2019
* possui base grande de dispositivos PnP (Plug and Play) - o SO baixa e configura o driver após plugado o dispositivo
* usuários, grupos, permissões
	* tipos de contas { padrão, admin, guest }
	* grupos servem para agrupar configurações de um conjunto de usuários
	* permissões de { Ler, Ler/Escrever } podem ser dadas a arquivos para grupos/usuários
* 