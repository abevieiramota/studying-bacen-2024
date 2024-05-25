* **Security Assertion Markup Language** -> sistema de autenticação (!), podendo, por meio de 'gambiarras', servir também para autorização
	* utilizado para informar a aplicativos/serviços sobre autenticidade de um usuário -> isso habilita usos como o de SSO, já que o usuário pode se autenticar apenas uma vez e essa autenticação ser reutilizada entre sistemas diversos
* **XML** para comunicação
* Criptografia com protocolos proprietários
* Atualmente na versão SAML 2.0
* **Papéis** 
	* **Service Provider** -> aplicativo/serviço que o usuário deseja acessar
	* **User Agent** -> quem está tentando acessar um aplicativo/serviço; também chamado principal/titular
	* **Identity Provider** -> IdP, provedor de identidade, serviço que armazena e confirma a identidade de usuários, permitindo autenticação por meios como login
* **Declaração SAML** -> mensagem que diz a um prestador de serviços que um usuário está conectado. As declarações SAML contêm todas as informações necessárias para que um provedor de serviços confirme a identidade do usuário, incluindo a fonte da declaração, o momento em que ela foi emitida e as condições que tornam a declaração válida.
* 