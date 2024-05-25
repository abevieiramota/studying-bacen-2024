* def::**Git**: sistema de controle de versão distribuído
* **Características**:
	* suporte para desenvolvimento não linear, com branches/merges e movimentação nas versões
	* compatibilidade com protocolos diversos, como HTTP, FTP, rsync, protocolo próprio e SSH
	* manipulação eficiente de projetos extensos
	* autenticação criptográfica do histórico - o hash depende de todo o histórico até chegar nele
	* diversas ferramentas em shell
	* algoritmos de merge e identificação de conflitos
	* git armazena os objetos inteiros e empacota/comprime periodicamente, para otimizar espaço
	* Cada diretório de trabalho do git contém o histórico completo, não sendo necessário acesso a um servidor central
* **Comandos**:
	* git config --global user.name / user.email ""
	* git config --global merge.tool "ferramenta" > permite usar ferramenta externa de merge
	* git config --global core.editor "editor"
	* git init > inicializa repo
	* git log/status/clone/add/rm/checkout/fetch/pull
	* git reset - descarta tudo até o último push
	* git stash
	* next_step::ver mais a fundo os comandos do git

![[Pasted image 20240512141640.png]]