[ProvasDeTI](https://app.nutror.com/curso/d678643526569/aula/780589)
* abordagem de desenvolvimento de software, focando em design OO orientado a domínio, mais adequado para softwares complexos
* elementos fundamentais do DDD
	* Domínio = campo de ação/conhecimento, abstrato/intangível -> é o foco do DDD
	* Modelo do domínio = estrutura do conhecimento atual sobre o domínio -> não se reduz a diagramas! base da ==linguagem ubíqua==
	* Especialista do domínio = pessoas que conhecem profundamente detalhes do domínio (por quê, quando, como); importante boa comunicação entre dev e domain expert; normalmente envolve conjuntos de pessoas
* objetiva facilitar o controle da complexidade de um sistema, buscando evitar que o design fique demasiadamente complexo e incompreensível
* formas de trabalhar a linguagem ubíqua
	* modelagem em voz alta -> buscar expressar design/conceitos em frases coerentes
	* diagramas (DDD não recomenda algum diagrama específico)
	* documentação - desafio de manter documentação atualizada
* é importante que o código expresse os detalhes do domínio de forma clara e objetiva
	* Model-Driven Design (MDD) -> abordagem de modelagem de forma que ela possa ser melhor expressa em código
		* fornece estereótipos de objetos/artefatos que ajudam a representar em código o domínio -> objetivo { domínio fique isolado de outras responsabilidades, camadas bem separadas, separação de responsabilidades, arquitetura flexível }
			* Entities ~ entidade no OO
			* Value Objects -> ==não tem identidade para o domínio==; são reconhecidos por seus atributos (ex: cores, coordenadas, endereços)
			* Aggregates -> reúne entidades/objetos de valor que fazem sentido juntos no domínio -> tem uma raiz, que agrega os elementos
			* Services -> resolvem problemas de negócio, mas não são entidades ou objetos de valor; stateless
			* Factory -> segue padrão de design Factory para criação de objetos de domínio
			* Repository -> encapsulam a complexidade da persistência de dados; sem lógica de negócio
		* interface com o usuário - aplicação - domínio - infraestrutura (! arquitetura em camadas)
			* interface com o usuário -> não necessariamente usuário é pessoa, pode ser outro sistema
			* aplicação -> adapta as ações da camada de domínio aos diversos tipos de interface com o usuário; conversões, traduções, segurança etc
			* domínio -> coração do software
			* infraestrutura -> persistência, log, auditoria etc