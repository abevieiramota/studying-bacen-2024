Arquitetura cliente-servidor (Sommervile p113)
* Organização em ==serviços==+servidores e clientes que consomem serviços por meio de uma rede usando um protocolo de solicitação-resposta
* Exemplos de serviços: serviço de impressão, de gerenciamento de arquivo, de compilação;
* **Quando usar**: quando há banco de dados compartilhado por diversos serviços; quando a carga do sistema é variável;
* **V**: escalabilidade distribuindo servidores em rede [[Escalabilidade em sistemas web]]
* **DV**: a rede pode virar gargalo; cada serviço passa a ser um ponto de falha, sujeito a ataques

Arquitetura serverless #TODO


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