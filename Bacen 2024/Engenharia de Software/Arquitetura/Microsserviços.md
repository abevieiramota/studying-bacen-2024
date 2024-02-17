#lvl1 
#TODO SpringBoot para microsserviços

V
* menor acoplamento entre os serviços
* deploy e replicação de forma independente por serviço
* cada aplicação só usa os serviços que precisa
* as alterações são feitas apenas nos serviços que devem ser alterados, não precisa restartar o server todo, por exemplo
DV
* maior complexidade de projeto, para dividir bem os serviços, evitando redundância e muita complexidade
* maior complexidade no gerenciamento da aplicação
* replicação de código de infraestrutura

* [Pattern: Microservice architecture](https://microservices.io/patterns/microservices.html)
	* contexto: aplicação com diversos subdomínios e diversos times de desenvolvimento
	* atributos que estimulam separação (benefícios de microservice)
		* simplificação de componentes (quanto menor/mais focado, mais simples)
		* autonomia de times
		* fast deploy
		* multiple stacks
	* atributos que estimulam unificação (drawbacks)
		* interações mais simples - não ter que lidar com complexidade de sistemas distribuídos
		* interações mais eficientes - sem custo de rede e outros inerentes a distribuição
		* ACID over BASE - operações usando transações ACID são mais simples de implementar
	* microservice - arquitetura como conjunto de componentes { independently deployable, loosely coupled, owned by a team, own code repository, own deploy pipeline } + API Gateway
	* padrão de um banco por serviço
		* mantém os dados gerenciados por cada serviço como privados e acessíveis apenas via sua API
		* transações dos serviços envolvem apenas seu próprio banco
		* não necessariamente um servidor por serviço - pode ser conjunto de tabelas por serviço, schema por serviço, database por serviço
		* benefícios { menor acoplamento de serviços (mudanças num banco não impacta outros serviços), liberdade dos serviços de usar bancos diferentes }
		* drawbacks { transações que envolvam múltiplos serviços mais complexa, join mais complexo para dados gerenciados por mais de um serviço, manutenção de diversos sgbds }
	* padrões de colaboração de serviços
		* Saga - sequência de transações locais, vão publicando resultado como mensagem/evento e há monitoramento para compensar transações anteriores, caso uma falhe
			* "*O padrão de design saga é uma maneira de gerenciar a consistência de dados entre microsserviços em cenários de transação distribuída.  Uma saga é uma sequência de transações que atualiza cada serviço e publica uma mensagem ou evento para disparar a próxima etapa de transação. Se uma etapa falhar, a saga executará transações compensatórias que contrariam as transações anteriores.*"
		* API Composition - um serviço consulta os outros e joina os dados
		* CQRS (Command Query Responsibility Segregation) - query que precisa de dados de múltiplos serviços; manter view read-only que é mantida usando eventos submetidos pelos serviços que mantêm os dados (! cuidado, CQRS é um padrão com outra definição, o autor desse link confundiu algo)
* necessário { autorização a nível de serviço, helth check/metrics endpoints }

