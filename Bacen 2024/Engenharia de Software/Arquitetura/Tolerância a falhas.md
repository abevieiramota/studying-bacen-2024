todo::Estudar sobre tolerância a falhas - Sommervile cap. 13

* def::**RAID** (Redundant Array of Independent Disks): combinação de várias unidades de armazenamentos, agrupadas como uma unidade lógica, com acesso transparente e capacidades diversas, como redundância, ganho de performance, aumento de capacidade
	* **Implementação**: pode ser realizada via { hardware, software }
		* **Hardware**: faz uso de uma controladora que faz uma interface com o SO e os discos (ficando transparente para o SO)
			* mais performático
			* o fabricante quem cria a controladora
		* **Software**: no SO que é configurada a camada lógica
			* maior consumo de CPU
	* def::**RAID 0**: divide arquivos em blocos e distribui a gravação desses blocos no conjunto de discos paralelamente - stripping
		* **V**: maior capacidade de escrita e de leitura (ex: dobro com 2 discos) !capacidade da controladora pode ser gargalo(ex: 2 discos com 100kbps e controladora com 150kbps -> capacidade é 150kbps)
		* **DV**: não há redundância -> dobro de risco de problemas; 
	* def::**RAID 1**: blocos de arquivos são replicados em mais de um disco (foco em disponibilidade/redundância) - mirroring/duplexing
		* **V**: + redundância/resistência a falhas; + desempenho de leitura (pode ler parte de um disco e parte de outro); manutenção a quente (hot-swap)
		* **DV**: perda de capacidade de armazenamento
		* !desempenho de escrita é mantido (escreve em paralelo nos dois discos) (!controladora é gargalo)
	* def:: **RAID 1+0**: união do RAID 0  e o RAID 1; pode ser montado de duas formas, de acordo com a ordem em que se aplicam os RAIDs
		* RAID 01: RAID 0 > RAID 1 > discos: divide os blocos em dois grupos, cada grupo sendo replicado em dois discos
		* RAID: 10: RAID 1 > RAID 0 > discos: replica os blocos em dois grupos, cada grupo sendo dividido em dois discos
		* **V**: ver V dos RAID 0 e 1
		* **DV**: ver DV dos RAID 0 e 1
		* !mínimo de 4 discos (com 4 discos de 1TB, a capacidade de armazenamento é de 2TB)
	* def::**RAID 5**: faz uso de bits de paridade distribuída, para agregar performance e redundância; similar ao RAID 4, mas, diferente desse, que mantém um disco todo para bits de paridade, no RAID 5 os bits de paridade são distribuídos em todos os discos
		* **V**: melhor aproveitamento de recursos, com ganho de desempenho e redundância
		* **DV**: 1 disco usado para bit de paridade
		* !mínimo de 3 discos, sendo 1 disco perdido para bits de paridade (!é fixo, 1 disco é perdido, independente da quantidade de discos usados)
		* distribuição pelo método Round Robin
		* !tolera falha de 1 disco no máximo (se perder 2, não consegue recuperar dados com os bits de paridade)
	* def::**RAID 4**: ver RAID 5, mas RAID 4 mantém todos os bits de paridade em um mesmo disco (não é paridade distribuída)
	* def::**RAID 50**: união do RAID 5 com o RAID 0
		* study_more::RAID 50
		* !mínimo de 6 = 2\*3 discos
		* !tolera falha de 1 disco em cada strip do RAID 0 (ou seja, uma falha em cada RAID 5)
	* def::**RAID 6**: similar ao RAID 5, mas usa dois grupos de paridade, melhorando a tolerância a falhas e agregando em performance
		* **V**: + tolerância, + velocidade, suporta falha em 2 discos
		* **DV**: + custo, comparado com o RAID 5; + complexidade de implementação
		* !mínimo de 4 discos
* def::**JBOD** (Just a Bunch Of Disks): concatenação de discos em um mesmo volume, ganhando em capacidade, sem mudanças em performance ou redundância; distribuição de arquivos, e não de fragmentos


* def::**Backup**:
	* 

| Tipo     | Eficiência                        | Min. Discos | Performance | Tolerância               | Observação                            |
| :------- | :-------------------------------- | :---------- | :---------- | :----------------------- | :------------------------------------ |
| RAID 0   | 100%                              | 2           |             | 0                        |                                       |
| RAID 1   | 50% (1/N discos com espelhamento) | 2           | 2x          | 1                        | ! maior redundância, tudo é duplicado |
| RAID 1+0 | 50%                               | 4           | 2x          | até 2 (depende do strip) |                                       |
| RAID 5   | 66%                               | 3           | 2x          | 1                        |                                       |
| RAID 4   | 66% = (n-1)/n                     | 3           | 2x          | 1                        |                                       |
| RAID 5+0 | 33%                               | 6           | 2x          | até 2 (depende do strip) |                                       |
| RAID 6   | 50% = (n-2)/n                     | 4           | 2x          | 2                        |                                       |

* falta x erro x falha 
	* falta/causa (fault) (aspecto físico) - causa de uma falha (setor defeituoso num disco -> pode ou não gerar um erro)
		* prevenção de faltas > especificação rigorosa, proteção de hardware etc
		* revisões de código acham faltas
	* error - estado intermediário de instabilidade (leitura do setor defeituoso e gera valor incorreto)
	* falha (failure) - manifestação observável - afeta o usuário
		* replicação/redundância, isolamento de componente faltoso, hot swapping
		* ! tolerância a falhas não implica inexistência de faltas
		* testes acham falhas




![[Pasted image 20240520202601.png]]