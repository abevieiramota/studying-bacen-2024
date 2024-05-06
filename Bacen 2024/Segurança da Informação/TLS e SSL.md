* def::**TLS (Transport Layer Security)**: 
* def::**SSL (Security Socket Layer)**: 
* **Características** (aplicam-se aos dois, a menos que especificado)
	* **Motivação**: necessidade de comunicação segura em meios compartilhados, como Internet (ex: transação bancária)
	* permitem o envio seguro de informações criando um canal seguro e versátil, zelando pelos princípios da { autenticidade, integridade, confidencialidade }
		* autenticidade -> verifica a identidade das partes, usando [[Criptografia#^def-criptografia-assimetrica|criptografia assimétrica]] -> assimétrico para torca de chaves
		* confidencialidade -> protege tráfego de usuários não autorizados com [[Criptografia#^def-criptografia-simetrica|criptografia simétrica]] -> simétrico para troca de mensagens
		* integridade -> reconhece alterações nos dados
		* ! não há relação com o princípio da disponibilidade
	* criam uma camada na arquitetura TCP/IP para uso por protocolos da camada de aplicação (ex: HTTP, POP3, SMTP etc)
		* ! localizada numa camada intermediária entre as camadas de aplicação e transporte (ex: HTTP > SSL > TCP > IP)
			* ! cuidado, não é na camada de rede
		* o uso desses protocolos é transparente para o usuário
	* tem capacidade de compressão de mensagens
	* não há distinção substancial entre SSL e TLS, mas eles não interoperam (as duas partes devem usar o mesmo protocolo)
	* **Diferenças**
		* TLS suporta diversas portas, enquanto o SSL usa porta fixa
		* TLS usa algoritmos de criptografia mais robustos, como o HMAC, enquanto o SSL suporta apenas MAC
		* TLS pode ser utilizado por autoridades intermediárias em infraestruturas de chaves públicas, enquanto SSL depende sempre da autoridade raiz
* **Arquitetura**
	* **Camada de conexão SSL**
		* **Handshake Protocol** -> 
			* responsável por:
				* estabelecimento da comunicação segura
				* autenticação das partes
				* escolha de algoritmos de criptografia
			* etapas:
				* negociação da versão do protocolo a ser utilizada
				* negociação dos algoritmos -> o cliente requisita comunicação segura, enviando listas de algoritmos suportadas, e o servidor responde com a algoritmos selecionados; busca-se escolher o algoritmo mais robusto suportado pelas duas partes
				* troca de chaves e autenticação -> troca de chaves para realizarem autenticação (criptografia assimétrica -> ver que há troca de chaves, mais de uma chave); aplica-se o conceito de [[Certificado Digital]]
				* encriptação simétrica e autenticação das mensagens -> a partir de agora as mensagens passam a usar funções hash para autenticação
		* **Alert Protocol** -> responsável pelo controle do protocolo por meio da troca de mensagens vinculadas ao funcionamento e tramissão de dados na conexão
			* semelhante ao ICMP em relação ao IP
			* possui dois tipos de alerta -> Fatal, que interrompe imediatament a transmissão; Warning, que serve para ir ajustando a transmissão
			* estrutura de 2 bytes { tipo da falha, detalhe da falha }
		* **Change Cipher Spec** -> é o que define o ponto a partir do qual toda a comunicação será criptografada de acordo com o definido no handshake
			* ambas partes precisam emitir essa mensagem -> aí a sessão TLS/SSL passa a estar de fato aberta e a usar o Record Protocol
	* **Camada de segurança e integridade dos dados**
		* **Record Protocol** -> protocolo responsável pelo encapsulamento/mascaramento/ofuscamento dos dados
			* recebe dados abertos da camada de aplicação, encapsula e realiza uma ou duas das seguintes operações
				* encriptar -> garante confidencialidade
				* adicionar MACs (Message Authentication Codes) -> garante integridade
* Lançamento/aposentadoria
	* SSL 2.0 \[1995, 2011\] -> criado pela Netscape
	* SSL 3.0 \[1996, 2015\]
	* TLS 1.0 \[1999, 2020\] -> criado pelo IETF
	* TLS 1.1 \[2006, 2020\]
	* TLS 1.2 \[2008, **hoje**\]
	* TLS 1.3 \[2018, **hoje**\] [diferenças em 07:00](https://www.estrategiaconcursos.com.br/app/dashboard/cursos/275778/aulas/2640908/videos/180002) { simplificação da comunicação, maior segurança, assinatura mais robusta, melhor algoritmo de curvas elípticas, desempenho do handshake }
	* ! importante, o recomendado hoje é usar TLS { 1.2, 1.3 }
* tool::**OpenSSL**: ferramenta open-source, escrita em C, com suporte para SSL e TLS, suportando diversos algoritmos
* 




![[Pasted image 20240505094957.png]]

![[Pasted image 20240505095846.png]]