* def::**GRASP** - **G**eneral **R**esponsibility **A**ssignment **S**oftware **P**atterns: design patterns, contendo 9 princípios de design de objetos
* **Information Expert**: atribuir responsabilidade por uma operação à classe que contém a maior quantidade de informação necessária para executar a operação
* **Creator**: atribuir a responsabilidade de instanciação de objeto A à classe que satisfaz um ou mais dos critérios { contém ou agrega instâncias de A, usa de forma específica A, tem informações para inicializar A }
* **Controller**: responsabilidade de lidar com system events fica com classe não UI, com lógica de caso de uso
* **Indirection**: a mediação entre dois elementos é feita por um objeto intermediário - exemplo MV**C**
* **Low Coupling**: baixo acomplamento = { quão forte os elementos estão conectados, têm informações um do outro, depende um do outro }; princípio para reduzir dependências entre classes, diminuir impacto em mudanças, aumentar reuso
* **High Cohesion**: objetos devem ser focados
* **Polymorphism**: a responsabilidade por mudança de comportamento é do tipo em que o comportamento muda
* n_entendi::**Protected Variations**: cria uma interface estável em torno de pontos de variação previsível/instabilidade
* study_more::**Pure Fabrication**: classe que não representa um conceito do domínio do problema, servindo apenas para conseguir baixo acoplamento, alta coesão e potencial de reuso

