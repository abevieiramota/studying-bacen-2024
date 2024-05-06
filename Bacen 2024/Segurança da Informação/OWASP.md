* def::**OWASP (Open Worldwide Application Security Project)**: função sem fins lucrativos com foco em melhoria na segurança de software
* **Características**
	* visão agnóstica de tecnologias e soluções
	* apoia o processo de segurança durante todo o seu ciclo
	* simples, desenhado para fácil absorção pelas equipes
	* é necessário ter domínio básico de princípios de segurança da informação
* [[CLASP|OWASP CLASP Project]]
* **Melhores práticas de codificação segura** ^owasp-codificacao-segura
	* Pontos de Falha no ciclo -> onde podem estar as falhas
		* Início -> quando sequer se considera segurança no processo
		* Arquitetura conceitual -> falhas na definição da arquitetura
		* Más práticas de programação
		* Implementação do software -> aqui envolve deploy
		* Falhas de manutenção e atualização
	* Pontos de Impacto -> o que será prejudicado caso falhas sejam exploradas
		* Software e informações
		* SO dos servidores
		* Base de dados do backend
		* Apps em ambiente compartilhado
		* Sistema do usuário
		* Outros SW de interação
	* **Listas de verificação**
		* **Validação de dados de entrada**
			* centralização da validação de dados de entrada
			* definir encoding para todas fontes de entrada de dados
			* rejeitar dados de entrada, caso haja falha de validação -> ex: SQL injection
			* validar, dos dados, 
				* tipos esperados
				* intervalos
				* tamanho
				* 'lista branca', especificando mais detalhes do que é aceito -> ex: formato de e-mail
		* **Codificação de dados de saída**
			* realizar sanitização de dados -> ex: escapar caracteres especiais para SQL em texto a ser utilizado em SQL
		* **Autenticação e gerenciamento de credenciais**
			* exigir autenticação para todo recurso que não seja público
			* garantir a segurança dos controles de autenticação, possivelmente centralizando em um servidor -> SSO, OAuth etc
			* definir procedimento a ser disparado em caso de falha no sistema de autenticação
			* alto nível de segurança para as funções administrativas/de gerenciamento de contas
			* caso a aplicação gerencie credenciais, deve armazenar senhas na forma de [[Técnicas#^def-one-way-salted-hash|one-way salted hashes]] e garantir que apenas ela manipule onde esses dados são registrados
			* mensagens de falha de autenticação não devem fornecer detalhes sobre a falha -> ex: não indicar se é o usuário que não existe, se a senha está incorreta etc
			* usar autenticação entre serviços
			* processos de redefinição de senha não podem ter níveis de segurança inferiores
			* garantir conformidade a política de senhas -> ex: formato, tamanho, periodicade de atualização etc
			* informar ao usuário o momento de última autenticação -> permite que o próprio usuário verifique se houve acesso não autorizado
			* exigir nova autenticação antes de realizar operações críticas -> ex: aplicativo de banco, que exige biometria para confirmar transferência
		* **Gerenciamento de sessões**
			* garantir a segurança na criação de identificadores de sessão, por exemplo, centralizando em um servidor
			* logout deve encerrar completamente a sessão/conexão associada
			* logout deve estar disponível em toda tela que exija autenticação
			* minimizar o tempo de sessão, considerando o tradeoff com outros requisitos
			* não permitir sessões simultâneas com mesmo usuário
			* na alteração de protocolo HTTP para HTTPS, gerar novo identificador de sessão
			* usar HTTPS mesmo na rede interna
			* configurar atributo secure em cookies transmitidos por conexão TLS
			* configurar cookies com o atributo HttpOnly, a menos que seja necessário definí-los /alterá-los client-side
		* **Controle de acessos**
			* utilizar apenas um componente único para autorização em aplicação Web
			* definir procedimento a ser disparado em caso de falha no sistema de autorização
			* isolar no código os trechos que contêm lógica privilegiada -> ex: código de admin
			* dados armazenados no lado cliente, utilizar mecanismos de criptografia e de verificação de integridade para detectar possíveis adulterações
			* auditar contas de usuários e assegurar a desativação de contas que não devem mais ser utilizadas
			* contas de serviço/acesso externo devem ter o menor privilégio possível
			* restringir { URLS protegidas, funções privilegiadas, referências diretas a objetos, serviços, dados, configurações de segurança } a usuários autorizados
		* **Práticas de criptografia**
			* definir procedimento a ser disparado em caso de falha no sistema de criptografia
			* definir e implantar processo de gerenciamento de chaves criptográficas
		* **Tratamento de erros e log**
			* não expor dados sensíveis em mensagens de erro, incluindo detalhes de sistema, id de sessão e informações dos usuários
			* não expor informações de debug/pilha de execução -> ex: ativar mecanismo de debug em produção
			* devem ser registrados logs sobre eventos de segurança com sucesso e com falha
			* restringir acesso a logs apenas a pessoas autorizadas
			* registrar { falhas de entrada de dados, tentativas de autenticação, falhas em controle de acesso, eventos suspeitos de adulteração, tentativas de conexões com tokens de sessão inválidos/expirados, exceções lançadas pelo sistema, uso de funções administrativas, falhas de conexão TLS com o backend, falhas no módulo de criptografia }
			* utilizar função de hash criptográfica para validar a integridade dos registros de log
		* **Proteção de dados**
			* implementar política de privilégio mínimo
			* criptografar informações sensíveis (! alerta para o uso de algoritmos conhecidos, padronizados, bem testados)
			* proteger o código-fonte
			* remover comentários em código de produção que pode ser acessado por usuários e podem revelar detalhes internos do sistema
			* não incluir informações sensíveis em path param
			* desativar a cache realizada no client-side (uso do cabeçalho Cache-Control: not-store)
		* **Segurança nas comunicações**
			* utilizar criptografia na transmissão de dados sensíveis -> TLS para proteger a conexão + criptografia de arquivos ou conexões que não usam HTTP
			* certificados TLS devem ser válidos, possuíram o nome de domínio correto, não estarem expirados e serem instalados com certificados intermediários, quando necessários (cadeia de certificados)
			* utilizar conexões TLS para todo conteúdo que requeira autenticação ou contenha informação sensível
			* utilizar um padrão único de implementação TLS configurado de modo apropriado -> ex: túnel ou transporte
		* **Configuração do sistema**
			* garantir que servidores, frameworks, componentes etc usem a última versão aprovada (! cuidado, não necessariamente a última lançada, que pode conter bugs etc -> necessário validar primeiro)
			* restringir para o mínimo o possível os privilégios de servidores Web
			* remover funcionalidades e arquivos desnecessários
			* caso use HTTP 1.0 e 1.1, garantir que há compatibilidade #n_entendi 
			* gerenciar atualização de código
			* isolar ambientes de dev, hml, prod, para que sistema em cada ambiente não afete outros
		* **Segurança em banco de dados**
			* verificação de dados de entrada e codificação de saída
			* encerrar conexões assim que possível
			* eliminar estruturas e contas desnecessárias incluídas por padrão pelos distribuidores dos bancos
			* a aplicação deve se conectar ao banco com diferentes perfis de privilégio, de acordo com a necessidade específica
		* **Gerenciamento de arquivos**
			* autenticação deve ser necessária para carregamento de arquivos
			* limitar tipos de arquivos aceitos (! verificando a estrutura dos arquivos)
			* garantir que arquivos da aplicação possuem atributo de somente leitura
			* verificar existência de vírus e malwares em arquivos carregados por usuários 
		* **Gerenciamento de memória**
			* garantir que os buffers têm tamanho suficiente para as necessidades
			* ~ ver ataque Heart Bleed
			* liberar memória alocada de modo apropriado
		* **Práticas gerais de codificação**
			* evitar criar código novo para tarefas que já possuam código já desenvolvido e testado
			* proteger variáveis compartilhadas contra acesso concorrente inapropriado
			* instanciar explicitamente variáveis durante a declaração
			* não usar dados recebidos de usuário sem antes realizar tratamentos adequados
			* revisar aplicações de terceiro utilizadas, para avaliar vulnerabilidades/nível de segurança
	* todo::Ler o guia de referência para código seguro do OWASP [link](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)
* [OWASP Enterprise Security API (ESAPI) Project](https://owasp.org/www-project-enterprise-security-api/)
* OWASP Legal Project
* [OWASP Application Security Verification Standard (ASVS) Project](https://owasp.org/www-project-application-security-verification-standard/)