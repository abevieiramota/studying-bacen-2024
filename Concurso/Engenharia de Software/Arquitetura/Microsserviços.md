* def::**Microsserviço**: arquitetura como conjunto de componentes { independently deployable, loosely coupled, owned by a team, own code repository, own deploy pipeline } + API Gateway
* **V**:
	* menor acoplamento entre os serviços
	* deploy e replicação de forma independente por serviço
	* cada aplicação só usa os serviços que precisa
	* as alterações são feitas apenas nos serviços que devem ser alterados, não precisa restartar o server todo, por exemplo
* **DV**:
	* maior complexidade de projeto, para dividir bem os serviços, evitando redundância e muita complexidade
	* maior complexidade no gerenciamento da aplicação
	* replicação de código de infraestrutura
* **Contexto**: aplicação com diversos subdomínios e diversos times de desenvolvimento
	* **Atributos que estimulam separação**: (benefícios de microservice)
		* simplificação de componentes (quanto menor/mais focado, mais simples)
		* autonomia de times
		* fast deploy
		* multiple stacks
	* **Atributos que estimulam unificação**: (drawbacks)
		* interações mais simples: não ter que lidar com complexidade de sistemas distribuídos
		* interações mais eficientes: sem custo de rede e outros inerentes a distribuição
		* ACID over BASE: operações usando transações ACID são mais simples de implementar
	* **Padrão de um banco por serviço**:
		* mantém os dados gerenciados por cada serviço como privados e acessíveis apenas via sua API -> encapsulamento dos dados pelos serviços
		* transações dos serviços envolvem apenas seu próprio banco
		* não necessariamente um servidor por serviço - pode ser conjunto de tabelas por serviço, schema por serviço, database por serviço
		* **V**: { menor acoplamento de serviços (mudanças num banco não impacta outros serviços), liberdade dos serviços de usar bancos diferentes }
		* **DV**: { transações que envolvam múltiplos serviços mais complexa, join mais complexo para dados gerenciados por mais de um serviço, manutenção de diversos sgbds }
	* **Padrões de colaboração de serviços**:
		* def::**Saga**: sequência de transações locais, vão publicando resultado como mensagem/evento e há monitoramento para compensar transações anteriores, caso uma falhe
			* "*O padrão de design Saga é uma maneira de gerenciar a consistência de dados entre microsserviços em cenários de transação distribuída.  Uma saga é uma sequência de transações que atualiza cada serviço e publica uma mensagem ou evento para disparar a próxima etapa de transação. Se uma etapa falhar, a saga executará transações compensatórias que contrariam as transações anteriores.*"
		* def::**API Composition**: utiliza um API composer/aggregator, responsável por invocar serviços individuais e combinar os resultados em memória e produzir uma resposta
* **Capacidades importantes**:
	* autorização a nível de serviço
	* helth check
	* metrics endpoints
* **Fontes**:
	* [Pattern: Microservice architecture](https://microservices.io/patterns/microservices.html)

