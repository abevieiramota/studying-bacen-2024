[Site](https://grpc.io/) "*gRPC is a modern open source high performance Remote Procedure Call (RPC) framework that can run in any environment. It can efficiently **connect services** in and across data centers with pluggable **support for load balancing, tracing, health checking and authentication**. It is also applicable in last mile of distributed computing to **connect devices, mobile applications and browsers to backend services**.*"

"*Geralmente, as comunicações RPC são mais rápidas do que a interação baseada em mensagens usada em sistemas orientados a serviços*" (Sommervile p. 347)

[Estratégia](https://www.estrategiaconcursos.com.br/app/dashboard/cursos/275777/aulas/2640897/videos/135114)

* A high performance, open source universal RPC framework (chamada remota)
* RPC
	* server disponibiliza skeleton (definição dos serviços)
	* client baixa o skeleton e gera classes clients para usar os serviços = stubs
	* o client faz chamada 'como se fosse' nativa - o stub é responsável por fazer a chamada remota
	* por muito tempo foi considerado um antipattern, por ser lento
* gRPC - framework de comunicação desenvolvido pelo Google focado em alto desempenho
	* por que passou a ser usado, se RPC era mal visto? 
		* uso em microsserviços
		* baseado no protocolo de comunicação **protobuf
		* capacidade de fazer { balanceamento de carga, autenticação, tracing/health checking }
	* protocol buffers (por padrão usa o protobuf, mas pode usar outros protocolos! é plataforma agnóstica!)
		* pode ser usado como IDL (Interface Definition Language)
		* pode ser usado para especificar o formato dos dados 
		* são trafegados binários, no lugar de texto (o que melhora performance!)
		* ![[Pasted image 20240309103404.png]]
		*  ![[Pasted image 20240309103555.png]]
		* ![[Pasted image 20240309103724.png]]
	* No servidor, em java, o serviço implementa GreeterGrpc.GreeterImplBase

gRPC x REST
* interessante REST para disponibilizar para clients gerais, não especialistas, para web services
	* fácil de entender
	* baseado em HTTP
	* fraco acoplamento entre cliente e servidor
	* suporte por diversas linguagens
	* DV: { não é bom para streaming/high volume, sem API contract, baseado em protocolos não otimizados }
* gRPC para clients especialistas, dentro da DMZ, na cloud 
	* API contract mais rígido (o stub é gerado usando o skeleton disponibilizado pelo servidor)
	* orientado a funções, ao invés de recursos
	* latência de rede reduzida (roda em cima do http 2.0 (padrão de comunicação binária))
	* comunicação bidirecional
	* code generation -> o código de uso do serviço é gerado automaticamente usando o skeleton
	* DV: { pouco conhecido, caching + complicado }
* gRPC x SOA
	* similar, com SOA usava SOAP, agora com gRPC
* Opções de conexão
	* request + response: unary RPC -> como se fosse uma chamada normal a função
	* request + server-stream (ex: youtube): server streaming 
	* stream + response: client streaming
	* stream + stream: bidirectional streaming (as streams funcional independentemente)
* Opções de deadline para response
	* timeout para resposta
	* max retries + frequência de retry (pode ser randômico)
	* 