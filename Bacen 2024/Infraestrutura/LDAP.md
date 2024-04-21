# LDAP

* Lightweight Directory Access Protocol - protocolo de ==acesso== a serviço de diretório
	* ! as bancas tendem a considerar LDAP como "serviço de diretórios", que é mais amplo do que a definição precisa
* características
	* portas TCP { soma dos dígitos extremos é 12 }
		* port::TCP/389
		* port_secure::TCP/636
		* port_tip::as pontas somam 12
	* utiliza estrutura em ==árvore== de domínios relacionais DIT - Directory Information Tree
		* nós superiores são domínios/subdomínios > organograma, nós inferiroes são os objetos da rede
	* é versão simplificada e otimizada do X.500 para arquitetura TCP/IP
	* autenticação, autorização etc-segurança
		* autenticação baseada em { senha, chave pública, certificado digital etc }
		* criptografia via túnel SSL/TLS
		* controle de acesso, via políticas
		* logging de auditoria, registrando eventos como autenticação bem-sucedida etc
		* proteção contra ataques de { força bruta, injeção de código, DoS etc }, como limite de tentativas de autenticação, validação de dados de entrada etc
		* políticas de senha { complexidade, prazo de expiração, bloqueio após erros etc }
	* comunicação assíncrona
	* protocolo/padrão aberto
	* permite armazenar de forma segura dados como senhas - usa MD5 como hash padrão
	* integrável com o AD - Active Directory (o próprio AD usa LDAP em sua implementação)
	* implementação open source OpenLDAP
		* usa bancos próprios { LDBM, BerkeleyDB }
		* dá suporte a uso de outros bancos relacionais
		* autenticação { Anônimo, Simples, SASL etc }
			* Anonymous - acesso sem fornecimento de credenciais; normalmente com diretórios públicos, como lista de telefones
			* Simple Bind - usuário fornece nome de usuário e senha; mais comum
			* SASL - Simple Authentication and Security Layer - framework de segurança baseado em desafio-resposta #n_entendi;suporta diversos mecanismos de autenticação e permite que o cliente e servidor negociem qual usar { Kerberos, LDAP, DIGEST-MD5, GSSAPI etc }
		* arquivo de configuração
			* server: /usr/local/etc/OpenLDAP/**s**lapd.conf
			* client: /usr/local/etc/OpenLDAP/ldap.conf
		* instalação 
			* sudo apt install slapd ldap-utils
	* o formato LDIF (LDAP Data Interchange Format) é usado para representar entradas LDAP e modificações nos registros na forma de texto. As funções do arquivo LDIF são importar dados para o diretório, alterar objetos existentes, criar o backup do diretório e fazer a replicação do diretório
* gerenciamento de recursos em rede pode se dar de forma { centralizada, descentralizada }
	* descentralizada -> cada máquina é administrada localmente; leva a crescimento 'exponencial' de complexidade, em relação à quantidade de dispositivos
	* centralizada -> usa um repositório de informações sobre os elementos de rede, facilitando consulta
		* elementos de rede { usuários, dispositivos, serviços, grupos etc }
	* diretório pode ser { banco relacional, arquivo texto, pastas etc }
	* deve suportar alto volume de consultas
	* pode assumir baixo volume de inserções/modificações
* X.500 é um protocolo de consulta a informações de diretório
	* define forma de conexão
	* { acesso, integração } de sistemas e servidores ao diretório
	* aderente ao modelo OSI
	* são usados agentes para a comunicação
		* agente de usuário -> consulta diretório
		* agente de sistema de diretório -> responde a requisições
* tipos de atributos que compõem o **DN** - Distinguished Name
	* **CN** - Common Name
	* **SN** - Surname
	* **C** - Country code - 2 dígitos
	* **O** - Organization name
	* **OU** - Organization Unit name
	* **DC** - Domain Component - arbitrário e pode possuir mais de um
	* ! Os atributos são dispostos do mais específico para o mais genérico
	* Exemplos
		* CN=Jeff Smith,OU=Sales,DC=Fabrikam,DC=COM
		* CN=Karen Berge,CN=admin,DC=corp,DC=Fabrikam,DC=COM
* Comandos
	* BIND - autenticar sessão LDAP, informando usuário, senha e versão do protocolo
	* UNBIND - encerrar sessão LDAP
	* SEARCH 
	* COMPARE - verifica se uma entrada tem determinado atributo
	* ADD - adiciona nova entrada ao diretório
	* MODIFY - altera entrada existente
	* ABADON - aborta uma requisição prévia
	* DELETE - deleta entrada existente
	* MODRDN - renomeia uma entrada existente
	* STARTTLS - inicia criação de túnel seguro TLS/SSL
* Pegadinhas
	* para identificar unicamente um objeto, não se pode utilizar o DN, porque ele depende da localização do objeto no diretório, que pode mudar; usa-se um atributo UUID
	* os dados são representados como estrutura hierárquica -> cuidado com afirmações de ser em tabela, ser 'compatível' com SQL etc