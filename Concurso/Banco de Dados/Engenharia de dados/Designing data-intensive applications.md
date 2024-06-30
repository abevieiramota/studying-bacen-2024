# Part 1 - Foundations of data systems

Trata de aspectos de sistemas de dados que se aplicam a todos esses sistemas, independente de rodarem em uma máquina apenas ou em clusters
## Chapter 1 - Reliable, Scalable and Maintainable applications

* **data-intensive x compute-intensive**:  de acordo com o parâmetro que determina majoritariamente o custo computacional -> data-intensive = volume de dados; compute-intensive = complexidade da computação
* data-intensive tasks tratam, de forma simplificada, principalmente das tarefas
	* storage
	* cache
	* search indexes
	* stream processing
	* batch processing
* abstração simplifica, mas é preciso entender as características das implementações para escolher ferramentas adequadas para o problema

### Thinking about data systems

* diferença entre ferramentas de 'data system' podem ser relevantes
* há ferramentas que não encaixam mais tão bem em 'data system' (ex: Kafka = mensageria + storage)
* há problemas que exigem combinação de ferramentas
* livro trata dos seguintes requisitos comuns a data systems
	* **reliability**: the system should continue to work *correctly* even in the face of *adversity*
		* *correctly*: performing the correct function at the desired level of performance
		* *adversity*: hardware or software faults, and even human error
	* **scalability**: as the system grows { data volume, traffic volume, complexity }, there should be reasonable ways of dealing with that growth
	* **maintainability**: over time, many different people will work on the system (maintaining + upgrading) and they should all be able to work on it *productively*

## Reliability

* def::**Reliability**: continuing to work correctly, even when things go wrong
* def::**Fault**: things that can go wrong -> **fault-tolerant**, system that anticipante and can cope with faults
	* fault -> desvio de parte do sistema em relação ao comportamento esperado/especificado
	* failure -> incapacidade de o sistema prestar o serviço para o usuário
	* fault-tolerant significa que o sistema possui mecanismos para lidar com faults, de forma que elas não gerem failures
* hardware faults
	* quanto maior a quantidade de máquinas do sistema, maior a probabilidade de faults ocorrerem
	* forma de lidar com hardware faults -> redundância
	* big data -> clusters -> maior taxa de hardware fault
* software errors
* human errors -> 'humans are known to be unreliable'
	* como criar sistemas seguros, num cenário de humanos não seguros? 
		* desenhar sistemas diminuindo espaço para erros -> ex: definindo domínios restritivos para inputs
		* testes extensivos
		* garantir recuperação rápida de erros, como ao realizar incrementos pequenos, ter ferramentas para recalcular dados/rollback etc
		* monitorar performance e taxas de erros (telemetria) -> métricas são importantes para prever ocorrência de falhas e diagnósticar falhas ocorridas
		* boas práticas de gestão e treinamentos
* reliability é importante em sistemas, mesmo os não críticos; há situações em que é sacrificada em benefício de outras características, como facilidade de desenvolvimento (ex: em prototipação), mas é preciso estar consciente desse sacrifício e o custo-benefício

## Scalability

* def::**Scalability**: capacidade de lidar com carga crescente, dentro de parâmetros de performance aceitáveis
* a carga de um sistema pode ser definida por parâmetros de carga, que devem ser selecionados de acordo com a arquitetura do sistema (ex: requests per second, ratio of reads to writes on a cache, número de usuários simultaneamente ativos em chat room etc)
* definidos parâmetros de carga, a avaliação de performance pode seguir dois caminhos
	* aumentada a carga e mantidos os recursos, qual o impacto na performance?
	* qual ajuste em recursos é necessário para manter a performance do sistema estável, dado um aumento na carga?
* latency x response time
	* response time = response moment - request moment (tempo entre a requisição e a resposta)
	* latency = response time - handling time (tempo que a requisição ficou 'latente', como o tempo de network etc)
