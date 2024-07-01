# Como fazer pesquisas - TPU - Histórico e panorama geral - 02/05/24

https://www.youtube.com/watch?v=q5x4ehYG__4

todo::ver guia de aplicação de tabelas de temporalidade, na página do pronome no CNJ ??olhei por cima, não entendi bem o sentido... há [palestra](https://www.youtube.com/watch?v=hDvn4aLxMmI)

!toda resolução mencionada, salvo se especificado, é do CNJ

* ~00:15: importância das TPUs
* ~17:30: apresentação dos participantes
* ~20:00: início da apresentação do Rubens
* ~23:00: início mesmo da apresentação do Rubens Curado
	* 2024, 20 anos de criação do CNJ
	* ~25:20: história das TPUs
		* essenciais para duas políticas importantes do CNJ -> { ==gestão estratégica e estatística==, implantação do PJe }
			* gestão estratégica e estatística
				* TPUs 'representam a forma como as informações processuais são organizadas, acessadas e compreendidas no ambiente digital'
				* padronização da linguagem dos sistemas processuais -> permitindo extração de dados padronizados, confiáveis e detalhados -> essencial para a gestão - não há gestão sem conhecimento
				* TPUs habilitam -> cultura de gestão por resultados, justiça em números etc
			* implantação do PJe
				* iniciativas para fomentar o processo eletrônico -> padronização de domínios web jus.br (res 41 e 45), TPUs (res 46), numeração única (res 63), doação de equipamentos de TI, divulgação de dados processuais na internet ([res 121](https://atos.cnj.jus.br/atos/detalhar/92)), nivelamento de TI (res 90 -> atualizado na [res 370](https://atos.cnj.jus.br/atos/detalhar/3706)), modelo de requisitos para sistemas informatizados (res 91), planejamento estratégico de ti (res 99), diretrizes para contratações de ti (res 182)
				* lei 11.419/2006 -> dispõe sobre a informatização do processo judicial
		* origem na [resolução 12, de 14/02/2006](https://atos.cnj.jus.br/atos/detalhar/206) -> define padrões de interoperabilidade, TPUs eram chamadas "tabelas básicas"
			* depois termo de cooperação técnica para desenvolvimento de uniformização taxonômica e terminológica { CNJ, CJF, TST, TJSP/MG/RS/ES/SE }
			* criado comitê técnico { jurídico, TI }
			* projeto -> TPUs, glossário, manual básico, padronização de cadastro de partes, projetos pilotos, acompanhamento e suporte à implantação, sistema de gestão compartilhada (atual SGT)
			* finalidade -> possibilitar extração de dados confiáveis para orientar gestão
			* objetivos alcançados -> { melhor reúso, pelos tribunais superiores, de informações dos sistemas de 1º e 2º graus; identificar estatísticas de duração das fases processuais; estatísticas de assuntos mais frequentes, para orientar atuação preventiva; melhor gestão de pautas temáticas; automatização de fluxos processuais; melhor controle de prevenção e distribuição processual }
		* [resolução 46, de 18/12/2007](https://atos.cnj.jus.br/atos/detalhar/167)
			* publicou o conteúdo das tabelas
			* definiu os órgãos destinatários e prazo de implantação
			* estipulou critérios de utilização e aperfeiçoamento
			* padronizou o cadastramento de partes
				* já havia previsão na lei 11.419/2006 de cadastramento com CPF/CNPJ -> atualmente alimentação diretamente da base de dados da Receita Federal
			* previu o acompanhamento da implantação
		* gestão das tabelas 
			* sistema eletrônico de gestão SGT
			* comitê gestor nacional
			* gestão compartilhada com todos os ramos da justiça
		* { STF foi o primeiro a implantar tabela de assuntos em 14/04/08, migrou 110k dos 130k processos em tramitação -> viu que 13 assuntos representavam 50% dos processos no acervo -> essencial à repercussão geral }
		* { 2009 -> apenas 10% dos processos em tramitação eram eletrônicos, 2022 -> +98% }
		* { outros projetos -> Justiça 4.0, juízo 100% digital }
		* capacidade atual de coleta de dados padronizados -> Datajud
* 43:00: início da apresentação do Marivaldo Dantas
	* ~TPUs permitem ver mais precisamente o acervo do judiciário (mas há limitações por conta da estrutura adotada -> não detalhou)
	* fala do problema de complementos não tabelados -> sem padronização, tribunais enviavam diversos conteúdos, alguns de baixa qualidade (em ~57:00 discute um pouco, quão mais detalhado -> mais custoso coletar/gerar a informação; em ~59:30 comenta sobre varas únicas, normalmente tem poucos servidores, menos capacitados -> quanto mais complexas as tabelas, mais difícil se tornam para serem usadas, gerando problemas de qualidade de dados especialmente para unidades com essas características -> quanto mais complexa a estrutura, maior a variabilidade dos 'modelos' -> menor a conformidade a um padrão geral, menor a capacidade de tirar conclusões gerais)
	* ~há o dilema entre tabela mais ou menas detalhada (principalmente assuntos e movimentos); ex: categoria de partes, no datajud usa só 4 categorias, apesar de na RFB ter muitas outras
	* ~resolução 12 meio que como carta de intenções para essa parte de tecnologia no judiciário
	* ~a tabela de movimentações tem como objetivo comunicar para a sociedade sobre a tramitação do processo (comenta sobre o "concluso", que ainda não é tão claro para a sociedade)
	* fomento do conhecimento do CNJ sobre o acervo do judiciário, do autoconhecimento dos próprios tribunais 
* 1:02:08: início da apresentação do Paulo Cristóvão Filho
	* importância para a gestão macro, do CNJ, mas também para a gestão micro, da Vara, como com movimentações de suspensão por não encontrar bens do devedor -> permite à Vara identificar quantos casos tem e direcionar ações
	* ~classe -> informa sobre o rito processual
	* interoperabilidade -> capacidade de comparar dados entre tribunais, dado o linguajar/glossário comum
	* fez pesquisa em tribunais de outros países e não achou trabalho tão avançado de taxonomia em produção
* 1:16:40: início da apresentação do Pedro -> servidor que trabalha com as TPUs no CNJ
	* início mesmo 1:18:50
	* objetivos -> { diferenciar { classe, assunto, movimento, documento }, conhecer as tabelas dessas entidades, como aplicar, conhecer a gestão das tabelas, o SGT e o manual de utilização das TPUs [[Manual_de_utilizacao_das_Tabelas_Processuais_Unificadas.pdf]] }
	* entidades
		* **classe**: se refere a como o pedido será processado no judiciário -> foco em direito processual
		* **assunto**: se refere ao objeto, o que é pedido
		* **movimento**: o que foi feito no processo -> foco em direito processual
		* **documento**: paralelo com movimento -> expedição (movimento) -> expedição de ofício -> o ofício é um documento, a expedição representa esse evento
	* SGT -> Sistema de Gestão e Atualização das Tabelas Processuais Unificadas, usado para fazer a gestão das tabelas pelo CNJ em conjunto com demais órgãos do judiciário
		* link do SGT: cnj.jus.br/sgt/consulta_publica_classes.php -> permite consultar as TPUs, com detalhes, como a que ramos de justiça a entidade se aplica, glossário, sendo do 2º grau, que movimenta (presidente, colegiado etc) etc
		* ~1:29:00: área restrita -> { gestor, colaborador, CNJ }
	* 1:29:55: **classe**
		* organizada de forma hierárquica, com 8 categorias raiz, em razão de competência específica, natureza ou matéria dos processos (que implicam em competências processuais)
		* tabela nacional e exaustiva -> órgãos não podem excluir/incluir novas classes sem autorização do Comitê Gestor das Tabelas Processuais Unificadas e Numeração Única
		* em caso de dúvida sobre a classe a ser adotada -> classificar como petição (deve ser autorizada por um superior, magistrado etc) e levar ao comitê para análise e deliberação, eventualmente solicitando criação de nova classe
	* 1:38:08: **assunto**
		* organizada de acordo com áreas do direito (exceção educação, saúde, temas de grande impacto/repercussão)
		* processo pode ter assuntos de diversos ramos (ex: o pedido tem assunto sobre a matéria, recebe recurso que tem assunto de matéria processual)
		* não podem ser assuntos de 1º ou 2º nível, a menos de assuntos finais de 2º nível
		* possível criar assuntos locais, mas abaixo no mínimo de algum assunto de 2º nível
		* ~2:03:10: é possível ver a partir de quando um assunto passou a ser válido, mas apenas nas planilhas que baixa no SGT -> mencionaram que é possível ver no PDPJ(?)
	* 1:43:20: **movimento**
		* dividido em magistrado { decisões, julgamentos, despachos } e serventuário { de acordo com a função do serventuário }
		* complementos { livre (obrigatório, domínio textual aberto), tabelado (domínio fornecido pela TPU), identificador (domínio é ID do sistema judicial) }
			* comentou dificuldade de trabalhar com complementos livres e identificadores
	* 1:46:30: **documento**
		* divididos em internos e externos, em categorias como ações processuais, elementos de prova, manifestações etc
	* cada tribunal tem responsáveis por analisar necessidades de ajustes nas TPUs, como inclusão - eles analisam, registram a solicitação na SGT, que é analisada -> passada por análise inicial, não sendo pedido repetido, já negado etc, vai para análise do comitê, que decide incluir ou não
	* 1:54:00: manual, desatualizado de 2014, mas ainda relevante, tem informações importantes e ainda válidas
* 1:56:00: retoma com a Ana, encerramento e perguntas
	* ~1:56:00: dúvida sobre temporalidade -> foi estabelecida com base em prazos de prescrição para exercícios de direitos -> menciona guia de aplicação de tabelas de temporalidade -> em página do proname no CNJ
	* ~2:01:00: temporalidade surgiu com o proname, depois da criação das TPUs


# Tabelas Processuais Unificadas e o impacto nas estatísticas do Poder Judiciário - 17/05/24

https://www.youtube.com/watch?v=n9KMzlzMpYg

todo::ver manual de uso da parametrização [link](https://www.cnj.jus.br/wp-content/uploads/2023/07/como-utilizar-parametrizacao-painel-de-estatisticas-do-poder-judiciario-versao-3-1.pdf)
todo:: ver página de parametrização de forma ampla [link](https://www.cnj.jus.br/sistemas/datajud/parametrizacao/)
todo::explorar [justiça em números - painel](https://paineis.cnj.jus.br/QvAJAXZfc/opendoc.htm?document=qvw_l%2FPainelCNJ.qvw&host=QVS%40neodimio03&anonymous=true&sheet=shResumoDespFT)
todo::o arquivo que pode ser baixado em [https://consulta-datajud.cnj.jus.br/](https://consulta-datajud.cnj.jus.br/) pode ser usado para validar dados enviados, não?
todo::estudar planilhas de regras

* ~15:00: alerta da Ana sobre a situação dos processos, que é calculada com base nos dados de TPUs dos processos fornecidos pelos tribunais - o tribunal não informa situação
* 16:55: início da apresentação da Isabely - situações processuais
	* 17:20: histórico do desenvolvimento de regras de situação
	* 20:00: começaram a trabalhar a classificação de processos com base nas TPUs pelas classes -> classificação em relação à fase processual -> grupos de procedimento
	* [Página sobre parametrização](https://www.cnj.jus.br/sistemas/datajud/parametrizacao/)
		* [planilha com parametrização (09/05/2024)](https://www.cnj.jus.br/wp-content/uploads/2024/05/parametrizacao-classes-todos-ramos-2024-04-2.xlsx)
	* parametrização é utilizada para classificações do Justiça em números
	* ~23:30: ! há flag indicando se a classe representa caso novo
	* ~25:00: recursos internos e tratamento como caso novo, tribunais que tratam de formas diferentes -> regras de recursos internos x caso novo tem peculiaridades
	* ~27:30: peculiaridades, como a de apelação cível 1035, que existe, não mais em uso etc
	* ~30:00: começaram a analisar regras com base em assuntos -> assuntos não são muito utilizados em parametrização (exceção em parametrizações da justiça eleitoral, que tem regras baseadas em assuntos)
	* ~31:30: situações
		* processo começa com distribuição, vem petições, agendamento/realização de audiências etc
		* há milhares de movimentos na TPU, mas nem todos eram relevantes para as estatísticas que estavam sendo analisadas
		* 35:27: foi criada parametrização de situações [link](https://www.cnj.jus.br/wp-content/uploads/2024/05/situacoes-datamart-validacao-2024-04.xlsx)
			* regras que associam movimentações a situações do processo (ex: situação Distribuído gerada pelo movimento de distribuição)
			* há situações que se iniciam e concluem com as movimentações associadas (apenas ocorrem, ex: distribuído), outras iniciam com certas movimentações/situações e concluem com outras (ex: pendente/tramitando)
			* as situações com 'início condicional' = Sim funcionam da seguinte forma (exemplo com pendente)
				* ao receber movimentação de Reativado, para verificar se a situação Pendente será iniciada, é preciso verificar se o processo já estava Pendente - em caso positivo, uma nova situação não é gerada
				* ou seja, o Reativado só inicia um Pendente caso não esteja Pendente (ex: reativação de processo baixado -> se baixado, não estava pendente, logo gera situação de pendente)
			* a coluna hierarquia agrupa situações em conjuntos maiores (ex: decisão proferida -> { denúnica/queixa recebida, rejeitada etc })
		* há aba 'Demais campos tabela situação' com regras mais específicas
	* 48:00: [painel de situações](https://justica-em-numeros.cnj.jus.br/painel-situacoes/)
* 1:00:10: início da apresentação do Igor - indicadores
	* 1:00:50: apresentação do arquivo que pode ser baixado na página de consulta do datajud ([https://consulta-datajud.cnj.jus.br/](https://consulta-datajud.cnj.jus.br/))
		* [planilha de indicadores](https://www.cnj.jus.br/wp-content/uploads/2024/05/indicadores-e-dicionario-dos-donwloads-painel-estatisticas-2014-04.xlsx)
			* contém variáveis do Datajud, mapeamento para variáveis do JN, nome, descrição e que situações representam a variável (ex: Caso Novo -> situação Pendente iniciada por Denúncia/queixa recebida, Distribuído etc)
			* tem variáveis sobre tempo, que geram muitas dúvidas
			* a aba 'Demais campos tabela fato' tem a descrição do domínio dos campos, como id_fase_processual
* ~1:22:00: início das dúvidas
* ~1:39:00: chave da tabela do datajud { tribunal, grau, procedimento, nº processo, recurso, órgão julgador }
* ~2:05:00: ~questão sobre baixa, júri etc


# Importância das TPUs no STJ e no STF - 06/06/24

https://www.youtube.com/watch?v=bgz0eOIzKJo



# Aplicação prática: o uso das Tabelas Processuais Unificadas - 13/06/24

https://www.youtube.com/watch?v=4Q43GnZdTcg



# O uso das Tabelas Processuais Unificadas

https://www.youtube.com/watch?v=C_W2CNKlvfg