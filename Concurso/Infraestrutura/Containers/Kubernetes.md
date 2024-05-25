* tool::**Kubernetes**:Ferramenta completa para orquestração de containers, atuando na implantação e gestão dos recursos dos containers
* **Características**
	* desenvolvido pelo Google, open-source
	* wrappers do Kubernetes (rodam ele por baixo): OpenShift e Rancher
	* auxilia na gestão de 
		* escalabilidade
		* balanceamento de carga
		* proxy reverso
		* service mesh (capacidade de os serviços se descobrirem)
	* benefícios
		* muita documentação na internet
		* agilidade no desenvolvimento de apps
		* adequado para DevOps
		* consistência de ambientes
		* isolamento
		* otimização de recursos
* **Arquitetura**
	* Kubernetes Nodes -> formam um cluster kubernetes
		* kubelet -> agent executado em cada nó, garantindo que cada container rode em um pod
		* kube-proxy -> mantém regras de network, relacionada à comunicação dos nós no cluster
	* kube-scheduler -> faz a seleção de nós para executar os pods (que podem executar um ou mais containers)
	* kube-api-server -> API do k8s
	* etcd -> metadados
	* kube-controller manager
	* cloud-controller manager
* **Namespace**
	* k8s -> 1...n clusters -> 1...n nós
	* é possível criar namespaces para isolar clusters (ex: namespace dev, namespace prod)
	* namespaces default { default, kube-system, kube-public }
		* default -> ~ sem namespace
		* kube-system -> reservado para objetos do k8s
		* kube-public -> reservado para objetos que devem ser acessíveis a todos os clusters
* **Service Discovery**
* **Load Balancer**
* **Deployment** -> por meio de configurações, é possível especificar a forma de deploy (ex: rollout, atualização de versões gradual etc)
	* forma declarativa para descrição de recursos dos seus pods
* **Fail handler**
	* **Health check** -> provê checagem de readiness e liveness #n_entendi 
		* live -> subiu
		* ready -> está pronta para atender requisições
* **Secrets** -> serve para manter dados sigilosos, como senhas
* **Pods** -> agrupamento de containers, permitindo que se comuniquem via HTTP como se fosse localhost
	* menor parte/objeto deployável em um k8s - basic execution unit
	* workload -> pods -> containers
	* **ciclo de vida** 
		* pending -> pod foi aceito pelo k8s, mas há pendências
		* running -> pod está em um nó em execução
		* succeeded -> todos containers do pod terminaram de executar com sucesso
		* failed -> todos containers do pod terminaram, mas existe pelo menos um que falhou
* **Controllers** -> controlam o estado do cluster
	* **CronJob** -> similar ao cronjob do Linux -> exemplo de cronjob.yaml
	* ![[Pasted image 20240426212601.png]]
	* **ReplicaSet** -> mantém um conjunto estável de réplicas de pod a fim de garantir disponibilidade
	* **DaemonSet** -> usado para pods que "provide a machine-level function, such as machine monitoring or machine logging"
* **Service** -> gerencia que serviços são acessíveis só na cloud e quais são acessíveis fora
	* ClusterIP -> expõe um serviço usando um IP interno -> acessível apenas dentro do cluster
	* Node Port -> vai expor com uma porta estática, acessível fora do cluster 
	* LoadBalancer -> necessário um provider externo de load balancing atrelado ao cluster (ex: Ingress) -> vantagem, roteamento criado dinamicamente
* **Volumes** -> para manter dados persistidos
* **Comandos**
	* kubectl get all -> lista os recursos em um namespace
	* kubectl get pods -> lista pods
	* kubectl apply -f arquivo.yaml -> deploya o arquivo.yaml
* **Outros orquestradores** { Docker Swarm + Portainer.io, OpenShift, Nomad, Mesos, CloudFoundry }
* **Outras ferramentas**
	* **Helm** -> baseado em YAML, serve para descrever serviços/objetos que vão rodar no k8s
* **Tips**:
	* containeres no mesmo pod compartilham IP


Aspectos de orquestradores
![[Pasted image 20240426145742.png]]