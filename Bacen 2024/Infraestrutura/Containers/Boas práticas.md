* Multi-stage builds
	* ex: para aplicação Java, a imagem vai ter um estágio para compilar a aplicação, daí exigindo um Maven/Gradle; feito isso, move o binário para o outro estágio, que não vai ter Maven etc
	* ![[Pasted image 20240426215513.png]]
* Don't install unnecessary libs
* Decouple applications -> cada container deve ser focado; isso facilita escalabilidade (ex: separar front e back em containers separados)
* Minimize the number of layers
* Read only layers
* Ephemeral containers
	* capacidade de substituir containers de uma mesma imagem de forma fácil/simples
* Build images without dockerfiles
	* echo -e 'FROM '