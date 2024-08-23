# Part 1 - Foundations of data systems

Trata de aspectos de sistemas de dados que se aplicam a todos esses sistemas, independente de executarem em uma máquina apenas ou em clusters
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

### Reliability

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

### Scalability

* def::**Scalability**: capacidade de lidar com carga crescente, dentro de parâmetros de performance aceitáveis
* a carga de um sistema pode ser definida por parâmetros de carga, que devem ser selecionados de acordo com a arquitetura do sistema (ex: requests per second, ratio of reads to writes on a cache, número de usuários simultaneamente ativos em chat room etc)
* definidos parâmetros de carga, a avaliação de performance pode seguir dois caminhos
	* aumentada a carga e mantidos os recursos, qual o impacto na performance?
	* qual ajuste em recursos é necessário para manter a performance do sistema estável, dado um aumento na carga?
* latency x response time
	* response time = response moment - request moment (tempo entre a requisição e a resposta)
	* latency = response time - handling time (tempo que a requisição ficou 'latente', como o tempo de network etc, esperando ser trabalhada)
* dado que um sistema normalmente lida com volumes grandes de requisições, é melhor tratar de distribuição de valores de performance, do que de performances individuais
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

### Maintainability

* maior parte do custo de sistemas está na operação (e consequente manutenções), e não no desenvolvimento
* mesmo assim, ocorre muito de haver resistência a trabalhar com soluções 'legadas', por motivos diversos como { ter que corrigir erros de outros, trabalhar com ferramentas antigas, com gambiarras etc }
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


## Chapter 2 - Data models and query languages

* data models são muito importantes em sistemas por moldarem como o sistema vai ser desenvolvido, mas também como pensamos sobre o problema a ser resolvido
* sistemas são construídos empilhando camadas de data models - ex: modelo conceitual > modelo lógico > modelo físico > modelo elétrico etc; cada camada abstrai complexidade da camada inferior, permitindo que grupos diversos de pessoas trabalhem juntos com a "mesma" informação (ex: engenheiros na camada física, analistas de negócio na camada conceitual etc)
* data models carregam premissas sobre os dados representados -> como devem ser usados - ex: que operações podem ser realizadas, quais são rápidas etc
* dominar um data model pode ser difícil (ex: relational modeling), mas é importante conhecer diversos para decidir melhor qual aplicar a uma necessidade específica

### Relational model versus Document model

* o modelo relacional envolve organizar os dados em relations (tables no SQL), que são coleções não ordenadas de tuplas (rows no SQL)
* o modelo relacional é dominante e à época se sobressaiu, dentre outros motivos, por abstrair detalhes da representação interna dos dados, não exigindo que desenvolvedores pensassem sobre esses detalhes, simplificando o desenvolvimento

#### The birth of NoSQL

* já houve outras tentativas com modelos diferentes (ex: network/hierarchical) de superarem o relacional; a última é do movimento NoSQL, que surgiu como uma tag a ser usada para indicar uma conferência ocorrida em 2009, sobre bases não relacionais; atualmente é interpretado como Not Only SQL
* motivos que têm levado à adoção de modelos NoSQL
	* necessidade de escalabilidade, como com grandes volumes/throughput
	* priorização de open-source
	* necessidade de consultas especializadas não suportadas bem pelo modelo relacional
	* frustração com restrições do modelo relacional (ex: esquema rígido) e necessidade de modelos mais dinâmicos/expressivos

#### The object-relational mismatch

* muitas aplicações atualmente são desenvolvidas usando um modelo orientado a objetos -> surge a necessidade de traduzir os dados da aplicação, em modelo orientado a objeto, para o modelo relacional (impedance mismatch) -> foram criadas ferramentas ORM (Object-Relational Mapping), como ActiveRecord e Hibernate, para simplificar esse mapeamento
* p. 30: exemplo de modelagem de dados de cv do Linkedin, usando SQL, XML/JSON etc; comenta uma das vantagens de modelar dados como documento, ter melhor 'localidade' -> todos os dados do documento estão localizados juntos, podem ser recuperados numa chamada, enquanto em modelos SQLs pode ser necessário acessar diversas estruturas/tabelas

#### Many-to-One and Many-to-Many relationships

* vantagens de normalizar campo, ter ele em tabela de tipos, e não como free field { valor consistente, evitar ambiguidade, facilidade de atualização, suporte a localização, melhor search } + usar ID para identificar informação, ID não precisa mudar, pode ficar fixo, enquanto a informação/sua representação muda -> se a informação estiver duplicada, é preciso atualizar em todos locais, havendo risco de gerar inconsistências + carga de múltiplos updates
* dificuldade com modelo de documento -> se a representação for mantida no documento, atualizações na representação implicarão atualização nos diversos documentos etc + bancos document-based tendem a não ter boas funcionalidades para join

