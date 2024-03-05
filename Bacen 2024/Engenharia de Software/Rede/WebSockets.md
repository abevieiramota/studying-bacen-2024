[Estratégia](https://www.estrategiaconcursos.com.br/app/dashboard/cursos/275777/aulas/2640897/videos/132945)

* exemplo dado: painel de senha, no lugar de ficar fazendo polling para verificar as senhas no servidor (short ou long polling), manter conexão aberta
* SSE - Server Sent Events: cria conexão, o servidor fica responsável por notificar o client, unidirecional
* já faz parte da especificação JavaEE
* esquema de URI *ws*, porta 80 por padrão, 443 com TLS
* WebSockets - cria conexão, servidor e cliente pode enviar dados - **bidirecional**
	* vantagens
		* real-time
		* usa protocolo próprio, mas com compatibilidade com o HTTP/TCP -> por meio de Header Upgrade, atualizando o protcolo HTTP para WebSocket
		* full duplex, bidirecional
* Estados #anki
	* 0 - Conexão não estabelecida
	* 1 - Conexão estabelecida e comunicação pode ser realizada
	* 2 - Conexão fechando
	* 3 - Conexão fechada
* Eventos
	* open -> quando a conexão foi estabelecida; Socket.onopen
	* message -> quando recebe mensagem do servidor; Socket.onmessage
	* error -> quando ocorre erro na comunicação; Socket.onerror
	* close -> quando a conexão é fechada; Socket.onclose
* Métodos
	* Socket.send()
	* Socket.close()
	* não tem receive! as mensagens são recebidas via callback


Java - anotações
* @ServerEndpoint: subir o server
* @ClientEndpoint: classe cliente
* @OnOpen: callback para início
* @OnMessage: callback para mensagem
* @OnError, @OnClose

![[Pasted image 20240303175750.png]]
![[Pasted image 20240303175802.png]]