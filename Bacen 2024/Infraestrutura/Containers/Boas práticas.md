* Multi-stage builds
	* ex: para aplicação Java, a imagem vai ter um estágio para compilar a aplicação, daí exigindo um Maven/Gradle; feito isso, move o binário para o outro estágio, que não vai ter Maven etc
	* ![[Pasted image 20240426215513.png]]
* Don't install unnecessary libs
	* ![[Pasted image 20240429141909.png]]
* Decouple applications -> cada container deve ser focado, ter apenas um aplicativo; isso facilita escalabilidade (ex: separar front e back em containers separados)
	* não tratar contêineres como VMs, que executam diversos serviços ao mesmo tempo -> contâiner pode funcionar assim, mas isso degrada vantagens do uso de containers
	* idealmente o ciclo de vida do container é igual ao ciclo de vida do app nele executado -> colocando mais de um app/serviço, pode ser o caso de terem ciclos de vida diferentes, que seriam melhor trabalhados cada um em container separado
* garantir que o aplicativo manipule sinais Linux corretamente
	* recomendado utilizar um sistema init especializado como o tini
* Minimize the number of layers
* Read only layers - executar containers com --read--only
* Ephemeral containers
	* capacidade de substituir containers de uma mesma imagem de forma fácil/simples
* Build images without dockerfiles
	* echo -e 'FROM '


![[Pasted image 20240429125731.png]]