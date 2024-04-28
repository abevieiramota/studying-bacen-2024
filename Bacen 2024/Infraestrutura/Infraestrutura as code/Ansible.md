* [Homepage](https://www.ansible.com/)
	* "*Ansible is an open source IT automation engine that automates 
		* [[Infraestrutura as code#^provisioning|provisioning]], 
		* configuration management, 
		* application deployment, 
		* orchestration, 
		* and many other IT processes. 
	* *It is free to use, and* 
	* *the project benefits from the experience and intelligence of its thousands of contributors.*"
* [Basics](https://www.ansible.com/how-ansible-works/)
	* Escrito em Python
	* Usa OpenSSH para transporte
	* Usa YAML nos arquivos de configuração
	* Apache License 2.0
	* Tem duas versões
		* Community Ansible -> suporte via command line para diversos SOs, como RHEL, Debian, Ubunto, Windows etc
		* Red Hat Ansible Automation Platform -> Ansible + enterprise features
			* integra diversos projetos relacionados; ex { run on-premise, WebUI etc }
	* Define dois tipos de nós { control, managed }, com o nó control executando comandos para afetar nós managed
	* São utilizados pequenos programas, Ansible modules, que são enviados aos nós managed, executados e depois removidos
	* É **agentless** -> o que diminui custos de manutenção da infra, por não ser necessário instalar programas em outras máquinas
	* Garante idempotência -> se o sistema está no estado declarado no playbook, múltiplas execuções não irão produzir efeitos adversos
	* São necessários um inventório (que managed nodes devem ser automatizados) e credenciais (para conectar aos managed nodes)
		* Pode usar sistemas de autenticação como Kerberos, LDAP etc
		* usernames e passwords podem ser criptografados com Ansible Vault
		* O arquivo de inventório pode agrupar as máquinas em grupos - exemplo de arquivo de inventório
			* ![[Pasted image 20240427201810.png]]
		* É possível associar variáveis aos hosts, tanto declarando no próprio arquivo de inventório, quanto em arquivos à parte, nos subdiretórios group_vars/ ou host_vars/
		* Além de declarar em arquivo, dados de inventório podem ser obtidos de sistemas de gerenciamento de inventório
	* Ansible Playbooks -> linguagem de automação -> no playbook é declarado o estado em que o sistema deve estar, daí o Ansible se encarrega de garantir isso. Ex:
		* ![[Pasted image 20240427202045.png]]
		* ! atentar para o \-\-\- no início e (deveria ter) ... no fim (é padrão do YAML)
		* é possível configurar detalhes como { políticas de load balancer/monitoring, prompt de variável, lógica baseada no estado das máquinas etc }
		* "*A playbook is composed of one or more ‘plays’ in an ordered list. The terms ‘playbook’ and ‘play’ are sports analogies. Each play executes part of the overall goal of the playbook, running one or more tasks. Each task calls an Ansible module.*" [link](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html)
		* a execução é de cima para baixo
	* Vantagens
		* elimina repetições/simplifica workflows
		* gerenciamento de configurações
		* deploy contínuo
		* permite zero-downtime rolling updates
* playbook, ficam em /ansible/playbooks/ -> script com tasks
	* já tem algumas tasks padronizadas, como 'install mysql', que já funciona para máquinas com configurações diversas
* arquivo hosts -> especifica as máquinas, com usuários/senha para conexão SSH
* ansible-pull permite inverter o processo, fazendo com que managed nodes, verifiquem em repositório se há playbook a ser executado
* Ansible Tower -> interface web, desenvolvida pela Red Hat
* **Comandos**
	* ansible -m ping 'nome da máquina' -> conecta na máquina, descobre fatos e pinga
		* -vvv -> modo verboso
	* [ansible-playbook](https://docs.ansible.com/ansible/latest/cli/ansible-playbook.html#ansible-playbook) arquivo_do_playbook.yaml
		* -i inventory.ini -> especifica o arquivo de inventório
		* -f \<n forks\> -> especifica a quantidade de processos paralelos a usar (default = 5)
	* ansible all -m ping -> pinga todos servidores
* [Ecosystem](https://www.ansible.com/ecosystem/)
	* Ansible Development Tools (ADT)
	* Ansible AWX -> web-based interface, REST API
	* Ansible collections -> repositório de soluções com Ansible
	* Ansible Core -> language and runtime that powers automation
	* Ansible Creator -> scaffolding conteúdo Ansible
	* Event-Driven Ansible Server
	* Galaxy -> compartilhamento de soluções ! not so sure
	* Ansible Lint -> qualidade do código escrito para Ansible
	* Molecule -> criação segura de Ansible roles
	* Ansible Navigator -> command-line tool for creating reviewing, and troubleshooting Ansible content
	* Ansible Pytest
	* Ansible Rulebook -> escuta de eventos e reação
	* Ansible SDK
	* Tox Ansible -> test