* **Características**
	* camada de aplicação
	* arquitetura cliente-servidor -> requisição-resposta
	* stateless
	* portas
		* port::TCP/80
		* port_secure::TCP/443
		* port_tip::80 e 4+4 = 8
	* [RFC 9110 - HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110.html) [Mozilla](https://developer.mozilla.org/en-US/docs/Web/HTTP)
* **Def**: protocolo para a troca ou transferência de hipertexto utilizado em sistemas de hipermídia, distribuídos ou colaborativos
* **Versões**
	* HTTPv1.0
		* sem conexão persistente
	* HTTPv1.1
		* com conexão persistente -> uma mesma conexão TCP é usada para múltiplas requsições/respostas
		* pode enviar múltiplas requisições sem precisar aguardar resposta (modo paralelo/pipelining)
	* HTTPv2.0
		* suporta recursos das versões anteriores
		* foco em eficiência da comunicação (velocidade e uso de recursos)
		* conexão persistente (usa apenas uma simultaneamente por cliente) #n_entendi ; por meio de multiplexação, permite múltiplos fluxos numa mesma conexão
		* compressão automática (nas versões anteriores não fazia parte do protocolo, utilizava-se o GZIP no lado do servidor), incluindo HPACK para compressão do header -> é recomendado não usar outra compressão
		* TLS não obrigatório, mas, se usado, exige TLS 1.2 ou superior #n_entendi 
			* com TLS 1.2, é necessário desabilitar a renegociação de conexão
		* otimização no envio de headers, enviando apenas o que não foi enviado anteriormente (ex: nas versões anteriores, User-Agent era enviado repetidamente em cada resposta)
		* capacidade de priorizar requisições (ex: priorizar main.html e depois os demais recursos, como imagens)
		* server push -> o próprio servidor envia dados, sem precisar de requisição (ex: solicitou index.html, o servidor já manda também os demais recursos linkados no index.html)
* **Tipos de mensagens**
	* **Request**
		* GET /index.html HTTP/1.1 <- request line (método, path do objeto, versão do protocolo)
		* Date: Thu, 20 May 2004 21:12:55 GMT  <- header (property: value)
		* Connection: close
		* {"doAction": "pay"} <- message body
	* **Response**
		* HTTP/1.1 200 OK <- status line (versão do protocolo, código de retorno/estado da conexão)
		* Server: Apache/1.3.27 <- header
		* Accept-Ranges: bytes
		* \<html\>...\<\html\> <- message body
* **Métodos** (9)
	* GET - solicitação de recurso
	* PUT - inserção de recurso
	* POST - envio de dados para o servidor
	* HEAD - similar ao GET, mas o body não é retornado
	* DELETE - remoção de recurso
	* OPTIONS - consulta de opções de requisição para dado recurso
	* TRACE - usado para debuggar requisições
	* CONNECT - inicia uma comunicação de duas vias (ex: uso de TLS #n_entendi)
	* PATCH - aplica modificações parciais a recursos ~ similar ao Update no CRUD
* **Headers**
	* Host -> nome de DNS e, opcionalmente, porta do servidor
	* Authorization -> credenciais do cliente para autenticação
	* Referer -> endereço da página de onde partiu a requisição
	* Location -> endereço da página à qual deve ser feito redirecionamento (usado em respostas 3xx ou 201 - CREATED)
	* #TODO
* **Códigos de status** ^http-status-code
	* 1xx - Informação
	* 2xx - Sucesso
	* 3xx - Redirecionamento
	* 4xx - Erro de cliente
		* 400 - BAD REQUEST
		* 401 - UNAUTHORIZED
		* 403 - FORBIDDEN
		* 404 - NOT FOUND
	* 5xx - Erro de servidor
		* 500 - INTERNAL SERVER ERROR
		* 503 - SERVICE UNAVAILABLE
		* 505 - ==VERSION NOT SUPPORTED==
* **HTTPS**
	* criptografia por protocolos [[TLS e SSL]]
	* os dados são cifrados para uma comunicação segura
	* permite verificar a autenticidade do servidor e do cliente, por meio de certificados digitais
		* tunelamento simples -> autentica apenas o servidor
		* tunelamento mútuo -> autentica servidor e cliente
	* processo de estabelecimento de conexão: SYN > SYN ACK > ACK ClientHello > troca de chaves/autenticação > conexão aberta #TODO ver melhor quando tiver estudado mais sobre criptografia
* **Pegadinhas**
	* o nome do método, na requisição, deve estar em maiúsculo