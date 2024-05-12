* def::**Sistemas Distribuídos**: sistema cujos componentes estão localizados em computadores interligados em rede e se comunicam e coordenam suas ações por meio de mensagens, disso decorrendo três características: concorrência de componentes, falta de um relógio global e falhas, de forma independente, de componentes (Sommervile)
	* **Concorrência de componentes**: os componentes funcionam de forma independente e consomem recursos compartilhados
	* **Falta de um relógio global**: a coordenação por troca de mensagens, muita das vezes, exige uma noção compartilhada do tempo em que as ações ocorrem; e há desafios com satisfazer essa necessidade
	* **Falhas, de forma independente, de componentes**: falhas na rede isolam componentes, que podem continuar a funcionar; componentes podem falhar individualmente, enquanto os demais continuam a funcionar; isso traz desafios para o sistema como um todo, cujo funcionamento é função do funcionamento de seus componentes
* "*Você sabe que tem um sistema distribuído quando a parada de um sistema que você desconhece impede você de trabalhar*"
* **V**:
	* compartilhamento de recursos
	* abertura - normalmente são implementados usando protocolos-padrão, facilitando integração de hardware/software
	* concorrência
	* escalabilidade
	* tolerância a falhas/alta disponibilidade
* **DV**:
	* maior complexidade > dificuldade de seguir um modelo de controle top-down, dada a independência dos componentes + adição da rede
	* dificuldade de compreender propriedades emergentes, como desempenho
* **Pontos importantes de design**:
	* se o sistema deve aparecer como único para o usuário
	* uso de protocolos-padrão
	* qualidade de serviço
	* gerenciamento de falhas
* **Arquiteturas**:
	* mestre-escravo (orquestrador e operadores): comum em sistemas de tempo real
	* [[Arquiteturas cliente-servidor e serverless]]
	* distribuída de componentes
	* ponto-a-ponto
	* next_step::**arquitetura hexagonal**: divisão do sistema em classes de domínio e classes de infraestrutura
		* comunicação entre classes dos dois grupos mediada por adaptadores
		* portas { de entrada - classe de fora chamando classe de domínio, de saída - classe de domínio precisa chamar método de classe externa }
	* **arquitetura multi-tenancy**: uma aplicação centralizada que atende a vários clientes
		* **single-tenancy**: total isolamento dos dados e aplicação { cada usuário tem sua aplicação, total isolamento, mitiga riscos de vazamentos }
		* **multi-tenancy**: todos usuários acessam a mesma aplicação, que define que dados cada usuário pode acessar { otimização de recursos computacionais, maior complexidade de segurança, concorrência por recursos }; segregação lógica
		* **híbrido**: todos usuários acessam a mesma aplicação, mas cada um usa um banco de dados separado
* **Conceitos**:
	* def::**Middleware**: fornece serviços de conversão de tipos de dados, interface para diversas linguagens, interoperabilidade