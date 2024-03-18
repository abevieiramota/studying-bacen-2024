[Provas de TI](https://app.nutror.com/curso/d6ea453772c03556da8f99d79db84f373f70937f/aula/5262298)
* motivação -> integração entre diversos sistemas, com tecnologias/plataformas/etc distintas -> interoperabilidade (capacidade de integrar partes, de forma que possam operar juntas)
* soluções desenvolvidas para tratar esse problema
	* file transfer
		* aplicações escrevem dados em arquivos compartilhados, que são lidos por outras aplicações
		* arquivo é objeto 'universal', normalmente as plataformas conseguem manipular -> usando formato comum
		* V: simples
		* DV
			* sem padrão para nomes/formatos de arquivos (deve ser combinado entre as aplicações
			* necessidade de controlar a concorrência de escrita/leitura
			* necessidade de manter manualmente consistência de dados persistidos em arquivos diferentes
	* shared database
		* aplicações escrevem num banco de dados compartilhado
		* controle transacional para leituras/escritas concorrentes
		* V: { menor acoplamento, controle de concorrência pelo banco }
		* DV: { dificuldade de atender a todos usos simultaneamente, gargalo pela concorrência de consumo }
	* remote procedure invocation (RPC)
		* aplicações expõem funções para outras aplicações invocarem remotamente
		* V: { encapsulamento/menor acoplamento (sem recurso compartilhado), }
		* DV: { acoplamento pelas interfaces, acesso remoto, manutenção de diversas APIs }
	* uso de APIs
		* limitação da abordagem via API -> client-server, é necessário que o client solicite ao servidor (~pooling)
	* mensageria
		* criam pacotes de dados que são enviados a canais, responsáveis pela entrega dos pacotes a sistemas interessados
		* assíncrono (sem necessidade das partes estarem disponíveis durante a comunicação) (ex: o Whatsapp funciona assim)
		* DV: { necessidade de compreender a tecnologia de mensageria, formatação de dados, }
	* **componentes**
		* **canal** - mensagens são enviadas a um canal; para recuperar as mensagens dele, é necessário conhecer esse canal (ter o nome, ID)
			* ~ tem endereço lógico
			* existem diversos esquemas de ordenação da entrega das mensagens (na ordem que chegou, por tamanho etc)
			* necessário definir política de retenção, de envio, políticas de retentativa em caso de falha, protocolos etc
			* arquiteturas
				* **ponto-a-ponto** - a mensagem é destinada a um receptor específico
				* **requisição-resposta** - mensagem é enviada e uma resposta do receptor é aguardada
				* **publish-subscribe**
					* publicadores: produtores de conteúdo
					* assinantes: consumidores de conteúdo
					* mensagens são enviados para tópicos, que são assinados por consumidores, que irão receber essas mensagens
					* os publicadores não precisam saber sobre os assinantes
					* proporciona baixo acoplamento entre os agentes
			* 