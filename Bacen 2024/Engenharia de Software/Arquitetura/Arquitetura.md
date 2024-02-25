 Conjunto de 
  ==estruturas necessárias para raciocinar sobre o sistema==, 
que inclui 
  ==elementos de software,== 
  ==relacionamentos entre eles e== 
  ==propriedades dos dois==
  
 **Padrões de arquitetura**
* [[Arquitetura em camadas]]
* [[Arquitetura baseada em Serviços]]
* [[Orientação a eventos]]
* [[Arquiteturas cliente-servidor e serverless]]
* [[Escalabilidade em sistemas web]]
* [[Cache]]
* [[Tolerância a falhas]]
* [[Distributed Ledger Technology (DLT)]]


**Fonte**: Sommervile

* "O desenvolvimento incremental de arquiteturas geralmente não é bem-sucedido" (p. 103), comparando com dev incremental de componentes, em metodologias ágeis;
* A arquitetura tem maior impacto em requisitos não-funcionais (ex: desempenho, segurança, disponibilidade, manutenção etc)
* Vantagens de projetar e documentar arquitetura
	* **comunicação com stakeholders** - arquitetura pode ser usada para falar do sistema;
	* **analisar o sistema**, tomando decisões críticas, com impacto em desempenho, confiabilidade, manutenibilidade etc;
	* **reuso**, permite identificar sistemas semelhantes e reusar solução
		* a exemplo de fábrica de software, que reusa arquiteturas
	* **diminuição de complexidade** - ao focar em abstrações-chave, ignorando detalhes não importantes em tempo de design
* Recomendação de Krutchen (1995) de visões fundamentais
	* Lógica - objetos/classes/entidades, que possam ser relacionadas com os requisitos
	* Processo - como o sistema funciona em runtime, com processos
	* Desenvolvimento - componentes de código
	* Física - hardware
* sistema distribuído
	* procedural - A chama B, necessária disponibilidade dos dois no momento da comunicação
	* por mensagem - A envia mensagem M com destinatário B, há um meio de campo, maior tolerância a indisponibilidade, A não precisa saber onde está B
	* middleware - fornece serviços de conversão de tipos de dados, interface para diversas linguagens, interoperabilidade
* arquiteturas de sistemas distribuídos
	* mestre-escravo (orquestrador e operadores) - comum em sistemas de tempo real
	* [[Arquiteturas cliente-servidor e serverless]]
	* distribuída de componentes
	* ponto-a-ponto

* **arquitetura hexagonal**: divisão do sistema em classes de domínio e classes de infraestrutura
	* comunicação entre classes dos dois grupos mediada por adaptadores
	* portas { de entrada - classe de fora chamando classe de domínio, de saída - classe de domínio precisa chamar método de classe externa }
* **arquitetura multi-tenancy**: uma aplicação centralizada que atende a vários clientes
	* **single-tenancy**: total isolamento dos dados e aplicação { cada usuário tem sua aplicação, total isolamento, mitiga riscos de vazamentos }
	* **multi-tenancy**: todos usuários acessam a mesma aplicação, que define que dados cada usuário pode acessar { otimização de recursos computacionais, maior complexidade de segurança, concorrência por recursos }; segregação lógica
	* **híbrido**: todos usuários acessam a mesma aplicação, mas cada um usa um banco de dados separado