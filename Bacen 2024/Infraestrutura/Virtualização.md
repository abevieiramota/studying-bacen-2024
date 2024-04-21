* componentes de uma virtualização { máquina virtual/guest system, hypervisor/monitor de VM/Virtual Machine Monitor, máquina física, sistema real/nativo/hospedeiro }
* live migration -> movimentação das VMs de um hypervisor para outro (ex: quando vai ser dada manutenção no hardware), sem desligamento das VMs
* níveis de virtualização
	* nível de hardware -> virtualização diretamente sobre o hardware, sem SO abaixo; também chamada bare metal (associar metal a hardware -> adjacente ao hardware)
	* nível de SO -> virtualização entre SO e aplicações
	* nível de linguagem de programação -> virtualização é um programa de aplicação
* o throughtput (volume de dados/operações processadas com sucesso em determinado período de tempo) em sistemas virtualizados pode ser afetado por fatores como
	* recursos de hardware -> capacidade do hardware utilizado
	* hypervisor -> cada solução de hypervisor adota estratégias diferentes de virtualização, que podem impactar em desempenho
	* alocação de recursos para a VM
	* rede -> principalmente quando VMs precisar se comunicar entre si ou com recursos externos
	* carga de trabalho
	* otimização do SO
* comunicação entre VMs
	* comunicação interna (host-only) -> uso de barramento interno ou comutador virtual permite comunicação entre VMs em mesmo host, sem necessidade de uso da rede física
	* comunicação na mesma rede física -> rede local virtualizada, comunicação usando IP
	* comunicação em nuvem -> uso de VPN e sistema de mensageria
	* comunicação entre hosts -> permite migração de VMs entre hosts
* snapshot -> imagem instantânea do estado atual de uma VM ou de um sistema de armazenamento, útil para backup, recuperação rápida, testes de configuração/reversão de alterações (cria-se ponto de restauração, caso dê erro, reverte). clonagem de VMs
* VDI - Virtual Desktop Infrastructure -> permite usuários acessarem remotamente desktops virutais hospedados em servidores centralizados; facilita a atualização/manutenção com a centralização do gerenciamento; permite melhor eficiência de recursos; é necessária boa infra de rede
	* é diferente de Remote Desktop, que é o acesso remoto a um computador; usa protocolos como Remote Desktop Protocol (RDP - porta padrão 3389), Virtual Network Computing (VNC), entre outros
* tipos de hypervisors
	* tipo 1, baremetal, nativo { VMWare ESX Server, Microsoft Hyper-V, Citrix XenServer }
		* roda diretamente sobre o hardware, gerenciando o acesso aos recursos de hardware
		* hypervisor monolítico -> emula todo o hardware para as VMs -> para isso, precisa dos drivers
		* hypervisor microkernelizado -> hypervisor mais enxuto, menor superfícia de ataque -> drivers nos SO guest; ex: Hyper-V
	* tipo 2, hosted  { VirtualBox, VMWare Player, VMWare Server, QEMU }
		* acima do SO da máquina
* consolidação de servidores -> prática de combinar servidores/aplicações em servidores/hardware, usando virtualização
	* + eficiência energética -> diminuição de servidores físicos
	* + eficiência de espaço físico
	* simplificação de gestão
	* redução de custos
	* resiliência e redundância -> necessário garantir esses atributos, por meio de backup, técnicas de recuperação/tolerância a falhas etc
* virtualização x container
	* container é unidade de software leve e portátil que encapsula um aplicativo, suas dependências, bibliotecas, permitindo execução consistente em ambientes diversos; considerada forma de virtualização a nível de SO; promove { isolamento, portabilidade, orquestração, inicialização rápida }
	* frequentemente usados com microsserviços, faz uso de imagens;
* hypercall -> chamada ao hypervisor similar a um syscall a um kernel
* paravirtualização -> as chamadas do sistema convidado precisam ser modificadas para as instruções de baixo nível -> é uma das formas de virtualização, há comunicação entre o núcleo do SO hóspede e o hypervisor, os SO guest usam drivers do próprio hypervisor; resultando em melhor desempenho; ex: Xen
	* virtualização total/hosted -> diferentemente, basta instalar o SO na VM, não exige modificação do SO hóspede; ex: VMWare (tipo 1 e tipo 2), Hyper-V
* ! associar virtualização de X como oferecer uma abstração de X (ex: virtualização de hardware, gera uma abstração de forma a poder apresentar uma configuração ou múltiplas configurações de hardware baseadas no hardware comportado)
* virtualização não se refere apenas a servidores, mas também a storage, network, aplicações; ! não há o que se falar em virtualização de periféricos
* ![[Pasted image 20240421133911.png]]
	* p. 51 da apostila so_02
* 