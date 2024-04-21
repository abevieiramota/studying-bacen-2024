* Active Directory - serviço de diretórios do Windows (a partir da versão 2000)
* diretório é similar à ideia de 'catálogo'
* domínio -> agrupamento lógico de contas e recursos; pode ser dividido em OU (Organizational Units), não sendo obrigatório
	* é estruturado de forma hierárquica, daí se falar em 'árvore de domínios' e 'floresta', quando, por exemplo, há um grupo de empresas
* workgroup -> contas/grupos válidos apenas em um servidor específico #n_entendi 
* catálogo global -> controlador de domínio que armazena uma cópia de todos os objetos do AD em uma floresta
* serviços
	* AD CS (Certificate Service) -> cria e gerencia certificados de chaves públicas
	* AD DS (Domain Service) -> armazena informações sobre usuários, computadores, dispositivos etc (! é o que normalmente se chama por AD apenas)
	* AD FS (Federation Services) -> operação com múltiplas plataformas #n_entendi 
	* AD LDS (Lightweight Directory Service) -> mais leve que o AD DS, por não requerer o desenvolvimento de domínios/DCs #n_entendi 
	* AD RMS (Rights Management Service) -> serviço para gerenciar proteção de informações
* arquivos
	* Ntds.dit -> armazena no servidor todos os dados (associar o .dit a Directory Information Tree) ! decorar
	* Edb.chk -> checkpoint utilizado para recuperação de estado
	* Edb.log -> logs de transações
	* Res1.log e Res2.log -> log reverso, usado quando não há espaço em disco #n_entendi 
	* Schema.ini -> inicializa o Ntds.dit, depois não é mais utilizado
* ! utiliza DNS para nomear e resolver nomes de domínio
* ! só funciona com o sistema de arquivos NTFS #TODO verificar