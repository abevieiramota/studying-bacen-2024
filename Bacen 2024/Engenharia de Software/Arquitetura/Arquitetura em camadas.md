* def::**Arquitetura em camadas**: organiza o sistema em camadas, que fornecem serviços à camada acima delas - níveis mais baixo comportam os principais serviços suscetíveis de serem usados em todo o sistema (Sommervile, p. 110)
	* **Quando usar**: desenvolvimento de recursos usando sistemas existentes; desenvolvimento com equipes por camada; requisito de proteção multinível;
	* **V**: favorece dev incremental; substituição de camada mais fácil, desde que a interface seja mantida; alteração de recurso físico mais fácil;
	* **DV**: dificuldade com manter uma separação rígida; perda de desempenho
	* def::**Cliente-magro**: tem apenas a camada de apresentação, mais fácil a instalação
	* def::**Cliente-gordo**: divide o processamento entre cliente e servidor, gerenciamento mais complexo
* def::**Arquitetura MVC**: separa a apresentação da interação dos dados do sistema, usando três componentes lógicos que interagem entre si: Modelo, que gerencia os dados e operações sobre eles; Visão, que define e gerencia a apresentação dos dados; e Controlador, que gerencia a interação do usuário, se comunicando com Visão e Modelo (Sommervile p. 109)
	* **Quando usar**: quando há diversas maneiras de apresentar/interagir com os dados e quando requisitos futuros de apresentação/interação são desconhecidos
	* **V**: independência na evolução das camadas Modelo e Visão, de apresentação; permite apresentar os mesmos dados de diversas maneiras
	* **DV**: overhead de código/complexidade quando dados/interação são simples

next_step::**Arquitetura PAC** (**P**resenter, **A**bstraction, **C**ontroller)
* ~parece MVC, comunicação entre agentes (?)

next_step::Estudar o capítulo 6 do Sommervile, em que apresenta diversos padrões de arquitetura