* def::**OAuth**: Protocolo que permite aos usuários ter acesso limitado a recursos de um website sem precisar expor suas credenciais; descreve uma maneira segura de acessar recursos de terceiros
* Trabalha de forma dinâmica com trocas de chaves
* Necessário uso de HTTPS
* **Papéis**
	* **Resource Owner** -> pessoa que concede acesso aos seus dados -> ex: autoriza site do estratégia para recuperar dado de foto, e-mail etc do google
	* **Resource Server** -> provedor de identidades #n_entendi 
		* pode ser público, permitindo qualquer serviço terceiro usar -> google
		* pode ser privado, permitindo apenas serviços autorizados -> gov.br
	* **Authorization Server** -> responsável por autenticação e emissão dos tokens de acesso (access token) para os clients (aplicação requisitante)
		* no exemplo do estratégia, ele que é o client
		* **bearer token** -> 
			* é referenciado no cabeçalho das requisições HTTP, devendo ser sempre feita com HTTPS, dado que o token é enviado de forma aberta no cabeçalho, da seguinte forma:
			* Authorization: Bearer SEU_TOKEN_DE_ACESSO
				* ! campo Authorization
				* ! prefixado com Bearer e espaço
	* **Client** -> camada que oferece os serviços requisitados pelo usuário e que, para isso, solicita acesso aos seus recursos; o escopo é que define quais recursos se quer acessar
	* **refresh token** -> usado quando o client é autorizado a ele mesmo gerar novos access token, isso por um tempo limitado #n_entendi 
* pode usar JWT (JSON Web Token)
* 





![[Pasted image 20240501174214.png]]

![[Pasted image 20240501175112.png]]