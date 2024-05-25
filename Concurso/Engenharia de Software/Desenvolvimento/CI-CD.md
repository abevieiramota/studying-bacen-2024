* def::**CI - Integração Contínua**: integrar as cópias de trabalho de todos os desenvolvedores frequentemente + build automatizado + testes > descobrir problemas na integração o mais rápido o possível; estágio de criação e teste de unidade do processo de lançamento de software
	* **V**: 
		* maior produtividade dos dev
		* descoberta mais rápida de bugs
		* capacidade de entrega mais frequente
		* melhor colaboração da equipe
		* melhor integração do sistema
	* **Práticas**: 
		* sistema de controle de versão
		* testes automatizados
		* build automatizado
		* deploy automatizado
* def::**CD - Entrega Contínua**: produção de entregáveis em ciclos curtos, com entregas pequenas e frequentes
	* **V**: 
		* redução de custo
		* menor tempo e risco de alterações
		* atualizações incrementais
		* processo repetível
		* maior qualidade das entregas
		* maior produtividade dos devs
* CI/CD é recomendado pelo XP
* **Tools**:
	* tool::**Jenkins**: "*The leading open source automation server, Jenkins provides hundreds of plugins to support building, deploying and automating any project.*"
		* **Jenkinsfile**: arquivo de configuração de pipeline, sintaxe similar a groovy - com duas versões, declarativa e scripted; arquivo fica no repositório do projeto - Pipeline-as-code, é configurado como parte do código da aplicação;
			* ![[Pasted image 20240303074651.png]]
		* **Conceitos**:
			* **Pipeline**: define o processo de build, test e delivery
			* **Node**: máquina capaz de executar um pipeline
			* **Stage**: bloco de tasks - ex: build, test
			* **Step**: single task, diz o que o Jenkins deve fazer
		* **Links**:
			* [Installing](https://www.jenkins.io/doc/book/installing/)
	* tool::**CircleCI**: 
		* usa containers/VM
		* $
		* **Links**:
			* [Getting started](https://circleci.com/docs/getting-started/)
	* tool::**TravisCI**: 
		* suporta { github, assembla, bitbucket, gitlab }
		* **.travis.yml**: arquivo de configuração
			* ![[Pasted image 20240512144621.png]]
	* tool::**GitLab**:
		* **.gitlab-ci.yml**
			* ![[Pasted image 20240303074759.png]]
		* necessário ter runners