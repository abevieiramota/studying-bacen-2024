* o sistema de arquivos do Linux tem como raiz /, podendo incluir sistemas de arquivos encontrados em dispositivos diversos
* o comando **mount** serve para anexar à árvore com raiz / o sistema de arquivos de dispositivos
	* sem parâmetros -> mostra sistemas de arquivo montados
	* mount \<dispositivo com sistema a ser montado\> \<ponto de montagem\>
		* ex: mount /dev/sda3 /teste
			* ! o ponto de montagem deve existir!
		* o tipo de sistema de arquivos pode ser detectado automaticamente, ou informado com o parâmetro -t
			* ex: mount -t ext4 /dev/sda3 /teste
		* -o -> permite especificar opções, separadas por vírgula
			* ex: mount -o remount,rw,noexec /dev/sda3 /teste
			* opções
				* ro -> read-only
				* rw -> read-write
				* exec -> permite execução de binários
				* noexec -> não permite execução de binários
				* remount -> tenta remontar um sistema de arquivos já montado
	* umount -> desmonta o sistema de arquivos; não desmonta caso o sistema de arquivos esteja ocupado (com arquivo aberto etc)
* o ponto de montagem padrão é /mnt
* /etc/fstab -> sistemas de arquivos que podem ser montados
	* mount -a -> monta todos sistemas de arquivos no fstab
* /etc/mtab -> dispositivos montados com o mount