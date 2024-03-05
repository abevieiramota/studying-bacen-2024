#lvl1

[Provas de TI](https://provasdeti.nutror.com/curso/dd94be62f09d32cc8654aa458d27b8b2a1183cd8/aula/6417229)

* CI - integrar as cópias de trabalho de todos os desenvolvedores frequentemente + build automatizado + testes > descobrir problemas na integração o mais rápido o possível; estágio de criação e teste de unidade do processo de lançamento de software
	* Benefícios { produtividade dos dev, descoberta mais rápida de bugs, capacidade de entrega mais frequente, melhor colaboração da equipe, melhor integração do sistema }
	* Práticas { sistema de controle de versão, testes automatizados, build automatizado, deploy automatizado }
* CD - produção de entregáveis em ciclos curtos, com entregas pequenas e frequentes
	* Benefícios { redução de custo, tempo e risco de alterações, atualizações incrementais, processo repetível, maior qualidade das entregas, produtividade dos devs }
* Estágios típicos de pipeline CI/CD
	* Compilação > Teste > Lançamento (envio da aplicação para repositório) > Implantação (deploy) > Validação
* CI/CD é recomendado pelo XP

**Tools** #TODO overview + arquivos de configuração (ver hello world das ferramentas)
* Jenkins - "*The leading open source automation server, Jenkins provides hundreds of plugins to support building, deploying and automating any project.*"
	* Jenkinsfile - arquivo de configuração de pipeline, sintaxe similar a groovy - com duas versões, declarativa e scripted; arquivo fica no repositório do projeto - Pipeline-as-code, é configurado como parte do código da aplicação;
		* ![[Pasted image 20240303074651.png]]
	* CD - gerar software a partir do source code
	* Conceitos
		* Pipeline - define o processo de build, test e delivery
		* Node - máquina capaz de executar um pipeline
		* Stage - bloco de tasks - ex: build, test
		* Step - single task, diz o que o Jenkins deve fazer
* CircleCI
	* usa containers/VM
	* $
* TravisCI - github, assembla, bitbucket, gitlab
	* .travis.yml -> arquivo de configuração
	* build - grupo de jobs (como testar com versões diferentes do java)
	* stage - grupo de jobs que rodam em paralelo
	* job - processo de clonar repositório e executar uma série de phases, como compilar, testar etc
	* phase - sequência de steps
* GitLab
	* .gitlab-ci.yml
		* ![[Pasted image 20240303074759.png]]
	* necessário ter runners