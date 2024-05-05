* def::**SDL (Security Development Lifecycle)**: metodologia criada pela Microsoft para favorecer o Security by Design, aumentando o nível de segurança, que consiste na adição de uma série de atividades e produtos concentrados na segurança em cada fase do processo de desenvolvimento de software
	* Desenvolvimento de modelos de ameaças no desenho da solução
	* Uso de ferramentas de verificação de código de análise estática
	* Realização de revisões de código e testes de segurança durante um "esforço de segurança" direcionado
* def::**SD3+C**: Security by { [[Técnicas de desenvolvimento seguro#^def-security-by-design|Design]], [[Técnicas de desenvolvimento seguro#^def-security-by-default|Default]], [[Técnicas de desenvolvimento seguro#^def-security-by-deployment|Deployment]] } + Communication
	* Communication -> devem ser trabalhados canais/processos de comunicação para tratar de vulnerabilidades, envolvendo desenvolvedores, administradores, usuários
* **Fases**
	* **Treinamento** -> { redução de superfície de ataque, defesa em profundidade (ex: firewall, vpn etc), princípio do privilégio mínimo }, modelagem de ameaças, codificação segura (ex: estouro de buffer, sql injection, cross site scripting etc), testes de segurança (metodologia e automatização), privacidade-LGPD
	* **Requisitos** -> é feito levantamento dos requisitos de privacidade/segurança e análise de custo de impleementar esses requisitos; criar { portas de qualidade (quality gates -> como que um pipeline, só passa para frente se passar nas checagens anteriores), barras de defeitos (bug bars) } -> níveis mínimos aceitáveis de segurança; avaliação de riscos de privacidade/segurança
		* envolve um Supervisor de segurança, da equipe de segurança central
	* **Design** -> a partir de requisitos, análise de superfície de ataque da aplicação e produção de um modelo de ameaças da aplicação; 
	* **Implementação** -> programação defensiva/segura (evitando diversos ataques, como sql injection etc);  aderência a padrões de codificação; uso de ferramentas de análise estática de código; utilizar ferramentas aprovadas; depreciar funções inseguras
		* ! nessa fase, trabalha-se com [[DevSecOps#^def-sast|SAST]]
	* **Verificação** -> ~testes, inspeção/auditoria de configurações/código; teste de fuzz -> introduzir falhas no programa passando como input dados malformados/aleatórios; análise dinâmica -> comportamento em tempo de execução; revisão de superfície de ataque; 
		* ! nessa fase, trabalha-se com [[DevSecOps#^def-dast|DAST]]
	* **Liberação** -> disponibilização do produto para o usuário; produção de plano de ação para responder a incidentes!; revisão final de segurança; 
	* **Resposta** -> tratamento de incidentes; busca de problemas de segurança; 



![[Pasted image 20240323180455.png]]