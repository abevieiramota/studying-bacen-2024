* def::**SOA** (**S**ervice-**O**riented **A**rchitecture): "*As arquiteturas orientadas a serviços (SOA, do inglês service-oriented architectures) são uma forma de desenvolvimento de sistemas distribuídos em que os componentes de sistema são serviços autônomos*" (p. 356)
* **Motivação**: 
	* inicialmente = acesso a sites, sem possibilidade de acesso aos dados por outro meio
	* web service = acesso a sites E disponibilização de dados por meio de serviços na web
	* "*Geralmente, um web service é uma representação-padrão para algum recurso computacional ou de informações que pode ser usado por outros programas, os quais podem ser recursos de informações, como um catálogo de peças, recursos de computador, tais como um processador especializado, ou recursos de armazenamento.*" (p. 355)
* def::**Serviço**: "*um ato ou desempenho oferecido de uma parte para outra. Embora o processo possa ser vinculado a um produto físico, o desempenho é essencialmente intangível e normalmente **não resulta da posse de qualquer um dos fatores de produção.***" (Sommervile, p. 355)
* def::**Serviço**: "*Um componente de software de baixo acoplamento, reusável, que encapsula funcionalidade discreta, que pode ser distribuída e acessada por meio de programas.*" (Sommervile, p. 359)
	* "*a essência de um serviço é que o fornecimento de serviço é independente da aplicação que o usa*" (Sommervile, p. 356)
	* "*A construção de aplicações baseadas em serviços permite que empresas e outras organizações cooperem e façam uso das funções de negócios umas das outras*" (Sommervile, p. 357)
	* "*Um web service é um serviço acessado usando protocolos baseados em padrões da Internet e em XML.*" (Sommervile, p. 359)
	* "*os **serviços não têm estado**, e gerenciar estado específico da aplicação do serviço é de responsabilidade do usuário do serviço, e não do serviço em si*" (Sommervile, p. 364)
* **Protocolos/padrões**: 
	* **Baseado em XML** (E**x**tensible **M**arkup **L**anguage), XSD (**X**ML **S**chema **D**efinition), XSLT (E**x**tensible **S**tylesheet **L**anguage **T**ransformation)
		* Troca de mensagens: (define mensagem e troca de mensagem)
			* SOAP (**S**imple **O**bject **A**ccess **P**rotocol)
		* Definição de serviços:
			* WSDL (**W**eb **S**ervice **D**escription **L**anguage): interface { nome da operação, parâmetros, tipos }
				* não contêm informações semânticas do serviço, informando o que ele faz
			*  UDDI (**U**niversal **D**escription, **D**iscovery and **I**ntegration): descoberta
				* pouco usado, optou-se por adotar mecanismos de pesquisa padrão + WSDL
		* Suporte:
			* WS-Security (**W**eb **S**ervices **S**ecurity)
			* WS-Addressing (**W**eb **S**ervices **A**ddressing)
			* WS-Reliable Messaging, WS-Transactions
		* Processo (workflow, para definir programas que envolvam vários serviços)
			* WS-BPEL (**W**eb **S**ervices **B**usiness **P**rocess **E**xecution **L**anguage)
	* [[RESTful]]
	* [[Microsserviços]]
	* next_step::Estudar XML, XSD, XPath e XSLT
* **Canal de comunicação**:
	* **stub**: parte do cliente que abstrai a comunicação na chamada
	* **skeleton**: parte do servidor que abstrai a comunicação na chamada
	* anki::Pesquisar um diagrama apresentando esses elementos e desenvolver cards do Anki
* **Elementos**: solicitante de serviço + registro de serviço + provedor de serviço
* **Metodologias**:
	* [[12 Factor App]]

next_step::Estudar Sommervile cap. 19
