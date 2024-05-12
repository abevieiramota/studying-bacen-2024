* **Características**:
	* [[Linguagens de programação#^def-lang-fort-tipada|Fortemente tipada]]
	* [[Linguagens de programação#^def-lang-stat-tipada|Estaticamente tipada]]
	* Multi-thread
	* [[Orientação a Objetos|OO]]
* **JVM**: é uma especificação de como uma máquina virtual deve ser feita -> tem diversas implementações
	* 
	* def::**Da Vinci Machine**: suporte, na JVM, para outras linguagens de programação
* def::**JDK**: development kit (JVM + kit para dev - javac etc)
* def::**JRE**: runtime environment (JVM)
* **Edições**:
	* **JavaSE**: Standard Edition -> basicamente o que já está na JVM (utils etc)
	* [[JavaEE]]: JavaSE + APIs (atualmente chamada JakartaEE) -> especificação de diversas API para desenvolvimento de aplicações enterprise
	* **JavaME**: micro edition; (! não é a mesma coisa que Android!)
* **Sintaxe**:
	* Declaração de variável:
		* `int a = 10;`
	* **Tipos primitivos**:
		* double, float: ponto flutuante 
			* !0.0 é double, para usar como float, ou faz cast ou coloca um f na direita `0.0f`
			* !cast de tipo maior para menor, `long a; int b = (int) a;`, apenas ignora bits, não dá erro
		* `var a = 55;`: tipo inferido em tempo de compilação
		* as variáveis definidas a nível de classe são inicializadas; a nível de método não!
		* **Bases**:
			* **binário**: `0b010`
			* **octal**: `06`
			* **hexa**: `0xA`
			* todo::Estudar conversão de bases
		* todo::Adicionar demais tipos primitivos do Java
	* **Operadores**:
		* x++, ++x (pré/pós-incremento)
		* \==, equals
		* bit shift operators (converte para binário e aplica)
			* 123 >> 2: move 2 bits para a direita
			* 123 << 2: move 2 bits para a esquerda
			* next_step::Operador java >>>
		* não há operador para exponenciação -> usar Math.pow
		* **boolean**: ||, && 
			* todo::Adicionar operadores booleanos
	* **if**
	  ```java
	  if (cond) { // parênteses obrigatórios, chaves não obrigatórias, caso haja apenas um statement no bloco do if
		// do something
	  } else if (cond2) {
		// do more
	  } else {
		// agora sim!
	  }
	  ```
	* **switch**
	  ```java
	  switch(expr) {
		  case x: 
			  // do something
			  break;
		  case y:
			  // do more
			  break;
		  default:
			  // agora sim!
	  }
		```
	* **for**
	  ```java
	  for(int i = 0; i < n; i++) {} // cada parte do for é opcional! for(;;) {} compila e executa indefinidamente
	  for(int num: numeros) {}
```
	* **while**
	  ```java
	  while (cond) {}
```
	* **do-while**
	  ```java
	  do {
		  // something
	  } while (cond)
```
	* **classe anônima**
	  ```java
	  button.addActionListener(new ActionListener() {
	    public void actionPerformed(ActionEvent e) {}
	  }
```
	* **String**:
		* String é imutável - os métodos não alteram o objeto
			* String x = "a"; String y = "a"; x\==y (true), x.equals(y) (true) -> porque instanciando com o literal apenas, a JVM usa o pool de strings, daí associa ao mesmo objeto
			* String x = new String("a"); String y = new String("a"); x\==y (false), x.equals(y) (true) -> porque instanciando com construtor, já não usa o pool
		* **Métodos**:
		  ```java
		  s.charAt(10)
		  s.substring(0, 5) // o end é exclusivo!
		  s1 + s2 // concatenação -> usa StringBuilder
		  System.out.printf("%s", s)
```
			* **StringBuilder**: permite construir string por meio de métodos como append(s); é mutável
	* **Array**: { tipo deve ser definido, tamanho deve ser definido, não é permitida alteração }
	  ```java
	  int [] idade = new int[10];
	  int idade [] = new int[10];
	  int [][] coords = new int[5][4];
	  idade.length;
```
	* **java.util.Collection**
		* **List**: aceita elementos repetidos, é mutável
			* implementações { ArrayList, LinkedList }
			  ```java
			  List idades = new ArrayList(); // lista de Object
			  List<Integer> l = new ArrayList<Integer>(); // aceita apenas Integer
			  l.get(idx);
			  l.add(x);
			  l.contains(x);
			  l.remove(idx);
			  l.forEach(n -> System.out.println(n));
			  l.forEach(System.out::println)
```
		* **Set**: não aceita elementos repetidos; 
			* implementações { HashSet, TreeSet, LinkedHashSet }
			* ordem: 
				* LinkedHashSet mantém a ordem de adição; 
				* TreeSet mantém a ordem de acordo com um Sort (com String, por exemplo, ordem textual); 
				* HashSet não garante ordem
			```java
			s.add(x)
```
		* **Map**: não extend do Collection! não aceita chaves repetidas
			* implementações { HashMap, LinkedHashMap, TreeMap }
			  ```java
			  m.put(x, y);
			  m.get(x);
			  m.keySet();
			  m.forEach((k, v) -> System.out.println(k, v));
```
		* **Queue**: 
			* implementações { PriorityQueue, Deque, LinkedList, }
			* métodos: além dos métodos padrões { add, remove, element }, tem { offer, poll, peek } - essas não lançam exceção em caso de erro, retornando valor como null/false
		* **Stack**: LIFO; métodos { push, pop, search }
		* **Stream**:
			* adicionados à List: removeIf, sort(Comparator.naturalOrder() ) -> inplace
			* list.stream/parallelStream(). { max(Comparator), map(Conta\:\:getSaldo).toList(), mapToDouble(Conta\:\:getSaldo).average(), }
				* findFirst, findAny (pega qualquer um, independente da ordem!), sorted, distinct
	* **Exceptions**:
		* RuntimeException extends Exception
			* todo::Ler javadoc de Exception e de RuntimeException
		* todo método tem implícito `throws RuntimeException`
		* try/catch/finally -> finally sempre é executado (! é possível fazer só try/finally)
		  ```java
		  try {
			  // meu código quebrado
		  } catch(ArrayIndexOutOfBoundException ex) {
			  // tratamento
			  // ! caso o bloco do try não lance potencialmente a exceção declarada -> erro de compilação
		  } catch(IOException ex) {
			  // ! não pode ter catch de exceção X seguido de catch de exceção Y, com Y extends X, porque será código unreachable
		  } catch(EXCA | EXCB | EXCC ex) {
			  // multicatch
		  } finally {
			  // execução obrigatória
		  }
```
		* toda exceção que estende de Exception é checked e precisa ser tratada
		* **try with resources**:
		  ```java
		  try (FileReader fr = new FileReader(path)) {
			  return fr.method();
		  }
```
	* **Threads**:
		* deve implementar Runnable ou extender Thread
			* se implementar Runnable, é preciso passar o objeto para um new Thread(new Classe())
			* enquanto extendendo Thread, basta instanciar
			* é possível passar o run como lambda function para o construtor do Thread (ex: new Thread(() -> System.out.println("oi");))
		* !`thread.run()` executa o código na mesma thread corrente! cuidado, pegadinha com ordem de resultados, com o run ficam serial as execuções
			* o `thread.start()` que cria fluxos novos, com execução concorrente
		* `Thread.currentThread()` -> identificador da thread corrente
		* todo::ver exemplo de código com uso de threads
* **OO**:
	* modificadores de acesso:
		* private > default (classes do mesmo pacote) > protected (subclasses) > public
	* java não permite herança múltipla, mas permite interface estender múltiplas interfaces -> nesse caso, super.m(), com m pertencendo às duas interfaces pais -> para evitar o diamond problem, é preciso fazer Pai.super.m(), prefixando com a interface pai
	* polimorfismo dinâmico (overriding/sobrescrita) x polimorfismo estático (overloading/sobrecarga)
	* método concreto em interface
	  ```java
	  interface A {
		  public default String olaMundo() { return "Olá mundo!"; }
	  }
```
* **Outras informações**:
	* Java tem perdido espaço em contextos efêmeros (aplicação com tempo de vida curto, como em contâiners), porque é interessante usar linguagens com fast startup + otimização (pessoal passou a usar linguagens como Golang (compilada), Javascript etc)
		* a solução do java foi criar um compilador gerando código específico para plataforma, usando JVMs como a GraalVM
	* nome de classe não é palavra reservada (String, por exemplo, pode ser usada como nome de variável!)
	* por padrão, estão implícitos
		* import java.lang.*
		* class X *extends Object*
		* public metodo (int param) *throws RuntimeException*
	* jshell -> shell similar ao do Python
	* short a = 10; a = a + 1; (erro de compilação -> o resultado somando com 1 é int, é preciso fazer cast)
* 


# Exemplos de código

## Hello World

```java
class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!"); 
    }
}
```

todo::Adicionar mais exemplos de código

# Não tão importante

**Features por versão**:
	* Features novas do Java 8
		* data
		* virtual extensions methods - default methods
		* removeif, sort
		* herdando de múltiplas interfaces
		* lambdas
		* streams
		* filter, peek map, reduce, max, min, collect
	* Features novas do Java 9
		* jshell
		* módulo - jigsaw
		* jpms
		* private methods interface
		* reactive streams
		* HTTP Client
	* Features novas do Java 10
		* var
		* otimizações para Docker
	* Features novas do Java 11
		* javac is dead (não precisa fazer mais javac, depois java > só java e já faz tudo)
		* Strings
		* strip x trim
		* repeat
	* Features novas do Java 12
		* switch expressions: arrow, break -> case 'A', 'B' -> 'A|B'; (já retorna)
		* Strings
	* Features novas do Java 13
		* keyword yield, para retornar valor num switch (sem precisar ficar dando break depois)
		* text blocks com """ asdsad """
	* Features novas do Java 14
		* if (obj instanceof String str) -> já verifica e casta para String guardando no objeto str
		* Records -> public record Person(String name, String address) {}; -> já adiciona construtor, getters, equals, hashCode, toString
	* Features novas do Java 15
		* hidden classes
		* zgc e shenandoah passam a não serem mais experimentais, G1 continua default
	* Features novas do Java 16
		* melhorias nos métodos default em interfaces
		* Stream.toList(), no lugar de .collect(Collectors.toList())
	* Features novas do Java 17
		* melhoria no gerador de números pseudo random
		* pattern matching for switch -> consegue fazer switch com obj e match por classe/interface, daí entra se for instância
		* sealed class/interface -> apenas pode ser extendida/implementada por classes/interfaces autorizadas
	* Features novas do Java 18
		* melhorias no javac compiler
		* simple web server
	* Features novas do Java 19
		* virtual threads (preview) -> limite de threads, modelo de thread não blocante -> quando vai fazer IO, a thread volta para o pool
	* Features novas do Java 21
		* string templates