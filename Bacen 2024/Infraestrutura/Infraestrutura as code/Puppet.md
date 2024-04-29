* [User guide](https://www.puppet.com/docs/pe/2023.6/pe_user_guide.html)
	* **Arquitetura agent-server** -> usa um server, que armazena códigos definindo o estado desejado da infra, e agents, que traduzem e executam os códigos em comandos #anki não é agentless
		* comunicação via HTTPS usando certificados SSL -> Puppet já vem com um built-in certificate authority para gerenciar certificados
		* isso não quer dizer que não há nós agentless -> nós de network, por exemplo, em switches etc podem ser agentless!
	* **Por que usar**
		* consistência -> com gerenciamento de configuração, é possível fazer assumptions mais seguras sobre o estado da infra (ex: qual versão do Apache está rodando)
		* automação -> mais importante, quanto maior o tamanho da infra
	* **Key concepts**
		* [[Infraestrutura as code]]
		* Idempotência -> garantia de que aplicação múltiplas vezes de um código de garantia de estado irá gerar o mesmo resultado -> permite um uso contínuo do Puppet
		* Agile methodology -> incremental + reuse
		* Git and version control -> versionar artefatos Puppet
		* resource -> aspecto do sistema (ex: pacote)
		* class -> grupo de resources que fazem sentido juntos (ex: serviços necessários para executar determinada aplicação)
	* **Puppet Code** -> DSL para especificação do estado de infraestrutura desejado
		* gira em torno de declaração de resources que compõem o estado desejado de um nó
		* permite lógica condicional
		* extensão .pp
		* encoding UTF-8 obrigatório
		* [exemplo](https://www.puppet.com/docs/puppet/7/intro_puppet_language_and_code#lang_manifests-manifest-example)
	* **The Puppet platform**
		* puppetserver
			* pode executar um agent para configurar a si próprio
			* JVM-based app, usando JRuby
		* puppetdb
			* usa PostgreSQL por padrão
		* puppet-agent -> { Facter, Hiera }; daemon
			* Facter -> inventory tool, recupera fatos sobre os nós agentes, como { hostname, IP address, SO etc }
				* os fatos coletados são enviados ao servidor como arquivos *manifest* extensão .pp, que compila em um *catalog* em JSON
				* fact -> unidade de informação sobre um nó
			* Hiera -> #n_entendi 
			* modules -> responsável por gerenciar uma task específica; contém código e data (configuração)
	* fornece um console para gerenciar a instalação Puppet
	* por padrão, a cada 30 min os agentes enviam fatos ao servidor, que retorna dados do catálogo -> o agente aplica operações para garantir que o nó está no estado esperado e depois envia logs para o servidor
	* pode-se falar em nó *serverless*, quando ele independe do servidor Puppet


![[Pasted image 20240428095005.png]]
![[Pasted image 20240428100806.png]]
![[Pasted image 20240428144848.png]]