#### Are document databases repeating history?

* debate sobre como representar relacionamentos N x M é antigo -> comenta o caso do banco IMS, de ~1960, com modelagem hierárquica (registros dentro de registros) e que também modela mal relacionamentos N x M, assim como bancos orientados a documentos atualmente
* ~p. 36-37 discussão sobre soluções para N x M com modelo hierárquico/network e relacional -> vantagem do relacional é que o otimizador quem fica responsável por definir os 'access paths' para recuperar os dados

#### Relational versus document databases today

* há diferenças como tolerância a falhas e tratamento de concorrência (será tratado em capítulos posteriores) -> nesse, tratará apenas da modelagem dos dados
* document { schema flexibility, melhor performance por conta de localidade, menor impedance mismatch }
* relational { joins, N x 1, N x M }
* em relação a complexidade de código de aplicação -> se modela dados como documento, document-based db tende a exigir código mais simples
	* necessidade de join pode não ser problema -> ex: aplicação de analytics, não exige relacionamentos; se for necessário, é problema para doc based db
	* quão mais interconectado os dados, melhor seguir na escala \[ doc based, relational, graph based \]
* em relação a flexibilidade de esquema
	* sem esquema, não há garantias de que campos um registro irá conter
	* no lugar de schemaless (há um esquema), schema-on-read (esquema é conhecido apenas na leitura) x schema-on-write (esquema é enforced na escrita)
	* schema-on-read é vantajoso quando { há diversas estruturas possíveis e é difícil de montar um esquema só, a estrutura é determinada por fontes externas e o mantenedor da base não tem controle sobre ela e precisará se adaptar a mudanças }
* em relação a data locality
	* se o documento tende a ser acessado frequentemente em sua totalidade, essa modelagem é mais vantajosa que a relacional, porque evita ter que fazer lookups em tabelas para montar os dados 
	* updates em documentos pode ser pouco performático, por exigir reescrita de todo o documento

#### Query languages for data

* linguagem declarativa tem vantagem sobre imperativa por delegar responsabilidades de recuperação dos dados para o banco, que pode seguir estratégias diversas, de forma dinâmica, de acordo com o caso

#### MapReduce querying

* modelo de computação para processar em lote grandes volumes de dados usando diversas máquinas

### Graph-like data models

* dados estruturados em árvore -> documento model é adequado; alguns N x M -> relational é adequado; muito N x M -> graph based é adequado
* apresenta dois modelos { property model, triple-based }
	* property model: (A) -> (Property) -> (B)
	* triple based: (X, Y, Z) -> diferente do property, elementos não têm atributos
* exemplo de property model com postgresql p. 51
* mostra linguagem cypher, sparql, datalog p.52 a 62

## Chapter 3 - Storage and Retrieval

O capítulo trata de como os sistemas de dados armazenam e recuperam os dados -> é importante conhecer storage engines porque impactam no funcionamento de aplicações que usam sistemas de dados (ex: OLTP x OLAP)

### Data structures that power your database

* p. 70 -> apresenta um exemplo de sistema de dados mínimo, em bash, armazenando os dados em forma de KV em arquivo, append only, retornando sempre o último valor da chave
	* ignora diversas responsabilidades de sistemas robustos -> ex: { concorrência, recuperar disco não mais usado, recuperar de faltas etc }
	* performance ótima de insert, péssima de retrieve
* esse exemplo é log-based (log = append-only record)
* para melhorar retrieve -> index -> metadados que auxiliam encontrar dados armazenados -> implicam em overhead na escrita
	* tradeoff -> index melhora read, mas piora writes
	* por esse motivo, não se indexa tudo por padrão, deixando para o desenvolvedor escolher o que indexar, com base no seu conhecimento sobre o negócio/uso dos dados

#### Hash indexes

* Exemplo de hash index para storage em arquivo append-only -> manter em memória um hash map de valores em byte offset no arquivo para acessar o valor
	* apesar de simples, é estratégia adotada em alguns storage engine, como Bitcask, do Riak
	* estratégia adequada para quando há muitos writes (updates de valores), mas poucos valores distintos de chaves
* Como lidar com limite de tamanho de arquivo? Quebrar em segmentos, fechando o segmento quando chega no limite e iniciando um novo
	* no exemplo do append only file, ao fechar o segmento, pode-se aplicar uma 'compactação', eliminando K-V desatualizados
	* compactação pode tornar segmentos menores -> menor que o tamanho limite -> permite unir segmentos pequenos em segmento maior
	* esse esquema de compatação/união de segmentos pode ser feito em background, enquanto os segmentos antigos são utilizados para read/write -> switch depois de concluir a compactação/união
