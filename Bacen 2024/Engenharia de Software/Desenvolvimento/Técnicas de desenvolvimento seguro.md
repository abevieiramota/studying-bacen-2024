[ProvasDeTI](https://provasdeti.nutror.com/curso/93ee181f34dea561421ed10f15614d24d58ce143)
* atributos essenciais de qualidade de um software { manutenibilidade, confiabilidade, eficiência, usabilidade }
* objetivos principais de explorações de vulnerabilidades { causar indisponibilidade, acesso indevido a dados, causar prejuízo à integridade dos dados }
* **STRIDE** -> acrônimo criado pela Microsoft para condensar perigos de segurança
	* **S**poofing (falsificação) -> falsificação de identidade de usuário
	* **T**ampering (adulteração)-> adulteração de integridade de informação/sistema
	* **R**epudiation -> negação de execução de ato cometido por um usuário
	* **I**nformation Disclosure -> divulgação indevida de informação
	* **D**enial of Service
	* **E**levention of Privilege -> dar privilégios indevidamente
* **Primitivas principais de SegInf**
	* **Disponibilidade** -> disponível para os usuários autorizados sempre que necessário (não precisa ficar 100% disponível, mas sim 100% do tempo em que foi necessário)
	* **Integridade** ->proteção contra modificações não autorizadas
	* **Confidencialidade** -> acesso apenas com autorização -> autenticação/autorização
* Diretrizes para software seguro
	* ter senha forte
	* atualizar aplicações
	* fuzzing -> envia entradas randômicas (com características que tendem a gerar falhas, como uso de caracteres não visuais), para identificar falhas
	* documentação
	* validação de entradas
	* tratatamento de erros na aplicação + evitar deixar vazar mensagens de debug para usuário (pode fornecer informações úteis para explorar vulnerabilidades)
* **SDL** - Security Development Lifecycle
	* abordagem pioneira para tratar software e infra de forma segura, apoiada pela Microsoft
	* envolve a adição de atividades e produtos ao desenvolvimento com objetivo de aumentar o nível de segurança (isso ajuda a reduzir custo!) -> reduzindo falhas, reduzindo a gravidade de defeitos
	* **SD3+C**
		* Security by { Design, Default, Deployment } + Communication
	* **Fases**
		* ![[Pasted image 20240323180455.png]]
		* **Treinamento** -> { redução de superfície de ataque, defesa em profundidade (ex: firewall, vpn etc), princípio do privilégio mínimo }, modelagem de ameaças, codificação segura (ex: estouro de buffer, sql injection, cross site scripting etc), testes de segurança (metodologia e automatização), privacidade-LGPD
		* **Requisitos** -> é feito levantamento dos requisitos de privacidade/segurança e análise de custo de impleementar esses requisitos; criar { portas de qualidade (quality gates -> como que um pipeline, só passa para frente se passar nas checagens anteriores), barras de defeitos (bug bars) } -> níveis mínimos aceitáveis de segurança; avaliação de riscos de privacidade/segurança
		* **Design** -> a partir de requisitos, análise de superfície de ataque da aplicação e se produz um modelo de ameaças da aplicação; 
		* **Implementação** -> programação defensiva/segura (evitando diversos ataques, como sql injection etc);  aderência a padrões de codificação; uso de ferramentas de análise estática de código; utilizar ferramentas aprovadas; depreciar funções inseguras
		* **Verificação** -> 
		* **Liberação** ->
		* **Resposta** -> 