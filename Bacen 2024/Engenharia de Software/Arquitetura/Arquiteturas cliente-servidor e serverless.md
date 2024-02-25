#lvl1

**Arquitetura cliente-servidor** (Sommervile p113)
* Organização em ==serviços==+servidores e clientes que consomem serviços por meio de uma rede usando um protocolo de solicitação-resposta
* Exemplos de serviços: serviço de impressão, de gerenciamento de arquivo, de compilação;
* **Quando usar**: quando há banco de dados compartilhado por diversos serviços; quando a carga do sistema é variável;
* **V**: escalabilidade distribuindo servidores em rede [[Escalabilidade em sistemas web]]
* **DV**: a rede pode virar gargalo; cada serviço passa a ser um ponto de falha, sujeito a ataques

[[Web services]]

**Arquitetura serverless** [Datadog](https://www.datadoghq.com/knowledge-center/serverless-architecture/)
* "*Serverless architecture is an approach to software design that allows developers to build and run services without having to manage the underlying infrastructure. Developers can write and deploy code, while a cloud provider provisions servers to run their applications, databases, and storage systems at any scale.*"
* terceiriza o trabalho de manutenção/gerenciamento de servidores, deixando o desenvolvimento focado no funcional
* FaaS - Function as a Service - uma das arquiteturas mais populares
	* aplicação desenvolvida como conjunto de funções discretas, que executam tarefas disparadas por eventos como chegada de e-mail ou requisição HTTP
	* providers: AWS Lambda, Google Cloud Functions (GCF) e Azure Functions
* conceitos fundamentais
	* invocation - execução individual de uma função
	* duration - tempo que leva para função executar
	* cold start - latência da primeira execução de uma função, ou quando ela passa certo tempo sem ser executada
	* concurrency limit - limite de execuções concorrentes (limitado pelo provider, throttled se exceder o limite)
	* timeout - tempo limite de execução de função até o provider derrubar ela
* container architecture x serverless architecture
	* container, desenvolvedor é responsável por atualizar o container, além de configurar esquema de escalabilidade, como com kubernetes
* ideal para
	* aplicações baseadas em triggers, como processamento de pagamento
	* short-lived tasks
	* workloads com tráfico imprevisível e infrequente
	* async processing
* V: custo { só paga pelo que usar de processamento }, escalabilidade, produtividade (foco no dev) 
* DV: loss of control (se ocorrer algum problema na infra/server, só o provider consegue tratar), security (um servidor pode executar aplicações de múltiplos clientes, havendo risco de acesso indevido), performance (cold start), testing (dificuldade com testes de integração - #n_entendi), vendor lock-in


**Sistemas distribuídos** (Sommervile p. 333)
"*Você sabe que tem um sistema distribuído quando a parada de um sistema que você desconhece impede você de trabalhar*"
* **Vantagens**:
	* compartilhamento de recursos
	* abertura - normalmente são implementados usando protocolos-padrão, facilitando integração de hardware/software
	* concorrência
	* escalabilidade
	* tolerância a falhas/alta disponibilidade
* **Desvantagens**:
	* maior complexidade > dificuldade de seguir um modelo de controle top-down, dada a independência dos componentes + adição da rede
	* dificuldade de compreender propriedades emergentes, como desempenho
* **Pontos importantes de design**:
	* se o sistema deve aparecer como único para o usuário
	* uso de protocolos-padrão
	* escalabilidade
	* qualidade de serviço
	* gerenciamento de falhas