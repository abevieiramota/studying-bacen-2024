# SMTP (Simple Mail Transfer Protocol)

* **Elementos de um sistema de correio eletrônico** { MUA, MTA, MDA }
	* **MUA** (Mail User Agent) - agentes do usuário; software do usuário, que permite acesso e gerenciamento das mensagens; pode usar protocolos de correio eletrônico ou ser WebMail, utilizando HTTP e navegador Web
	* **MTA** (Mail Transfer Agent) - agentes de transferência; servidores de e-mail que atuam de forma intermediária, ==como cliente e como servidor==, no envio e recebimento de mensagens
	* **MDA** (Mail Delivery Agent) - garante que a mensagem chegue no destinatário (do servidor de e-mail ao usuário), usando protocolos como o IMAP e POP
	* **Features**
		* notificação de entrega/leitura
		* priorização de mensagens
		* envio de mensagem para múltiplos destinatários ou lista de distribuição
			* o envio de mensagem para múltiplos destinatários é implementado como envio de uma mensagem, com mesmo conteúdo e pelo MTA do remetente, para cada destinatário
			* o envio de mensagem para lista de distribuição é implementado como envio de uma mensagem para o MTA da lista, que irá enviar uma mensagem, com mesmo conteúdo, para cada destinatário
		* redirecionamento de mensagem
	* **Estrutura de mensagem** { Envelop, Message Content }
		* **Envelope**: dados necessários pelo MTA para envio da mensagem ao destino, ex: { endereço de origem, endereço(s) de destino(s), detalhes de segurança/prioridade etc }
		* **Conteúdo**: composto por { Header, Body }, separados por uma linha em branco
			* **Header**: contém dados necessários pelo MUA, ex: { Content-Type, To, From, Subject etc } 
			* **Body**: conteúdo da mensagem
* **Características**
	* usado na comunicação entre MTAs
	* permite modo Open Relay, habilitando o uso do servidor por qualquer um que se conecte - recomendado ser desabilitado
	* codificação padrão ASCII, mas podendo ser estendida para outros formatos, por meio de codificação MIME (Multipurpose Internet Mail Extensions)
	* endereçamento de usuários é baseado em DNS para resolução de domínio em IP dos MTAs
	* porta TCP ==25==
	* porta TCP 465 com SSL
	* arquitetura request-response
	* não implementa recursos de segurança nativos
	* trabalha com modelo store-and-forward (agentes responsáveis por encaminhamento armazenam as mensagens até conseguirem enviar)
	* envia e-mail com descrição de erro para o remetente, caso ocorra
	* utiliza conexão persistente (similar ao HTTPv1.1)
	* servidores modernos adotam políticas de timeout para ausência de mensagens numa conexão
* **Comandos**
	* HELO -> identifica o emissor na sessão
	* MAIL -> inicializa o envio de uma mensagem
	* RCPT -> define o destinatário - executado uma vez para cada destinatário, quando múltiplos
	* DATA -> indica que será enviado o corpo da mensagem
	* RSET -> aborta a transação corrente
	* QUIT -> requisita término da sessão
* **ESMTP** (Extended SMTP)
	* versão posterior, solicionando alguns problemas
	* **Características**
		* aumento da capacidade da mensagem
		* mudança na codificação das mensagens #TODO para qual?
		* implementação de confirmação de entrega, DSN (Delivery Status Notification)
		* implementação de autenticação, AUTH, como medida de segurança
		* para verificar se o servidor suporta ESMTP, o client envia um comando EHLO
* **Pegadinhas**
	* o e-mail é composto por um envelop e, no conteúdo, um header; ambos contêm 'metadados', mas são destinados a agentes diferentes -> { envelop: MTA, header: MUA }
	* o comando para verificar se o servidor suporta ESMTP é um HELO, mas colocando na letra inicial a mesma inicial de ESMTP -> EHLO
* **Extra**
	* **Configuração do POSTFIX** (servidor usado em distribuição UNIX)
		* arquivo fica em /etc/postfix/main.cf
		* **Parâmetros**
			* daemon_directory - diretório de localização de daemons
			* mynetwork - configurações que indicam clientes que podem usar o servidor como relay
			* ? há outros na apostila do estratégia, mas não entendi... ?