* dado que um sistema normalmente lida com volumes grandes de requisições, é melhor tratar de distribuição de valores de performance, do que performances individuais
	* variações de performance podem decorrer de fatores diversos, como maior volume processado, perdas de pacotes de rede, garbage collector, hardware faults etc
	* tipicamente se reporta a média do tempo de resposta -> não informa quantos usuários/requests observaram esse valor de response time
	* mais interessante usar percentis { mediana (50th), p95, p99, p999 } (interessante relato de que na Amazon tendem a usar p999 e consideram que o usuário com requests mais lentas tende a ser aquele com maior volume de dados -> usuário com mais compras -> mais valioso)
	* quanto maior o percentil, mais custoso é para otimizar performance, porque vai sendo necessário lidar com fatores cada vez mais diversos e randômicos
* crescimento de carga -> necessidade de repensar arquitetura
	* scale up (máquina mais poderosa) x scale out (mais máquinas) = shared nothing
	* arquiteturas normalmente envolvem um mix de scale up/out
	* sistemas elásticos -> ajustam capacidade em reação a mudanças na carga
		* são interessantes quando há alta imprevisibilidade na carga
		* mas adicionam complexidade -> não havendo alta imprevisibilidade, ajuste de capacidade manual pode ser mais interessante
	* scale out com sistemas stateless é simples; com stateful é complexo (ex: databases)
	* arquiteturas para large scale normalmente são bem específicas -> processar 100k requests de 1kB cada X processar 3 requests de 2GB cada -> mesmo throughput, mas padrões diferentes de carga
	* "*An architecture that scales well for a particular application is built around assumptions of which operations will be common and which will be rare - the load parameters.*"

## Maintainability

* maior parte do custo de sistemas está na operação (e consequente manutenções), e não no desenvolvimento
* mesmo assim, ocorre muito de haver resistência a manter soluções 'legadas', por motivos diversos como { ter que corrigir erros de outros, trabalhar com ferramentas antigas, com gambiarras etc }
* def::**Maintainability**: capacidade de, de forma aceitável, { operar, entender, evoluir (extensibility/modifiability/plasticity) } o sistema
* operação -> inclui responsabilidades como
	* monitorar a saúde do sistema e restaurar o funcionamento em caso de mal funcionamento
	* diagnosticar causas de mal funcionamento
	* manter o sistema/plataforma atualizados
	* conhecer o relacionamento entre o sistema e suas dependências, de forma a previnir alterações nelas que causem problemas nele
	* antecipar problemas futuros e atuar de forma proativa (ex: aumento de demanda -> aumentar capacidade)
	* estabelecer boas práticas e criar ferramentas para operação, como deploy, gerenciamento de configuração etc
	* executar operações de manutenção (ex: mover aplicação para outro servidor)
	* manter a segurança do sistema, diante de alterações em configurações
	* definir processos de operação
	* preservar o conhecimento da organização sobre o sistema, diminuindo a dependência de pessoas específicas
* simplicidade
	* sintomas de alta complexidade
		* espaço de estados da aplicação grande
		* alto acoplamento entre módulos
		* dependências 'entrelaçadas'
		* nomenclaturas inconsistentes
		* gambiarras('hacks') para lidar com problemas de performance
		* lógicas de exceção para tratar situações pontuais apenas
	* def::**Complexidade acidental**: complexidade que não é inerente à solução do problema, mas que surge com uma implementação da solução
	* aumento de complexidade implica em (considerar que parte da complexidade é não essencial, é acidental)
		* diminuição de produtividade 
		* maior risco de introdução de bugs quando realizadas mudanças
		* maior risco de a solução ser entendida errada por mantenedores (ex: ter lógicas que dependem de premissas não explícitas, aumentando o risco de serem alteradas indevidamente, por desconhecimento dessas premissas por parte do mantenedor)
	* abstração (ex: criar interface que abstrai a implementação) é uma forma de reduzir complexidade (ex: SQL abstrai a implementação da execução); abstração com soluções distribuídas é desafiador
* extensibilidade -> capacidade de evoluir a solução de forma aceitável -> requisitos mudam com o tempo (ex: mudanças de prioridade, normas legais, mudança de plataforma etc), o que implica em necessidade de evolução da solução
* 




