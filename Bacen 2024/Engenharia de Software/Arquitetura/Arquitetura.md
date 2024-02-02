 Padrões de arquitetura
	* [[Arquitetura em camadas]]
	* [[Arquitetura baseada em serviços]]
	* [[Microsserviços]] (orquestração de serviços e API gateway)
	* [[Orientação a eventos]]
	* [[Arquiteturas cliente-servidor e serverless]]

#TODO saber onde cada padrão pode ser usado, vantagens e desvantagens

Conjunto de 
  ==estruturas necessárias para raciocinar sobre o sistema==, 
que inclui 
  ==elementos de software,== 
  ==relacionamentos entre eles e== 
  ==propriedades dos dois==


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
* aplicação de processamento de transação - leitura e alteração de dados por diversos usuários
* sistema distribuído
	* procedural - A chama B, necessária disponibilidade dos dois no momento da comunicação
	* por mensagem - A envia mensagem M com destinatário B, há um meio de campo, maior tolerância a indisponibilidade, A não precisa saber onde está B
	* middleware - fornece serviços de conversão de tipos de dados, interface para diversas linguagens, interoperabilidade
* arquiteturas de sistemas distribuídos
	* mestre-escravo (orquestrador e operadores) - comum em sistemas de tempo real
	* [[Arquiteturas cliente-servidor e serverless]]
	* distribuída de componentes
	* ponto-a-ponto