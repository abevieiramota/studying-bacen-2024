**Re**presentational **S**tate **T**ransfer - estilo de arquitetura (restrições a serem seguidas na criação de web services)

**Requisitos**
* **Uniform interface**
	* Resource-based - URLs linkam recursos, comandos via métodos HTTP
	* Manipulation of resources through representations - os recursos são representados (JSON, XML etc) e contém instruções para manipulá-los
	* Self-descriptive messages - as respostas são descritivas o suficiente para que o cliente saiba como usá-las (ex: retornar Content-Type informando o formato do recurso)
	* **H**ypermedia **A**s **T**he **E**ngine **O**f **A**pplication **S**tate (HATEOAS) - deve ser possível descobrir toda a API manipulando os recursos; linkar recursos com outros recursos, permitindo navegação sem precisar consultar documentação
* **Stateless** - o estado necessário para processar a requisição deve estar contido na própria requisição; promove maior escalabilidade (já que qualquer servidor pode atender as requisições, não dependendo de estado de requisições anteriores)
* **Cacheable** - respostas devem conter informações sobre se podem ser cacheadas; ETag -> identificador de versão de recurso
* **Client-Server**
* **Layered System**

**Ferramentas**
* Spring Boot - #TODO
	* Controller que atende requisições REST é anotado com @RestController
* OpenAPI Specification - formato de documentação de APIs Rest; documenta endpoints disponíveis, operações, parâmetros/outputs, métodos de autenticação, informações de contato, licença etc; escrita em YAML ou JSON
* Swagger - conjunto de ferramentas open-source em torno da OpenAPI Specification; { editor de documentação, renderizador de documentação, gerador de código de cliente/server, parsers etc }

**Best practices**
* operações que não mapeiam tão diretamente para recursos podem ser modeladas como atributos de recursos (ex: ativar um registro pode ser implementada como um put alterando o valor de activated do registro)
* versão da API como parte da URL
* permitir retornar apenas subconjunto dos atributos do recurso (com um query parameter para especificar quais, por exemplo)
* use HTTP status code adequadamente
	* 200 OK - sucesso
	* 201 Created - POST que resultou em criação de recurso
	* 204 No Content - resposta a requisição que não gera dados (ex: DELETE)
	* 304 Not Modified - quando há cache e o recurso não foi alterado
	* 400 Bad Request - request mal formada
	* 401 Unauthorized - erro de autenticação
	* 403 Forbidden - autenticado, mas sem autorização para acessar o recurso
	* 405 Method Not Allowed - método não autorizado para o usuário
	* 410 Gone - recurso não mais disponível
	* 415 Unsupported Media Type - formato solicitado não suportado
	* 422 Unprocessable Entity - erros de validação
	* 429 Too Many Requests - requisição rejeitada por limite de requisições

 "*Os atuais padrões de web services têm sido criticados como padrões ‘pesados’, muito gerais e ineficientes. Implementar esses padrões requer uma quantidade considerável de  processamento para criar, transmitir e interpretar as mensagens XML associadas. Por essa razão, algumas organizações, como a Amazon, usam uma abordagem mais simples e mais eficiente para comunicação de serviços, usando os chamados serviços RESTful*" (Sommervile p. 357)
