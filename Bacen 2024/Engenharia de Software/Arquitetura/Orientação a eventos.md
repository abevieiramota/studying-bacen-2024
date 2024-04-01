[Fonte](https://medium.com/@seetharamugn/the-complete-guide-to-event-driven-architecture-b25226594227)

* "*The event-driven architecture enables loose coupling of applications by introducing a middleman known as an event broker. This means that applications and devices do not need to know where they are sending information or where the information they are consuming comes from.*"
* event -> change in state (ex: customer request, inventory update, sensor readings etc)
* V
	* melhor responsividade (real-time), escalabilidade;
	* decoupling - adicionar um novo serviço envolve fazer ele subscribe, não impacta outros serviços já existentes
* DV
	* more complex
* top use cases
	* integration apps
	* sharing/democratizing data across apps
	* IoT + data ingestion/analytics
	* event-enabling microservices
* **conceitos**
	* **event broker**: middleware que encaminha eventos usando padrão publish-subscribe
	* **event portal**: portal que centraliza informações sobre os eventos processados pela arquitetura, permitindo descoberta, definição/revisão de eventos, visualização de que aplicações usam que eventos etc
	* **topics**: usado para descrever eventos, com estrutura hierárquica; publish e subscribe são em tópicos
	* **event mesh**: rede de event brokers que permite a distribuição de eventos para destinos variados (rede local, cloud etc) de forma transparente (a confirmar)
	* **deferred execution**: natureza assíncrona da arquitetura, o envio de um evento não implica em resposta logo após
	* **eventual consistency**: entre o envio de evento e a confirmação de um efeito, não é possível saber se o efeito já ocorreu ou não
	* **choreography**: uma forma de coordenar diversos eventos relacionados é usar um nó central, numa abordagem de orquestração -> coreografia é outra forma, em que as partes se coordenam, sem um nó central
	* **CQRS - command query: responsibility segregation**: forma de melhorar escalabilidade de serviços, separar serviços que respondem a queries de serviços que alteram estado -> a frequência de chamadas entre eles é diferente, sendo melhor separados para escalar