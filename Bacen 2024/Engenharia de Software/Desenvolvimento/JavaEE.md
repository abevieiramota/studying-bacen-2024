#TODO ler sobre RMI

* Servlet
	* A interface javax.servlet.Servlet define métodos que são acionados durante o ciclo de vida padrão do servlet. O método service() desta interface -> executa apenas se o init tiver concluído
		* #TODO ver interface de Servlet e documentação
* JPA
	* Anotações
		* @Entity: indica que a classe Java é uma entidade JPA.
		- @Table: especifica a tabela do banco de dados à qual a entidade é mapeada.
		- @Id: indica que um campo é a chave primária da entidade.
		- @GeneratedValue: especifica como a chave primária da entidade é gerada.
		- @Column: especifica a coluna do banco de dados à qual um campo é mapeado.
		- @Temporal: define o tipo de dados da coluna de data/hora no banco de dados.
		- @EmbeddedId: indica que uma classe incorporada é usada como chave primária da entidade.
		- @Embedded: especifica que uma classe deve ser mapeada como um tipo embutido em outra entidade.
		- @Transient: indica que um campo não deve ser mapeado para o banco de dados.
		- @Version: especifica o campo que deve ser usado para controlar a concorrência em transações.
		- @OneToMany: define uma associação "um-para-muitos" entre duas entidades.
		- @ManyToOne: define uma associação "muitos-para-um" entre duas entidades.
		- @OneToOne: define uma associação "um-para-um" entre duas entidades.
		- @JoinColumn: especifica a coluna na tabela do banco de dados que é usada para armazenar uma associação.
		- @NamedQueries: define uma ou mais consultas nomeadas.
		- @NamedQuery: define uma consulta nomeada.
		- @NamedNativeQuery: define uma consulta SQL nativa nomeada.
		- @NamedEntityGraph: define um gráfico de entidade nomeado.
		- @AttributeOverride: substitui as configurações padrão de mapeamento para um campo ou propriedade da entidade.
		- @AttributeOverrides: substitui as configurações padrão de mapeamento para vários campos ou propriedades da entidade.
		- @MappedSuperclass: permite que você crie uma classe Java que contém campos e métodos comuns que são compartilhados por várias entidades. Essa anotação indica que a classe Java é uma superclasse mapeada.
		- @Inheritance: permite que você especifique a estratégia de herança usada pela hierarquia de classes Java.
		- @DiscriminatorColumn: especifica a coluna usada para armazenar o tipo de entidade quando a estratégia de herança usada é a "single table".
		- @DiscriminatorValue: especifica o valor usado na coluna DiscriminatorColumn para identificar a entidade atual.
		- @ElementCollection: permite que você mapeie uma coleção de objetos embutidos ou básicos como uma entidade independente.
		- @OrderColumn: especifica uma coluna na tabela intermediária usada para representar a ordem dos elementos em uma associação "um-para-muitos" ou "muitos-para-muitos".
		- @OneToMany(mappedBy): especifica que uma coleção de objetos deve ser mapeada como uma associação "um-para-muitos" com outra entidade.
		- @ManyToMany: define uma associação "muitos-para-muitos" entre duas entidades.
		- @JoinTable: especifica a tabela intermediária usada para representar uma associação "muitos-para-muitos".
		- @JoinColumnOrFormula: permite que você especifique uma expressão SQL para mapear uma associação "um-para-um" ou "muitos-para