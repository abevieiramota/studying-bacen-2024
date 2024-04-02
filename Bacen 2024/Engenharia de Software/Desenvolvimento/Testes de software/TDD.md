[TDD](https://app.nutror.com/curso/d678643526569/aula/457120)

* ciclo de vida: red green refactoring + baby steps
* mock: simulam o comportamento de objetos reais, usado quando é difícil a aplicação de testes triviais (como quando exige integração com outros componentes)
* ATDD - Accepctance TDD: envolve a participação de equipe, PO etc, diferente do TDD, mais focado no dev


[JUnit](https://app.nutror.com/curso/a4445f052c3ea49133006f6d10949a53a98bfa46/aula/7064550) #TODO cheat-sheet

* framework para facilitar o dev e automação de testes em java
* baseada em anotações, se o método é de teste, se deve ser executado antes/depois
* JUnit 5 = JUnit Platform (core do JUnit 5) + JUnit Jupiter (testes baseados em Jupiter) + JUnit Vintage (testes usando JUnit 3 e 4 - retrocompatibilidade)
* incluir o junit.jar no classpath - também vem já configurado em IDEs como Eclipse, NetBeans etc
* em org.junit.jupiter.api
	* @Test (não tem atributos!), @ParameterizedTest (o método tem argumentos e define-se um @ValueSource), @RepeatedTest (modelo de teste para testes repetidos N vezes), @TestFactory (fábrica de testes para testes dinâmicos), @TestTemplate (template para testes), @TestMethodOrder (configura a ordem de execução dos métodos - se não tiver, o JUnit quem define a ordem; anotação de classe, daí anota os métodos com @Order(n)), @TestInstance (configura o ciclo de vida da classe de teste), @DisplayName (define o nome de exibição para a classe/método), @DisplayNameGeneration (gerador de nome), @BeforeEach (executado antes de cada um dos métodos - setup), @AfterEach (executado após cada um dos métodos), @BeforeAll (executado antes de todos métodos), @AfterAll (executado depois de todos), @Nested (classe anotada é classe aninhado), @Tag (usado em filtragens de testes; não pode ser nula/branca, não pode conter espaços em branco; sem palavras reservados), @Disabled, @Timeout (falha o teste se exceder tempo; unidade padrão = s, pode alterar com o atributo unit = TimeUnit.MILLISECONDS, ex)
* asserções org.junit.jupiter.api.Assertions (métodos estáticos)
	* compara resultado com esperado e pode receber mensagem caso falso
	* assertTrue(boolean), assertTrue(boolean, msg), assertTrue(boolean, messageSuplier), assertFalse
	* assertSame, assertNotSame (verifica se é o mesmo objeto)
	* assertEquals(expected, actual), assertEquals(expected, actual, tolerance/delta)
	* assertNull, assertNotNull
* asserções de terceiros: hamcrest, AsssertJ, Truth
* assumptions org.junit.jupiter.api.Assumptions
	* assumeTrue
* condições { SO, JRE, propriedades do sistema, baseadas em script }, org.junit.jupiter.api.condition
	* @EnabledOnOS @DisabledOnOs (ex: @EnabledOnOS(MAC)) (org.junit.jupiter.api.condition.OS.MAC)
	* @EnabledIfSytstemProperty(named = "os.arch", matches = ".\*64.\*")
	* @EnabledIf("2 * 3 == 6")
* classe não podem ser abstratas e devem ter apenas um construtor (?)
* não podem ser privados e com retorno void