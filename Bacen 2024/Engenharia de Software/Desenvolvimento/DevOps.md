[Provas de TI](https://provasdeti.nutror.com/curso/fdf12e5903ae53d6b83a53632bf346d2a6add378/aula/4178727)

* ! Cultura de engenharia de software que aproxima devs e ops melhorando comunicação/colaboração entre as partes e automatizando/monitorando as fases de construção de um software
	* Padronização de ciclo de desenvolvimento menores, maior freq de implantação, liberações mais seguras, colaboração, maior visibilidade, alinhamento, aprendizado contínuo
* DevOps = interseção { dev, ops, garantia de qualidade }
* **Práticas**
	* **CI - Integração contínua**: continuamente integrar o desenvolvimento de todo mundo da equipe -> importante ter um sistema de versionamento e repositório central; testes automatizados, avaliação de qualidade de código etc na integração
	* **CD - Entrega contínua**: o pipeline de criação de artefato de deploy automático e feito frequentemente, deploy fácil em produção
	* **Microsserviços**: menor acoplamento, maior coesão
	* **Infraestrutura como código**: versionamento do código de infraestrutura, testes, maior confiabilidade, maior facilidade de criação de ambientes
		* Tools { chef, ansible, terraform etc }
	* **Monitoramento e registros em log**: permite monitorar a infraestrutura em uso e atualizar a aplicação de acordo
		* you can't improve what you don't measure
	* **Automação** { CI/CD, test, containers, monitoração, infra as code }
	* **Infraestrutura imutável** -> "uma vez que a infraestrutura é provisionada, quaisquer mudanças necessárias são feitas por meio de um novo provisionamento de infraestrutura, e não alterando a infraestrutura atual. Ou seja, ao invés de modificar o ambiente existente, uma nova versão é construída e substitui a antiga. Isso evita inconsistências e problemas decorrentes de alterações ad hoc, promovendo uma abordagem mais controlada e previsível de gerenciamento de infraestrutura."
* **Pilares**
	* reduzir silos organizacionais
	* aceitar falhas
	* promover facilidade de mudança
	* promover automação
	* meça tudo
* **Benefícios**
	* maior integração/colaboração entre times de dev e de infra
	* maior facilidade de gerenciamento de ambientes de desenvolvimento
	* maior aderência entre os ambientes { dev, hml, prod } (menos o 'na minha máquina funciona')
	* velocidade na entrega > pipeline de deploy mais rápido e automatizado
	* maior escalabilidade
	* Faster Mean Time to Recovery (MTTR): diminuição para reparos no projeto
	* Higher Mean Time Between Failures (MTBF)
	* melhor segurança > maior automação da garantia de qualidade do código
* **Ciclo de vida do aplicativo** e como DevOps influencia
	* **Plan**: planejamento da infra, pipelines, gerenciamento de bugs, de práticas etc
	* **Develop**: otimização de pipelines e suporte de infra, sem sacrificar qualidade; automatização de testes, integração etc
	* **Deliver**: gerenciamento de implantação, configuração, infra, aumentando confiabilidade
	* **Operate**: monitoramento, manter disponibilidade, rápida correção, telemetria/alertas

![[Pasted image 20240427153442.png]]

* **Else**
	* shift left testing - testes feitos desde as fases iniciais do ciclo de vida do produto
	* a equipe de devops que é responsável por criação de scripts automatizados de entrega contínua etc
	* TOGAF (The Open Group Architecture Framework): framework que provê métodos e práticas para apoiar a criar, manter, usar, gerir e evoluir a arquitetura corporativa de uma empresa