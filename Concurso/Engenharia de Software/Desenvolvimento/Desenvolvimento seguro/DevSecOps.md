* def::**DevSecOps**: integração da segurança nas diversas etapas, dev/ops/negócio, desde o início; segurança como responsabilidade compartilhada entre equipes de dev, ops e seg
* antes de devsecops > segurança adicionada após o ciclo de desenvolvimento
* **Benefícios**:
	* melhor colaboração entre equipes
	* economia ao evitar problemas de segurança
	* segurança proativa
	* rapidez nas correções de segurança
	* processo repetível e adaptativo
* **Práticas**:
	* integração de equipes de dev, ops e sec, com a participação de profissionais de segurança nas demais equipes
	* automatização de testes de segurança
	* monitoramento em tempo real de segurança
	* security by design
	* treinar dev e ops em segurança
	* mentalidade de que é processo contínuo
	* deve tratar { comunicação, pessoas, processos, tecnologia } - !não é só tecnologia
	* rastreabilidade: rastrear os itens de configuração em todo o ciclo de desenvolvimento
	* auditabilidade: controles/processos permitem auditoria (documentação, logs)
	* visibilidade: monitoramento, alertas
* **Tools**:
	* tool::**Nagios**: monitoramento de sistema e infra
	* tool::**OWASP ZAP**: teste de aplicativo web
	* tool::**SonarQube**: verificação de código
* **Testes de segurança**
	* def::**SAST (Static Application Security Testing)**: teste caixa branca, análise estática de código fonte ^def-sast
		* **V**:
			* baixo custo para múltiplas execuções
			* permite verificar aspectos de segurança em código sensível/que trata de dados confidenciais
			* capacidade de apontar precisamente onde no código há falha
		* **DV**:
			* capacidade limitada de identificação de falhas, dado que muitos ataques exploram falhas no contexto do funcionamento do sistema (aspectos dinâmicos)
			* alta taxa de falso-positivo
			* não explora bem vulnerabilidades relacionadas a configurações do software
		* Critérios para escolha de ferramenta { linguagem do código fonte, catálogo de vulnerabilidades analisadas, nível de acurácia/precisão, cobertura de bibliotecas/frameworks, suporte a CI, custos etc }
	* def::**DAST (Dynamic Application Security Testing)**: teste caixa preta, avalia o software em funcionamento, perspectiva do usuário/funcional/comportamental, simulação de invasor ^def-dast
		* **V**:
			* geralmente exige menor conhecimento técnico que SAST
			* pode testar sistemas já em produção
		* **DV**:
			* atuação tardia no ciclo de desenvolvimento -> é preciso ter aplicação executável
			* testa apenas impacto na fronteira da aplicação
	* def::**IAST** (Interactive Application Security Testing):  combinação dos dois -> usa agente que monitora a aplicação em tempo real, tendo acesso também às bibliotecas/frameworks usados
	* def::**RASP** (Runtime Application Self-Protection): tecnologia que protege uma aplicação de dentro para fora, analisando o comportamento do aplicativo e respondendo em tempo real a atividades potencialmente maliciosas

![[Pasted image 20240427155007.png]]

