* **Motivações para ataque** { demonstração de poder, financeira, ideológica, comerciais }
* **Conceitos**
	* **Exploração do elo mais fraco**
	* **Vulnerabilidade**: condição que, quando explorada por um atacante, pode resultar em uma violação de segurança
	* **Exploit**: ferramenta desenvolvida para explorar uma vulnerabilidade específica
	* **Blue team x Red team**: profissionais de seg inf; blue -> defesa, red -> ataque
	* **Ethical hacker**
	* **Pentester**: profissional de segurança e de auditoria contratados para realizar testes e identificar falhas
	* **Scan**: varredura em redes
		* técnica usada antes de ataques, visando obter informações e identificar vulnerabilidades { versão de SO, apps, bibliotecas, portas abertas }
		* **Tools**: { NMAP }
	* **Computacionalmente seguro**: diz-se de solução que, considerando o poder computacional disponível, torna inviável um ataque por força bruta 
	* **Fuzzing**: envio de entradas com múltiplas variações para uma aplicação, com objetivo de identificar vulnerabilidades
	* **APT** - Ameaça Persistente Avançada: direcionamento de um ataque a determinada vítima de forma coordenada, com a utilização de diversas técnicas/recursos, geralmente organizado por times altamente coordenados
* **Atividades**
	* **Identificação de vulnerabilidades** -> com uso de ferramentas (exploits) e bases de conhecimento sobre vulnerabilidades existentes para as características do alvo
	* **Análise da estratégia** -> com as informações levantadas, criar plano para invasão, normalmente buscando explorar os elos mais fracos
	* **Aplicação do ataque** -> codificação e operação das ações
* **Pentest** -> teste de penetração
	* **Tipos**
		* **Blackbox**: parte de poucas informações; as principais portas de entrada são engenharia social e phishing
		* **Whitebox**: fornecem-se ao pentester informações básicas, como de rede, pulando a etapa de identificação; foco em verificar a robustez de configurações dos equipamentos e inexistência de exploits conhecidos a serem utilizados
		* **Greybox**: fornecem-se algumas informações de fácil obtenção e que não fazem parte do escopo do princípio da obscuridade
* anki::**STRIDE** -> modelo de ameaças; formato \<propriedade\> -> \<definição\>
	* **Spoofing**: autenticação -> personificar algo ou outra pessoa
	* **Tampering**: integridade -> modificar dados ou código
	* **Repudiation**: não repúdio -> alegar não ter realizado uma ação
	* **Information Disclosure**: confidencialidade -> expor informações a alguém não autorizado a vê-las
	* **Denial of Service**: disponibilidade -> negar ou degradar o serviço aos usuários
	* **Elevation of Privilege**: autorização -> obter recursos sem a autorização adequada
