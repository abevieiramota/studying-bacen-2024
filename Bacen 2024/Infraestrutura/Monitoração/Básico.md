* **Tipos**
	* Análise estática de código fonte -> sintaxe, boas práticas etc
		* Lint tools -> ex { Find bugs, PMD, CheckStyle, ESLint, JSHint, JLint, Pylint }
		* Code coverage -> ex { Jacoco, }
	* Análise dinâmica -> 
		* tools { Grafana, Prometheus }
	* 
* **Tools**
	* **SonarQube** -> começou como integrador de Lints, mas evoluiu para um Sonar way
		* Issues { Bug, Vulnerabilty, Code smell }
			* Bug -> "*An issue that represents something wrong in the code. If this has not broken yet, it will, and will probably break at the worst possible moment. This needs to be fixed as soon as possible.*"
			* Vulnerability -> "*A security-related issue that represents a backdoor for attackers*"
			* Code smell -> "*A maintainability-related issue in the code. Leaving it as-is means that at best, developers maintaining the code will have a harder time than they should when making changes. At worst, they'll be so confused by the state of the code that they'll introduce additional errors as they make changes.*"
		* Severity { Blocker, Critical, Major, Minor, Info }
		* Quality profiles -> conjunto de regras verificadas
			* o SonarQube já vem com alguns profiles padrão e é possível estender eles, adicionando novas regras
		* Quality gates -> requisitos que definem se um projeto 'passa ou não'
	* **Prometheus**
		* aplicação envolve diversos componentes { código, servidor, banco, infraestrutura, SonarQube like etc } -> como saber se está tudo ok? servidor para monitoramento de tudo
		* open source
		* usa linguagem PromQL
		* é necessário que os serviços exponham uma API para o Prometheus acessar e coletar métricas
		* **Arquitetura**
			* Prometheus server
			* Prometheus web UI -> interface pobre, de forma que normalmente se usa Grafana
			* Alertmanager -> envio de alertas ex { slack, e-mail etc }
			* Pushgateway
			* Service discovery -> configurado no prometheus.yaml, informa o que monitorar
		* **Features**
			* 
	* **Grafana**
		* Web UI para visualização de dados
		* pode criar um dashboard ou usar dashboards já criados por terceiros
		* 