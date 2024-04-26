* #TODO ver a documentação
* #TODO ver e documentar https://docs.docker.com/get-started/docker_cheatsheet.pdf
* #TODO https://labs.play-with-docker.com/
* ![[Pasted image 20240425215828.png]]
* **Motivação**: containers são autossuficientes (trabalha o problema do 'na minha máquina funciona'), ajuda a evitar cloud vendor lock-in, agilidade maior no deploy, maior portabilidade
* **Características**
	* desenvolvido em Golang
	* favorece isolamento (baixo acoplamento, controlável - ex; é possível fazer um container se comunicar com outro)
	* WORA - Write Once Run Anywhere -> portabilidade
	* leveza -> executa de forma nativa -> não precisa da estrutura de virtualização, como hypervisor, que implica em overhead
		* executa como um processo
	* trabalha de forma stateless
	* possibilidade de utilizar diversos containers numa só máquina
	* automação -> o dev desenvolve a app e a configuração do ambiente -> a união resulta num container
	* escalabilidade
* OCI - Open Container Initiative -> lembrar que Docker é um tipo de container
	* OCI busca promover especificações de runtime e containers (ex de runtimes: Apache Mesos, LXC, OpenVZ etc)
* **Conceitos**
	* **Docker image** -> similar a uma classe em POO -> especificação
		* imutável, read only
		* definida em estruturas de camadas; ex:
			* SO > JVM > app java
			* definido no Dockerfile
			* FROM openjdk:14
	* **Container** -> instância (em execução) de uma Docker image
		* gravável
		* wrapper do ambiente para executar a aplicação
		* gerenciado pelo Docker
		* base de pipelines CI/CD
	* **Service** -> quando preciso gerenciar diversos containers (ex: Docker Swarm, Kubernetes etc)
		* permite que o uso escalável e elástico de vários containers
	* **Registries** -> as imagens são binários -> é importante ter um repositório onde armazená-las/gerenciá-las
* **Docker Engine**
	* dockerd -> daemon de gerenciamento de containers
	* Docker CLI/API -> comunicação com o dockerd
* **Containerd overview**
	* Container execution -> create, start, stop, delete
	* Image management -> image push, image pull
	* Container filesystem -> volumes
* Comandos
	* docker pull hello-world -> verifica local, se não tiver, baixa do dockerhub
	* docker run hello-world
		* docker run -it alpine -> executa a imagem alpine de forma **i**nterativa e com **t**erminal
		* toda vez que dá um run numa imagem, um container é criado -> caso queira acessar o mesmo container, é preciso executá-lo especificamente, e não criar um novo com a mesma imagem
	* docker ps -> executando
		* docker ps -a -> histórico
	* docker rm \<container id\>
	* 