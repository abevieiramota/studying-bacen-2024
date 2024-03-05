[Estratégia](https://www.estrategiaconcursos.com.br/app/dashboard/cursos/275777/aulas/2640897/videos/132944)
* rest tradicional -> retorna todo o objeto de um recurso, usando query param para indicar os campos a serem retornados
* rest tradicional -> endpoint por recurso -> se preciso de dados de vários recursos, uma chamada por recurso -> vários roundtrips, necessidade de conhecer diversos endpoints
	* com rest, resolve-se com BFF (Back-end For Front-end), componente de back-end que tem responsabilidade de prover dados para funcionalidades de front -> altamente orientado a interface
* graphql - padrão criado pelo facebook, concorrente do REST 
	* servidor graphql fica na frente dos serviços -> você faz requisição para ele e ele se vira para consultar os serviços e retornar os dados
	* envia estrutura dos dados que quer
	* SDL - Schema Definition Language (define o esquema dos dados e de como são solicitados)
	* Não está vinculado a nenhum BD, é query language, não é linguagem de programação!
	* a requisição é feita com POST (passa a consulta no body da requisição)
	* pode ser usado para API composition
* Rest x GraphQL
	* Rest + fácil, simples, suportado por diversas linguagens/frameworks, muito utilizado
	* GraphQL + otimização de payload, uma requisição para trazer vários dados, facilita trabalhar com múltiplos BDs, suportado por diversas linguagens
* tipos de campos
	* scalar - tipos primitivos (Int, Float, String, Boolean, )
	* object (referencia outro tipo)
	* query - interface para definir quais consultas podem ser realizadas; read-only, define endpoints para read
	* mutation - interface para escrita de dados, define endpoints para write
	* input - objeto a ser usado como parâmetro em mutation
	* enum - 
	* ![[Pasted image 20240303172319.png]]