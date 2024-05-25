* def::**DevOps**: cultura de Engenharia de Software que aproxima devs e ops melhorando comunicação/colaboração entre as partes e automatizando/monitorando as fases de construção de um software
* def::**DevOps**: interseção { dev, ops, garantia de qualidade }
* **Práticas**:
	* [[CI-CD]]
	* [[Microsserviços]]: menor acoplamento, maior coesão
	* [[Infraestrutura as code]]: versionamento do código de infraestrutura, testes, maior confiabilidade, maior facilidade de criação de ambientes
	* [[Monitoração]]: permite monitorar a infraestrutura em uso e atualizar a aplicação de acordo
	* **Automação**: { CI/CD, test, containers, monitoração, infra as code }
	* def::**Infraestrutura imutável**: "*uma vez que a infraestrutura é provisionada, quaisquer mudanças necessárias são feitas por meio de um novo provisionamento de infraestrutura, e não alterando a infraestrutura atual. Ou seja, ao invés de modificar o ambiente existente, uma nova versão é construída e substitui a antiga. Isso evita inconsistências e problemas decorrentes de alterações ad hoc, promovendo uma abordagem mais controlada e previsível de gerenciamento de infraestrutura.*"
	* def::**Shift left testing**: testes feitos desde as fases iniciais do ciclo de vida do produto
* **Pilares**:
	* reduzir silos organizacionais
	* aceitar falhas
	* promover facilidade de mudança
	* promover automação
	* meça tudo
* **V**:
	* maior integração/colaboração entre times de dev e de infra
	* maior facilidade de gerenciamento de ambientes de desenvolvimento
	* maior ==aderência== entre os ambientes { dev, hml, prod } (menos o 'na minha máquina funciona')
	* velocidade na entrega > pipeline de deploy mais rápido e automatizado
	* maior escalabilidade
	* def::**Faster Mean Time to Recovery** (MTTR): diminuição do tempo necessário para reparos no projeto
	* def::**Higher Mean Time Between Failures** (MTBF): maior espaçamento entre falhas
	* melhor segurança > maior automação da garantia de qualidade do código
* **Ciclo de vida do aplicativo** e como DevOps influencia:
	* **Plan**: planejamento da infra, pipelines, gerenciamento de bugs, de práticas etc
	* **Develop**: otimização de pipelines e suporte de infra, sem sacrificar qualidade; automatização de testes, integração etc
	* **Deliver**: gerenciamento de implantação, configuração, infra, aumentando confiabilidade
	* **Operate**: monitoramento, manter disponibilidade, rápida correção, telemetria/alertas
* **Informações relacionadas:**
	* def::**TOGAF** (The Open Group Architecture Framework): framework que provê métodos e práticas para apoiar a criar, manter, usar, gerir e evoluir a arquitetura corporativa de uma empresa