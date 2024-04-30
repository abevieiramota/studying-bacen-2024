* **Características**
	* [[SO#^so-multitarefa|multitarefa]] 
	* [[SO#^so-multiusuario|multiusuário]]
	* **Kernel** 
		* monolítico -> é um componente só que faz comunicação com hardware; se falhar, falha tudo
		* usa módulos, carregados apenas sob demanda, para diminuir o consumo padrão de memória do kernel; ficam em /lib/modules/versão_do_kernel/
	* permite uso de servidores de janelas/ambientes gráficos -> os mais populares { **Gnome**, **KDE**, Cinnamon, **MATE**, **XFCE**, Pantheon, Deepin etc }
* **Distribuições**
	* #TODO adicionar Ubuntu, Debian, Fedora, Arch etc
	* RHEL - Red Hat Enterprise Linux: distribuído por modelo de as$inatura, estável/seguro, suporte de longo prazo, empresarial;
	* CentOS: código aberto baseado no RHEL, gratuita, bastante usada em servidores, suporte de longo prazo, grande comunidade;
	* Oracle Linux: código aberto baseado no RHEL, KUE - Kernel Unbreakable Enterprise, versão personalizada do kernel Linux com melhorias de desempenho, segurança e suporte a tecnologias Oracle, distribuído por modelo de as$inatura;
* **Comandos**
	* uname -a -> informações sobre o kernel
	* systemctl -> gerenciador serviços com o systemd
		* systemctl enable/disable httpd.service -> habilita/desabilita o serviço httpd.service no boot
		* systemctl is-active httpd.service -> verifica se o serviço httpd.service está ativo
		* systemctl start/restart/stop/reload/status httpd.service
	* who -> usuários logados 
	* ./script.sh -> executa script ! caso o script não esteja no path, é preciso prefixar com ./ para que ele seja executado
	* awk -> utilitário para manipulação de texto -> faz uso de linguagem interpretada própria
		* awk -F: '{print $1 " => " $7}' /etc/passwd
			* imprime a lista de usuários com seus shell padrão, no formato "abevieiramota => /bin/bash"; o comando entre aspas simples é executado uma vez para cada linha em /etc/passwd
			* -F: -> indica que o separador de campos é dois-pontos (splita por ele), que serão identificados por $1 a $n_campos
		* awk -f arquivo_com_comando
	* su -> **s**ubstitute **u**ser, serve para trocar de usuário (não necessariamente para o root, apesar de geralmente ser usado para isso)
		* su -> sem argumentos, solicita a senha para alternar para o root, registrando em log a operação
		* su \<nome do usuário\> -> alterna para usuário
	* sudo -> permite que usuários executem comandos com privilégio de outro usuário (não necessariamente do root, apesar de geralmente ser usado para isso)
		* verifica o arquivo /etc/sudoers, que armazena, para hosts, que usuários e comandos estão habilitados
		* a senha solicitada é a do próprio usuário!
		* sudo apt-get install abc -> como não foi especificado usuário, irá usar privilégios de root
		* sudo -u abe ./script.sh
		* sudo -g prof ./script.sh -> seta o grupo para prof na execução
		* pode ser configurado para deixar de exigir a senha por um tempo (ex: 1 min) após ela ter sido fornecida
	* mkdir, cd, pwd (print working directory), rmdir, touch, rm, echo
	* > -> redireciona criando arquivo ou substituindo
	* >> -> redireciona appendando
	* | -> pipe
	* ls -a (all, incluindo ocultos); ls -l (lista longa, detalhada); ls -s (imprime o **s**ize dos arquivos) [Questão](https://www.qconcursos.com/questoes-de-concursos/questoes?q=Q2365594)
	* cat -> concatena arquivos (ex: cat arq1 arq2)
		* cat arq1 > arq2 -> cria/sobrescreve arq2 com conteúdo de arq1
		* cat arq1 >> arq2 -> appenda em arq2 o conteúdo de arq1
	* zcat -> permite visualizar conteúdo do arquivo compactado sem descompactá-lo
	* tail -> mostra as últimas linhas do arquivo
		* tail -n 20 teste.txt -> mostra as últimas 20 linhas
		* tail -f -> vai atualizando com as últimas alterações no fim do arquivo (**f**ollow)
	* find
		* find . -> todos arquivos no diretório, incluindo em subdiretórios
		* find ./teste -maxdepth 1 -name \*.php -> procura arquivos terminados em .php no diretório apenas (depth 1)
		* find ./teste -name 'comando*' ! -name '\*.php' -> ! ou -not procura começando com 'comando' e não terminando com '.php'
		* find -name '\*.jpg' -o -name '\*.txt' -> -o ou -or para definir múltiplos critérios com OR
		* find . -type f -> busca apenas arquivos (**f**ile)
		* find . -type d -> busca apenas **d**iretórios
		* find . -type f -perm 0740 -> busca arquivos com as permissões
		* find . -user abe -> arquivos do usuário
		* find . -group abe -> arquivos do grupo
		* find -mtime 5 -> modificado há até 5 dias
		* find -atime 5 -> acessado há até 5 dias
		* find -size +10M -> arquivos maiores que 10MB
	* grep -> mostra linhas de arquivo que tem match com padrão; comum usar com o cat, ex: cat arquivo.txt | grep string_interessante
	* more -> apresenta conteúdo do arquivo uma tela por vez, pulando com espaço
	* df -> mostra espaço disponível em disco (disk free)
		* -T -> informa o tipo de sistema de arquivos do SO
	* free -> mostra quantidade de memória utilizada e livre
	* which -> mostra path de comando, ex: which cat -> /bin/cat
	* watch -> monitorar saída de comando
		* watch -n 1 top -> apresenta na tela, a cada 1 segundo, o resultado do top
	* tee -> grava conteúdo em arquivo E apresenta no terminal
	* hostname -> apresenta o nome da máquina
	* wc -w -c -> conta as palavras e caracteres do input
	* mv -> renomeia arquivo (possivelmente movendo)
	* ln -> criação de links simbólicos
	* xargs \<comando\> -> executa o comando para cada linha recebida de input
		* cat lista_supermercado.txt | xargs echo
* **Processos**
	* execução em foreground (com interação direta com usuário) e background (sem interação direta com usuário)
		* crtl + z; bg -> suspende o processo e depois envia para background
			* para já executar em background, adicionar & após o comando; ex: teste.sh &
			* processos que normalmente são executados em background são os daemons, cujos nomes terminam normalmente com 'd'
		* jobs -> lista processos em background, indicando o número associado
		* fg %\<número do job\> -> move o processo para foreground
			* caso seja executado sem parâmetro, devolve para foreground o último processo enviado para background (funciona como pilha)
			* possível também passar uma string contendo o início do comando a ser retornado para fg (ex: fg %ping)
* **Agendamento de tarefas** -> ferramenta mais conhecida é o [[Cron]]
* **Sistemas de arquivos** -> responsável pelo gerenciamento dos arquivos (estrutura, nome, acesso, permissões, usos etc)
	* Linux lida com sistemas de arquivos típicos do Windows, como FAT32 e NTFS
	* EXT (EXtended File System)
		* bloco -> menor unidade de alocação, com tamanho definido, durante a formatação, como um dos seguintes valores { 1024, 2048, 4096, 64KiB } 
		* apenas a partir do EXT**3** que foi implantado recurso de journaling, similar ao log do Postgres para garantir durabilidade
			* possui três modos de operação:
				* ordered -> atualiza o journal ao fim de cada operação, exigindo duas operações, a escrita no arquivo e no journal; é o default
				* writeback -> mantém apenas informações de metadados
				* journal -> mais segur, mas mais lento, armazena cópia de segurança dos arquivos modificados não gravados em disco
		* EXT4 permite endereçamento de 48 bits, permitindo alto volume de dados armazenados, bem como sem limitação para o tamanho do arquivo individual
			* para um block size de 4KiB, o max file size é de 16TiB
	* NFS (Network File System) - protocolo de sistemas de arquivos distribuídos, para acesso remoto de forma transparente
	* XFS -> default no RHEL
	* GFS2 (Global File System 2) -> permite permissão de escrita compartilhada (shared storage)
* **LVM** (Logical Volume Manager)
	* mantém uma camada lógica de gerenciamento de partições -> é possível variar os discos físicos, mantendo o particionamento, de forma transparente para o SO
		* ex: adicionar mais um disco, estendendo o espaço de uma partição (lógica)
		* trata o problema de definir partições e precisar posteriormente remanejar espaço (que impõe riscos e custos)
		* facilita também a realização de backups
	* normalmente já vem compilado nas distribuições, exigindo apenas que seja ativado
* **Estrutura de diretórios** -> as distribuições Linux tendem a seguir uma mesma estrutura
	* /etc -> **E**nvironment **T**ables and **C**ontrols -> arquivos de configuração
		* /etc/group -> arquivo que define grupos de usuários
		* anki::/etc/passwd -> define quem pode acessar o sistema e permissões (! cuidado, não é ele quem armazena senhas, apesar do nome remeter a password)
			* ![[Pasted image 20240418200719.png]]
		* /etc/shadow -> armazena senhas de usuários, criptografadas, e informações de data de expiração/validade das contas
		* /etc/syslog.conf -> controla a saída de log do daemon syslogd
		* /etc/profile -> contém comandos executados para todos usuários no login; só o root pode modificar
		* /etc/network/interfaces -> usado para ativar/desativar interfaces de rede
		* anki::/etc/resolv.conf -> configura resoluções de host via [[Infraestrutura/Redes/DNS|DNS]]
			* ![[Pasted image 20240419145531.png]]
			* domain -> nome do domínio local
			* search -> lista de pesquisa para procura de nomes curtos (no exemplo, a busca por um nome como 'gitlab' vai gerar uma busca por 'gitlab.ti.teste.com.br')
			* nameserver -> especifica o IP de um serivdor de nomes que o resolvedor deve pesquisar
		* anki::/etc/exports -> configura diretórios exportados com [[NFS]]
		* /etc/ldap.conf -> configuração para execução de clients [[LDAP]]
		* /etc/ssh/sshd_config -> configuração de SSH
		* /etc/hosts -> mapeamento de nome de domínio e IP, dispensando consulta a servidores DNS
			* formato: \<ip\> \<nome do host\> \<alias\>
			* 127.0.0.1 localhost maquina_local
	* /usr -> aplicativos e bibliotecas do sistema não necessários para o boot (associar a Unix System Resources)
		* /usr/bin -> executáveis de programas
		* /usr/lib -> bibliotecas e arquivos compartilhados
		* /usr/src -> código-fonte de programas
		* /usr/doc -> documentação em geral
	* /home -> arquivos dos usuários
	* /root -> diretório home do root (! não é o mesmo que o diretório raiz /)
	* /var -> sites hospedados, bases de dados
		* /var/log -> logs de serviços
		* /var/www -> sites hospedados
	* /boot -> imagem do kernel e o initrd (initial ram disk), carregados no boot
	* /bin -> programas dos comandos básicos, como 'cd', 'ls' etc
	* /lib/modules/versão_do_kernel -> módulos do kernel e bibliotecas básicas
	* /opt -> aplicativos adicionais, não essenciais ao sistema ou não oficiais!
	* /proc -> informações de depuração do kernel
	* /tmp -> arquivos temporários
	* /dev -> armazena arquivos de dispositivos (! DEVices)
* **Memória virtual**: usa-se tanto partição swap, como é possível também criar um arquivo de memória swap
* **Gerenciadores de pacotes**
	* **Debian based**
		* APT - não permite instalação via site (caso queira dessa forma, é preciso usar o DPKG)
			* sudo apt-get update ~ sudo apt update -> atualiza os repositórios de software
			* sudo apt-get/apt upgrade -> atualiza pacotes instalados
			* sudo apt-get dist-upgrade ~ sudo apt full-upgrade -> atualiza pacotes instalados, SO, e remove dependências não utilizadas
			* sudo apt-get/apt update && sudo apt-get/apt upgrade -> atualiza repositórios e pacotes já instalados
			* sudo apt-get/apt install nome_do_pacote
			* sudo apt-get/apt remove nome_do_pacote
				* sudo apt-get/apt autoremove -> remove dependências desnecessárias
			* sudo apt-cache/apt search termo_pesquisa
		* DPKG (Debian Package) - instala pacotes .deb; 
			* comando dpkg \<opção\> nome_pacote -> opções
				* -i -> instala
				* -r -> desinstala (mantém arquivos de configuração)
				* -P -> desinstala e remove arquivos de configuração
				* -l -> lista pacotes instalados
				* -p -> informações sobre pacote instalado
				* -s -> status de pacote
				* -L -> lista arquivos que fazem parte do pacote
				* --help -> ajuda
			* comando dpkg-reconfigure permite reconfigurar pacotes
	* Red Hat based
		* RPM - criado pela Red Hat para instalar pacotes .rpm, utilizado em distribuições como Red Hat Enterprise Linux (RHEL), Fedora, Mandriva etc
			* comando rpm \<opção\> pacote
				* -i -> instalação
				* -U -> atualização de pacote
				* -e -> desinstala (! lembrar de **e**xclude)
				* --help
				* -q -> verifica se pacote já está instalado
		* YUM - Yellowdog Updater Modified - similar ao APT para .rpm; diferente do APT, permite instalar por URL
			* sudo yum update -> atualiza repositórios
			* sudo yum install pacote 
			* sudo yum remove pacote
			* sudo yum search termo_pesquisa
* [[Shell Script|Unix Shell]] -> interpretador e linguagem de programação
* [[Gerenciamento de processos]]
* [[Montagem de volumes]]
* **Usuários, grupos, permissões**
	* root -> administrador; diretório home = /root
	* cada arquivo/diretório tem três níveis de permissão de acesso { dono do arquivo (U), grupo proprietário (G), demais usuários (O) }
	* as permissões são { read, write, e**x**ecute }; para visualizar, usar ls -l
	* ![[Pasted image 20240419201545.png]]
	* permissões especiais
		* setuid -> executa com o usuário dono do arquivo (forma de permitir executar com privilégio do dono sem precisar fornecer credenciais dele)
		* setgid -> executa com o grupo do dono do arquivo (/\\)
		* sticky bit -> indica se os arquivos no diretório só podem ser modificados por seus proprietários
	* modificando permissões
		* chmod u=rwx, g=rx, o=x arquivo
		* chmod 0751 arquivo
			* 0 = 000 -> desabilitadas todas as permissões especiais
			* 7 -> 111 -> rwx para usuário
			* 5 -> 101 -> r\_x para grupo
			* 1 -> 001 -> \_\_x para outros
		* chmod 1751 -> similar ao comando acima, mas com o sticky bit ativado (001)
	* modificando dono/grupo -> comando chown (! cuidado, apesar de significar change owner, ele permite alterar também o grupo)
		* chown -R abe /teste -> altera **r**ecursivamente o dono da pasta teste e arquivos/pastas abaixo dela
		* chown abe:player /teste -> altera ao mesmo tempo o dono e o grupo
		* o comando chgrp permite alterar apenas o grupo -> sintaxe igual à do primeiro exemplo do chown
	* superusuário
		* pode tudo, toda operação válida em arquivos/processos e algumas syscalls são exclusivas dele. Exemplos de operações restritas:
			* modificar o diretório raiz
			* criar arquivos de dispositivo
			* configurar o relógio
			* aumentar limites de uso de recursos e prioridades de processos (qualquer processo - dono do processo também pode alterar ele)
			* definir o nome de host
			* configurar interfaces de rede
			* abrir portas privilegiadas (< 1024)
			* desligar o sistema
		* tem UID = 0 e GID = 0 e é possível alterar seu nome
		* /root -> diretório home
		* /sbin -> diretório com os binários utilizados pelo **s**uperusuário
		* no uso do shell, é possível identificar o tipo de usuário de acordo com o prompt #anki 
			* $ -> usuário comum
			* \# -> superusuário