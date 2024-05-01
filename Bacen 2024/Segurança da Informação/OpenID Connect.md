* **OpenID Connect (OIDC)** -> protocolo de identidade que utiliza os mecanismos de autorização e autenticação do OAuth 2.0
	* OIDC -> autenticação, enquanto OAuth 2.0 -> autorização
	* usa OAuth 2.0 como protocolo subjacente
* permite aos clientes/aplicações a verificação da identidade do usuário final integrado aos recursos do servidor de autorização
* usa JWT (JSON Web Tokens) e REST
* tem consentimento integrado [f](https://auth0.com/pt/intro-to-iam/what-is-openid-connect-oidc)
* multiplataforma
* mais simples que SAML 2.0
* faz uso de token de ID, em JWT, contendo o resultado da autenticação; de acesso e de atualização
	* tokens de ID devem ser assinados digitalmente
* fluxos comuns
	* implícito -> tokens devolvidos para o Relying Party diretamente na URI de direcionamento, comumente usado em SPAs
	* de código de autorização -> mais seguro que o fluxo implicito, não retorna o token diretamente para o RP
	* híbrido -> retorna diretamente para o RP apenas o token de ID
* a especificação do OpenID Connect não especifica a mecânica de autenticação a ser utilizada, ex { usuário+senha, código por SMS/e-mail, biometria, federado etc }