* Como estamos usando vários segmentos, no lugar de um arquivo apenas, cada segmento tem seu hash map de K -> offset
* Detalhes relevantes para essa abordagem append-only + hash map de K
	* file format -> CSV não é o melhor formato, melhor formato binário
	* deleting records -> sinalizar que a chave foi deletada com uma tag ("tombstone"), de forma que, na compactação/união, os demais registros dela sejam removidos
	* crash recovery -> restart do banco -> perde o in-memory hash
		* pode recuperar lendo todos os segmentos e reconstruindo o hash -> pode ser lento
		* Bitcask lida com isso salvando snapshots dos hashmaps em disco
	* partially written records -> um crash no meio de uma operação pode deixar escrita parcialmente realizada
		* Bitcask usa checksums para detectar partes corrompidas (?como?)
	* concurrency control -> uma solução é ter apenas uma thread para escrita e múltiplas para leitura
* Vantagens de append-only (por que não simplesmente ficar abrindo o arquivo e atualizando valores)
	* append/união são operações sequenciais, geralmente mais rápidas que operações com acesso randômico
	* recuperação de crash mais simples -> as operações alteram apenas valores novos, antigos são mantidos intactos, sendo sempre possível recuperar o valor antigo
	* merge/união de segmentos reduz segmentação
* Limitações
	* hashtables precisam caber em memória -> muitas keys pode ser problema; hash table on-disk é lento
	* não adequado para buscas em range -> a busca acaba envolvendo pesquisar cada chave pertencente ao range


#### SSTables and LSM-Trees

* O formato anterior, append-only, mantém registros ordenados de acordo com o momento de escrita -> mas essa ordem só é relevante para recuperar o mais recente de cada chave, à parte disso é irrelevante
* Uma alteração a essa estrutura -> manter registros ordenados por K -> Sorted String Table = SSTable
* Vantagens sobre append-only
	* merge de segmentos é simples e eficiente -> similar ao merge do mergesort, dado que estão ordenados
	* não é necessário manter hash de todas as chaves, mas apenas de parte delas -> se preciso achar uma chave, busco no hash chaves anteriores e posteriores a ela e busco nesse range
	* ?não entendi bem o ponto 3, de compactação dos segmentos de um range, economizando em espaço de disco/bandwidth -> não é necessário descomprimir a cada leitura/escrita?
* Como manter as chaves ordenadas? Há diversos algoritmos, como red-black trees, AVL trees etc
* p. 78 apresenta as operações para funcionar essa estrutura -> não captei todos os detalhes, como isso de manter a memtable e escrever em disco periodicamente, daí ter uma versão atual, uma antiga, compactar etc
	* mas entendi que mantém uma estrutura em memória ordenada e periodicamente escreve em disco + append only log para recuperar de crash
* LSM-Tree -> Log-Structured Merge-Tree; storage engines que usam esse princípio de merge/compacting sorted files -> LSM storage engines (ex: term dictionary no Lucene/elasticsearch)
	* essa estrutura é lenta em buscas por valores não presentes na base (vai na memória, depois em disco etc) -> usa-se bloom filter para verificar existência
	* há diferentes estratégias para determinar a ordem e momento de merge/compacting -> p.79 par. 4 tem detalhe
	* range queries (armazenamento sequencial) e escrita em disco são rápidos

#### B-Trees

* index mais usado, padrão em diversos bancos relacionais
* similar a SSTables, B-Trees mantêm K-V ordenados por K, mas divide a base em blocks/pages, geralmente de ~4KB, e lê/escreve uma página por vez -> a árvore é de blocos, cada bloco potencialmente referenciando outros blocos, com um bloco raiz
	* n_entendi::não entendi a diferença entre a abordagem com segmentos e com blocos...
	* branching factor -> número de referências a nós filhos por bloco
	* a inclusão de novos valores envolve achar o bloco/página em que ele deve ficar e lidar com o caso de estar lotado, dividindo em dois e atualizando referências
	* o algoritmo busca manter a árvore balanceada, com profundidade O(log n)
		* árvore com página de 4KB, branching factor 500 e altura 4 consegue armazenar 256 TB :O
	* escrita em disco altera arquivos -> LSM-Trees apenas appendam
* segurança das operações
	* escrita de novo valor pode exigir diversas operações, como dividir uma página em duas e atualizar referências -> o que é perigoso em caso de crash durante essas operações, risco de deixar páginas órfãos
	* para lidar com isso, usa-se um WAL, Write-Ahead Log/redo log, em que cada operação na B-Tree é registrada antes de ser aplicada na árvore
	* é preciso ter controle de concorrência para duas threads não enxergarem estados parciais, no meio de uma operação -> tipicamente usam-se lightweight locks
		* Log-structured approaches tendem a ser mais simples, porque fazem a alteração em background -> não entendi, por que não fazer assim com B-Tree?
* otimizações -> ver p. 80
* 









# Links interessantes

* [Como analisar latência](https://bravenewgeek.com/everything-you-know-about-latency-is-wrong/)