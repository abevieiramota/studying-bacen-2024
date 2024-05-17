* def::**Graphql**: padrão criado pelo facebook, concorrente do REST 
	* servidor Graphql fica na frente dos serviços -> você faz requisição para ele e ele se vira para consultar os serviços e retornar os dados
	* envia estrutura dos dados que quer
	* SDL - Schema Definition Language (define o esquema dos dados e de como são solicitados)
	* !não está vinculado a nenhum BD, é query language, não é linguagem de programação!
	* a requisição é feita com POST (passa a consulta no body da requisição)
	* pode ser usado para API composition
* Rest x GraphQL:
	* Rest: + fácil, simples, suportado por diversas linguagens/frameworks, muito utilizado
		* por padrão, retorna todo o objeto de um recurso, usando query param para delimitar campos a serem retornados
		* um endpoint por recurso -> em caso de necessidade de vários recursos, uma chamada por recurso, várias roundtrips, necessidade de conhecer diversos endpoints -> BFF (Back-end For Front-end) componente de back-end que tem responsabilidade de prover dados para funcionalidades de front
	* GraphQL: + otimização de payload, uma requisição para trazer vários dados, facilita trabalhar com múltiplos BDs, suportado por diversas linguagens
* **Tipos de campos**:
	* scalar - tipos primitivos (Int, Float, String, Boolean, )
	* object (referencia outro tipo)
	* query - interface para definir quais consultas podem ser realizadas; read-only, define endpoints para read
	* mutation - interface para escrita de dados, define endpoints para write
	* input - objeto a ser usado como parâmetro em mutation
	* enum - 
	* ![[Pasted image 20240303172319.png]]