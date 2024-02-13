#lvl1
(Sommervile p. 109)
* Independência entre camadas, havendo dependência apenas de uma camada com sua camada inferior; independência -> evolução segura
* **Quando usar**: desenvolvimento de recursos usando sistemas existentes; desenvolvimento com equipes por camada; requisito de proteção multinível;
* **V**: favorece dev incremental; substituição de camada mais fácil; alteração de recurso físico mais fácil;
* **DV**: dificuldade com manter uma separação rígida; perda de desempenho
* cliente-magro (tem apenas a camada de apresentação, mais fácil a instalação) x cliente-gordo (divide o processamento entre cliente e servidor, gerenciamento mais complexo)


**Arquitetura MVC** (Sommervile p. 109)
* Separa a apresentação e a interação dos dados
* **Quando usar**: quando há diversas maneiras de apresentar/interagir com os dados e quando requisitos futuros de apresentação/interação são desconhecidos
* **V**: independência na evolução das camadas de modelo e de apresentação
* **DV**: overhead de código/complexidade quando dados/interação são simples

**Arquitetura PAC** (**P**resenter, **A**bstraction, **C**ontroller)
* ~parece MVC, comunicação entre agentes (?)