* **Tipos**
	* **Falsificação/Spoofing de e-mail**: adulteração de dados de identificação do e-mail, com a finalidade de { propagar códigos maliciosos, spam, phishing etc }
		* manipulação de campos do protocolo SMTP, como From, Reply-To e Return-Path
		* ex: atacante se passa por pessoa ou organização conhecida
	* **Man In The Middle (MITM)**: capacidade de o atacante se inserir no meio de uma comunicação
		* possivelmente envolve transformar a conexão original em duas (A -> B para A -> MITM -> B)
		* a captura pode ser utilizada para
			* repetir mensagens (ex: solicitação repetição de transferência bancária) -> mitigado com chaves dinâmicas de sessão #n_entendi 
			* modificar mensagens (ex: alterar o valor transferido) -> mitigação com uso de cálculos de verificação/funções hash (não impede alteração, mas permite identificação)
			* eliminar mensagens, violando disponibilidade -> mitigação com confirmação de recebimento
			* inspecionar mensagem -> mitigado usando criptografia
			* ! ver que os dois primeiros tipos não envolvem, necessariamente, quebra de confidencialidade, apenas de integridade
	* **ARP Spoofing / ARP Poisoning:** explora, no protocolo [[ARP#^def-protocolo-arp|ARP]], a dinâmica de ARP Request e ARP Reply, redirecionando o tráfego indevidamente
		* ARP Spoofing -> um host na rede responde (ARP Reply), indevidamente, um ARP Request indicando ser ele o host associado ao IP da request
		* ARP Poisoning -> adulteração de tabelas ARP
		* Tools: { CAIN&ABEL, }
	* **SMURF**: redirecionamento de tráfego por adulteração de endereço IP, objetivando atacar a disponibilidade de um serviço
		* atacante envia mensagem broadcast, adulterando o IP de from para o do serviço que quer que seja sobrecarregado (porque todos nós da rede responderão para ele)
	* **Sniffing**: interceptação de tráfego
		* não necessariamente sniffing é malicioso (pode ser feito por administradores de redes para detectar problemas, analisar desempenho, monitorar atividades maliciosas etc)
		* Tools: { Wireshark, TCPDump, }
	* **Força bruta**: busca esgotar as possibilidades, por tentativa e erro
		* poder de ataque é proporcional ao poder de processamento
		* podem ser utilizadas heurísticas para agilizar a busca
			* dicionário de termos frequentes
			* substituições óbvias de caracteres, como a -> @, o -> 0 etc
			* sequências numéricas de teclado, como 1234 ou qwert etc
			* informações pessoais
		* sobre senhas, cofres de senha são soluções para mitigar
	* **Defacement**: desfiguração de página web, com objetivos como { demonstração de poder, expor causa, vandalismo digital, }
		* exploram erros de app web, de servidores web, linguagem/libs web etc
	* **Phishing**: uso de páginas web clonadas com a finalidade de obtenção de informações privada
		* divulgação por meio de e-mail, whatsapp etc -> verificar a URL e garantir uso de certificados digitais para tentar evitar
		* **Spear Phishing**: phishing com alvo específico, como órgão de governo, empresa específica etc
	* **Pharming**: redirecionamento de um tráfego que iria para um site legítimo para outro
		* ! diferente de phishing, aqui o usuário está acessando o site correto, mas é redirecionado
		* pode ser feito por DNS Poisoning
	* **Negação de Serviço**: busca comprometer a disponibilidade do serviço, esgotando algum tipo de recurso do serviço, gerando indisponibilidade total ou intermitência/degradação de performance
		* pode ser realizado por envio de grande volume de requisições ou explorando falhas em algum componente do serviço
		* DDoS tem os mesmos princípios do DoS, porém é tratado de forma coordenada e distribuição, com computadores envolvidos de forma voluntária ou não (zumbis)
		* difícil de prevenir, o normal é agir de forma reativa
		* **Soluções**
			* usar soluções Anti DDoS para tentar identificar
			* entrar em contato com operadoras para bloquear tráfego
			* superestimar recursos de rede e recursos computacionais
			* uso de autoescaling com nuvem
			* estabelecimento de padrões de tráfego
			* identificar tráfego inválido e encaminhar para "buracros negros"
			* uso de CDNs, desonerando servidores do serviço
			* hardening
		* **DRDoS ou DDoS Refletor**: semelhante ao SMURF, enviam-se requisições com endereços forjados para usuários legítimos, de forma que eles respondam ao alvo do ataque
	* **SPIM (SPAM over Instant Message)**: envio em massa para propagar informação com finalidade maliciosa, usando serviços de mensagens instantânea (ex: envio de arquivo malicioso, ato de engenharia social)
	* **Engenharia Social**: exploração de relações sociais com o objetivo de descobrir informações privadas, de forma direta ou indireta (ex: descobrir informações de um funcionário de empresa para tentar obter mais informações da empresa)
		* **Vishing**: uso de sistema telefônic/chamada de voz para obter acesso às informações
		* **Phishing ou Spear Phishing**
		* **Hoax**: informação falsa divulgada em veículos de comunicação em massa, com isso conseguindo um grau de credibilidade baseada na popularidade da informação
		* **Whaling**: ataques altamente direcionados para ludibriar altos executivos - whale
	* **Ransomware**: sequestro de dados, por meio de criptografia dos dados, tornando eles inacessíveis sem a chave
		* como lidar: ou paga o resgate, ou (se tiver) usa backups que estejam funcionais (daí a necessidade de ter estratégias robustas de backups - ex: salvar em dispositivos offline)
	* **Malware**: malicous software
		* objetivos { roubar dados, roubar identidades, traçar perfis, gerar danos a hardwares/sistemas }
		* formas de infecção: 
			* exploração de vulnerabilidades de programas
			* execução automática de mídias removíveis infectadas, como pen-drive
			* acesso a páginas web maliciosas
			* ação direta de atacantes, invadindo computadores e inserindo códigos/programas maliciosos
		* **Tipos**
			* **Vírus**: código que pode ser um programa ou parte de um programa que tem a capacidade de gerar cópias de si/infectar outros programas
				* pode executar tarefas como deletar arquivos, instalar programas, reduzir configurações de segurança, esgotar recursos etc
				* depende de uma ação direta do usuário ou SO para executar/abrir o programa infectado
				* é possível estar inativo, podendo ser ativado posteriormente
				* propaga pela internet ou mídias removíveis
				* mitigável com desabilitação de execução automática
				* **tipos**
					* **vírus stealth**: usam-se técnicas para evitar a detecção
					* **vírus metamórfico/polimórfico**: usam-se técnicas para ocasionar alterações no seu código para dificultar a edição
					* **vírus de boot**: afeta o processo de boot, a MBR
					* **vírus de arquivo**: afetam arquivos de programas executáveis
					* **vírus residente**: carregado automaticamente em memória com o load do SO
					* **vírus propagado por e-mail**
					* **vírus de script/macro/telefone celular**
			* **Worm**: tem capacidade de se propagar pela rede enviando cópias de seu código, buscando explorar vulnerabilidades dos sistemas
				* pela propagação em rede, pode causar prejuízo nos recursos de redes
			* **Spyware**: foca na obtenção de informações de um host por meio de monitoramento de suas atividades
				* pode ser malicioso, daí malware, mas também pode ter finalidade legítima (ex: monitoramento de atividades em computador da empresa)
				* **keylogger**: monitora teclas digitadas; usa-se teclado virtual para evitar ataque por keylogger
				* **screenlogger**: armazena atividades da tela
				* **adware**: coleta de informações para direcionar propagandas
			* **Trojan Horse**: entra no SO escondido em outros programas (ex: programa divulgado para crackear outros programas, mas que contém código malicioso)
			* **Backdoor**: busca gerar meios para acesso futuro do atacante, como mantendo abertas portas
			* **Rootkit**: conjunto de programas e técnicas que permite esconder e assegurar a presença de um invasor ou de outro código malicioso em um computador comprometido, *conseguindo controlar o computador* -> o foco é na manutenção do acesso indevido + limpar rastros, não a invasão em si
				* operações { remoção de rastros, instalar malwares, mapear potenciais vulnerabilidades etc }
				* depende de uma invasão e de escalada de privilégios
				* tipos { kernel, virtual, firmware, library } rootkit (de acordo com que camada afeta)
			* **Bots e botnets**: programas que permitem a comunicação e controle do invasor sobre o sistema da vítima por acesso remoto
				* diferente de um rootkit, normalmente não gera dano ao computador afetado, normalmente sendo meio para outros ataques
				* pode ser mantido inerte até que o invasor dispare um comando
				* **botnet**: rede de bots/zumbis que permite realizar ataques em escala
			* **Bomba lógica**: programas que são disparados a partir de eventos específicos ou predefinidos (ex: contador, data específica etc)
	* **Ataques da camada de aplicação**:
		* **LFI/RFI** (Local File Insert, Remote File Insert): inserção de arquivo
			* **LFI**: burla controle de acesso, uso de passagem de parâmetros em requisições HTTP
			* **RFI**: usa um servidor comprometido para inserir arquivos em outro servidor alvo
		* **XSS - Cross-Site Scripting**: inserção de códigos/scripts em servidores Web, de forma que sejam executados pelos usuários do serviço Web
			* pode-se { sequestrar sessão de usuário, alterar código HTML no lado cliente, redirecionar usuários para sites maliciosos, capturar entradas de usuários }
		* **CSRF - Cross-Site Request Forgery** (também nomeado XRSF): a partir de uma ==sessão ativa== do usuário, busca-se forjar operações, como se fosse o usuário, nessa sessão
			* o atacante não precisa quebrar senha do usuário
			* uma proteção é o uso de CSRF Token
		* **SSRF - Server-Side Request Forgery**: similar ao CSRF, mas quem é afetado é o servidor, que irá fazer operações forjadas para outros servidores (lembrar de uma arquitetura de microsserviços, por exemplo, em que há diversos serviços se comunicando no back-end)
			* usuários, por não terem acesso ao back-end, não conseguem enxergar o problema
			* tendo acesso a serviços internos, que já possuem diversos acessos/autorizações internamente
		* **Clickjacking**: inclusão de elemento HTML invisível para o usuário, de forma que, ao usuário clicar no elemento visível, o click seja realizado sobre o elemento invisível
			* cabeçalho X-Frame-Options do HTTP orienta o browser sobre se pode ou não renderizar elementos como \<frame\> e \<embed\>
			* diferente do CSRF, depende de um click/botão
		* **SQL Injection**: permite que o atacante execute SQLs injetados no servidor, como drop table
		* **LDAP Injection**: similar o SQL Injection, mas atacando um servidor LDAP
		* **XML Injection**: por meio de XML, injeta comandos
		* **Zero Day Vulnerability**: janela entre a descoberta/exploração até a correção da vulnerabilidade
			* forma de lidar envolve avaliar comportamentos divergentes, com uso de ferramentas como [[IDS, IPS#^def-ips|IPS]]
		* **Buffer overflow**: ataque explora o uso de espaço em memória maior que o suportado, podendo gerar indisponibilidade ou expor dados protegidos
			* exemplo: heart bleed, ataque de buffer overflow no OpenSSL
		* 
* **Informações extras**
	* O Google Search é ferramenta útil para levantar informações sobre os sites, com isso podendo ser utilizado em busca de vulnerabilidades
		* [Google hacking database](https://www.exploit-db.com/google-hacking-database): base de consultas no Google para descobrir vulnerabilidades
	* 