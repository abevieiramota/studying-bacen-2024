* **Princípios de Segurança da Informação**
	* **Confidencialidade** -> zelar pela privacidade e sigilo dos dados; acesso apenas por autorizados
	* **Integridade** -> garante-se que a informação gerada na origem é a mesma recebida no destino (dado em trânsito); a informação armazenada mantém-se inalterada (dado em repouso)
		* problemas de integridade não são apenas aqueles produzidos por entidades mal-intencionadas -> um ruído físico, por exemplo, pode comprometer a integridade
	* **Disponibilidade** -> a informação deve estar disponível sempre que **requisitada por usuário autorizado** (! para usuários não autorizados, não há o que se falar sobre disponibilidade)
	* **Autenticidade** -> garantia de que o sistema ou pessoa gerador da informação é, de fato, quem diz ser; problema atual do deep fake!
		* **Não-repúdio ou Irretratabilidade** -> derivado da autenticidade -> o gerador de uma informação não pode negar que gerou ela
			* trata tanto a origem (quem gerou não pode negar que gerou), mas também o destino (quem recebeu não pode negar que recebeu)
	* **Legalidade** -> a legislação vigente e normas relevantes devem ser respeitadas; ex { LGPD, normas da Febrabam para bancos, política de segurança interna etc }
* **Outros conceitos**
	* **Furto de dados** -> obtidos tanto por interceptação de tráfego, quanto por exploração de vulnerabilidades existentes em computador;
	* **Uso indevido de recursos** -> acesso não autorizado a computador e uso não autorizado (ex: propagação de malwares)
	* **Varredura** -> busca ampla sobre vulnerabilidades
	* **Interceptação de tráfego** -> coleta de dados em trânsito
	* **Exploração de vulnerabilidades**
	* **Ataque de negação de serviço** -> envio de grande volume de mensagens a um computador, tornando ele inoperante -> prejuízo na disponibilidade
	* **MIIM - Man In The Middle** -> entidade que está monitorando um canal de comunicação
	* **Ataque de Força Bruta** -> tentativa usando força bruta para acertar algum segredo
	* **Hardening** -> prática de diminuir vulnerabilidades, como desinstalar serviços não utilizados
* **Tipos de problemas**
	* **Ameaça** -> causa potencial de um incidente indesejado (ex: funcionário demitido pode tentar acessar e divulgar dados sigilosos)
	* **Risco** -> probabilidade de uma fonte de ameaça explorar uma vulnerabilidade, resultando em um impacto para a organização
	* **Vulnerabilidade** -> fragilidade de um ativo que pode ser explorada por uma ou mais ameaças (ex: ausência de política de expiração de acessos após demissão; ausência de gerador de energia)
	* **Impacto** -> resultado gerado por uma ameaça ao explorar uma vulnerabilidade
* **Segurança física** -> elementos tangíveis que apoiam e sustentam os princípios de segurança da informação; ex { trava, gerador de energia, token físico etc }
	* Unidade de Alimentação Ininterrupta (UPS) -> sistemas munidos de bateria capazes de armazenar energia e fornecer corrente elétrica aos demais equipamentos por um período limitado; ex: no-break, suprindo falta de energia (com baterias)
	* Gerador -> tem uma capacidade de abstecimento próprio, potencialmente pode manter o sistema funcionando por mais tempo que com um UPS
	* CFTV -> câmeras para registro e visualização dos ambientes de uma organização -> na maioria das vezes, o vídeo é gravado para, caso necessário, ser acessado posteriormente
	* Travas de equipamento -> impede o uso de dispositivos físicos, como trava que impede o uso de entrada USB
	* Alarmes -> tanto físicos, como de incêndio, como lógicos, como os IDS, que tratam de detecção de intrusos
	* Catracas -> uso de senhas, crachás, smartcards etc para restringir acesso a locais
	* Sala cofre -> ambiente seguro para datacenters, com controles de segurança, de acesso, mecanismos de reação a catástrofes etc
	* Site físico redundante -> outro ambiente que seja capaz de assumir a operação em caso de catástrofe no ambiente principal -> tem evoluído com o uso de nuvem
* **Segurança lógica** -> aspecto intangível que dis respeito à informação e fluxo dos dados { elementos da rede, a rede em si, sistemas/softwares }
* **Controle de acesso** -> estabelecimento de regras/bloqueios para acesso a { locais, equipamentos, serviços, dados }
	* diretamente associado a Autenticação e Autorização
	* geralmente organizado em camadas (ex: primeiro catraca de entrada, cartão para elevador, token para acesso à sala etc)
		* associado ao conceito de **defesa em profundidade**
	* **Formas**
		* **Mandatory Access Control** (MAC) -> o administrador do sistema é responsável por atribuir as devidas permissões para os usuários; associa labels aos usuários, que definem os acessos
			* acaba sendo mais simples de auditar, por ser mais centralizado e simplificado
		* **Discretionary Access Control** (DAC) -> mais flexível que o MAC, considera o usuário que necessita compartilhar o recurso com outros usuários; o próprio usuário refine regras de acessos aos recursos de que ele é dono
		* **Role-Based Access Control** (RBAC) -> controle baseado em papéis -> o administrador garante privilégios por papéis e atribui papéis aos usuários
* **Autenticação**
	* **Baseada em**
		* algo que você **sabe** -> ex { senha, resposta a pergunta de segurança etc }
		* algo que você **tem** -> ex { smartcard, token etc }
		* algo que você **é** -> ex { digital, íris, DNA, biometria etc }
	* AAA -> aspectos relevantes { Authentication, Authorization, Accountability/Accounting }
	* Autenticação forte -> conjugação de mecanismos de autenticação de forma encadeada (2FA ou MFA); normalmente, combinam-se duas técnicas, como algo que sei, senha, e algo que tenho, código enviado via SMS a celular
		* ! cuidado -> para ser 2 fatores é necessário mesclar fatores diferentes -> caso use íris + digital, não é múltiplos fatores, porque os dois métodos são baseados em algo que se é!
	* **Single Sign On (SSO)** -> permite o consumo de recursos de diversos sistemas/serviços a paritr de uma única camada de autenticação
		* compartilhamento de sessão -> ex: loguei no gmail, já posso usar calendar, drive etc
	* **Biometria** -> forma de identificar indivíduo unicamente por meio de suas características físicas ou comportamentais(!)
		* Impressão digital
		* Palma da mão
		* Imagem da face
		* Retina (fundo do olho), íris (anéis superficiais do olho)
		* Reconhecimento de voz
		* ! aspectos comportamentais incluem assinatura escrita digitalmente, voz etc, que levam em consideração não apenas o resultado, mas também o processo
		* **Características**
			* **Universalidade** -> em condições normais, todos possuem
			* **Singularidade** -> é diferente entre pessoas difernetes
			* **Permanência** -> a característica não varia com o tempo (ex: reconheicmento facial é menos usado com crianças, por mudar muito com o tempo)
			* **Mensurabilidade** -> a característica pode ser mensurada quantitativamente
* Como compartilhar recursos já existentes e reconhecer usuários de forma mútua e confiável { [[SAML]], [[OAuth]] }
	* SAML é mais antigo e está sendo substituído pelo OAuth
* 