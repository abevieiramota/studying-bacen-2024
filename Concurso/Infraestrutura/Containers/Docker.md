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
* **Comandos**
	* os comandos normalmente seguem a estrutura docker \<tipo de objeto\> \<operação\>, a exemplo de docker volume create e docker network create
	* docker pull hello-world -> verifica local, se não tiver, baixa do dockerhub
	* docker push -> envia para um registry
	* docker run hello-world
		* docker run -it alpine -> executa a imagem alpine de forma **i**nterativa e com **t**erminal
		* toda vez que dá um run numa imagem, um container é criado -> caso queira acessar o mesmo container, é preciso executá-lo especificamente, e não criar um novo com a mesma imagem
		* docker run --rm -> o container deve ser removido após a execução ser finalizada (evita ficar acumulando containers)
		* --name
		* -e -> variável de ambiente
	* docker ps -> apenas containers em execução
		* docker ps -a -> histórico, todos containeres
	* docker rm \<container id\> -> remove container
	* docker network create \<network id\> -> daí quando for subir um container, pode passar --network=\<network id\> e ele fará parte dessa rede, podendo se comunicar com outros containers nela (alternativa é usar docker-compose)
	* docker commit -> permite criar uma imagem a partir de um container (serve para versionar imagens)
	* docker build github.com/creack/docker-firefox -> clona o repositório e, usando ele e o Dockerfile na raiz do repositório, cria uma imagem
* **Exemplo de uso** -> rodar aplicação com nginx
	* docker pull nginx -> baixa a imagem do nginx
	* docker run nginx -> cria e executa container dessa imagem
	* docker ps -> dá para ver que o container está escutando a porta TCP/80, mas, ao acessar pelo browser, não há resposta
		* o nginx está escutando na porta 80 do container! é preciso mapear a porta 80 do host para a porta 80 do container
	* docker run -p 80:80 nginx -> a porta 80 do host deve ser mapeada para a porta 80 do container
		* para ficar mais clara a ordem, pensar no exemplo docker run -p 69:80 -> vai mapear a porta 69 do host para a porta 80 do container
	* /\\ executando dessa forma, o terminal irá ficar sendo utilizado pelo container -> para executar o container em modo daemon, adicionar -d
		* docker run -d -p 80:80 nginx
	* docker exec -it \<container id\> bash -> acessa terminal do container
		* no exemplo, alterou a index.html do nginx
		* o container mantém essas alterações -> se parar (stop) e iniciar novamente (start), as alterações são persistidas (mas apenas no container! ao instanciar um novo container com a mesma imagem, não tem as alterações)
	* formas de persistir alterações
		* 1 - não ideal: criar uma nova imagem a partir de um container (ou seja, instancia o container, configura/instala coisas e depois cria imagem a partir dele)
			* docker commit \<container id\> \<id da nova imagem\>
		* 2 - criar imagem com Dockerfile -> no exemplo, com nginx + vim + index.html alterado
			* Dockerfile
				* FROM nginx:latest -> herda da última imagem do nginx
				* RUN apt-get update -y (o -y é para já confirmar o comando!)
				* RUN apt-get install vim -y
				* COPY index.html /user/share/nginx/html/ -> copia o arquivo index.html, que está no diretório do Dockerfile, na pasta
			* docker build . -t \<imagem id\> (! executar no diretório em que está o Dockerfile)
		* 3 - com mapeamento de volume (associa um volume do host com um volume do container)
			* docker run -p 69:80 -v $(pwd):/usr/share/nginx/html nginx -> mapeia o current dir do host para /usr/share/nginx/html do container
			* dessa forma, basta alterar o arquivo no volume do host que isso será refletido no volume do container
* **Dockerfile** #anki 
	* FROM alpine:latest -> estende imagem
	* RUN sudo apt update-> executa comando !**no momento de criação da imagem** -> docker build
	* ENTRYPOINT \["dotnet", "DotNet.Docker.dll"\] -> programa a ser executado quando o container foi executado; só pode haver um (havendo mais de um, apenas o último é considerado)
	* CMD \["java", "OlaMundo"\] -> o indicado é ser usado para conter os parâmetros a serem passados para o programa declarado no ENTRYPOINT, mas parece que o povo usa para informar logo programa + parâmetros (como no exemplo); executa o comando !**em tempo de execução do container** -> docker run ! **atentar para a sintaxe, com colchetes**
	* ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk-> cria variável de ambiente
	* COPY \<arquivo no host\> \<path no container\>
		* COPY . . -> copia tudo do diretório do Dockerfile no host para o diretório padrão no container (que pode ser alterado com WORKDIR) (arquivos podem ser ignorados com o .dockerignore, como um .node_modules)
	* WORKDIR /app -> toda vez que executar container dessa imagem, usará esse diretório como padrão
* **Docker network**
* **Docker compose**
	* arquivo compose.yaml
	* permite configurar containers com um arquivo YAML, podendo versionar 
	* há seção 'services', em que serviços são declarados com nomes, que podem ser utilizados para acessá-los na rede
	* docker compose up
	* ![[Pasted image 20240426114052.png]]
* Features do kernel Linux que o Docker usa
	* cgroups -> serve para isolamento de CPU, memória, I/O -> recursos
	* namespaces -> permite fazer isolamento do ambiente do container -> cada container ter seu IP, monto de pontagem etc; namespaces { PID namespace, net namespace, mnt namespace, IPC namespace, user namespace }
		* PID namespace -> o PID dos processos no container vão ter PIDs específicos do container -> no host, o PID é outro
		* net namespace -> isolamento de interfaces de rede
		* mnt namespace -> isolamento de filesystem
		* IPC namespace -> isolamento de semáforos
		* user namespace -> isolamento de usuários
	* netlink
	* selinux
	* netfilter
	* capabilities
	* apparmor
* **Quando não usar Docker**
	* requisitos de alta velocidade
	* requisitos de alta segurança
	* aplicativos desktop GUI
	* dados valiosos aramzenados
	* quer facilidade de gerenciamento
* next_step::docker-compose




![[Pasted image 20240426144954.png]]