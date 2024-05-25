* **multitarefa** -> permite a execução de múltiplos processos ao mesmo tempo ^so-multitarefa
	* no Linux, usa-se o fork para instanciar um novo processo
* **multiusuário** -> múltiplos usuários podem usar ao mesmo tempo, executar processos, por exemplo, simultaneamente ^so-multiusuario
* **Boot**
	* 1º estágio - encontra uma partição inicializável e depois carrega em memória o carregador de 2º estágio (GRUB, LILO etc), que reside em /boot
	* 2º estágio - o carregador de inicialização do 2º estágio solicita seleção do SO, depois carrega o kernel dele em memória e passa o controle para ele
	* systemd, sistema de inicialização de programas executados em background (daemons), assume o controle e carrega dispositivos/processos
	* Gerenciamento de >1 SO na máquina { LILO, GRUB }
		* LILO - LInux LOader
		* GRUB - GRand Unified Bootloader