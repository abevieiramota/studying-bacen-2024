#TODO ler sobre RMI

[JavaSE](https://www.estrategiaconcursos.com.br/app/dashboard/cursos/275777/aulas/2640890/videos/203286)
* fortemente tipada -> a variável só tem um tipo apenas
* estaticamente tipada -> definição de tipo em tempo de compilação (var é apenas um shortcut para a definição ser inferida em tempo de compilação)
* multi-thread
* da vinci machine -> suporte para outras linguagens na jvm
* Write One Run Anywhere - WORA
	* compilada: em c, compila para uma plataforma
		* V: permite otimizações considerando plataforma + arquitetura
	* compilada e interpretada: em java, compila para bytecode (código de máquina virtual), jvm interpreta (! a entrada da JVM é bytecode, não é java!); a interpretação transforma bytecode em linguagem de máquina
		* V: interoperabilidade, capacidade de otimizações on-the-fly (as compiladas apenas só conseguem otimizar na compilação) - ex: Just In Time compilaton
* Sopa de letrinhas
	* JVM: é uma especificação de como uma máquina virtual deve ser feita -> pode ter diversas implementações
	* JDK: development kit (JVM + kit para dev - javac etc)
	* JRE: runtime environment (JVM)
	* Java
		* JavaSE: Standard Edition -> basicamente o que já está na JVM (utils etc)
		* JavaEE: JavaSE + APIs (atualmente chamada JakartaEE) -> especificação de diversas API para desenvolvimento de aplicações enterprise
		* JavaME: micro edition; (! não é a mesma coisa que Android!)
* HelloWorld
	* public class X { public static void main (String args []) { System.out.println("Olá"); } }
* Sintaxe
	* variável: *tipo nome* - ex: int a = 10;
	* tipos
		* double, float: ponto flutuante; ! cuidado, 0.0 é double, para usar como float, ou faz cast ou coloca um f na direita #TODO o que ocorre fazendo cast de um tipo maior para um menor long > int > short
		* var a -> tipo inferido em tempo de compilação
		* as variáveis definidas a nível de classe são inicializadas; a nível de método não!
		* bases
			* 0b010 binário
			* 06 octal (! cuidado se derem um print, o valor é '6')
			* 0xA hexa
	* x++, ++x
	* \==, equals
	* if (condição) -> ! parênteses obrigatórios!; com apenas uma instrução, não é necessário chaves (nem no if, nem no else, nem no else if)
	* bool operators: ||, &&,
	* switch (var) { case 1: assd; break; default: asdahds;}
	* for (inicia; checa; incrementa) {}; ! cada parte do for é opcional -> for (;;) {} compila e executa eternamente
	* for (int num: numeros) {} "foreach"
	* while (condição) {}; usa break para sair
	* do {} while(condição)
	* bit shift operators (converte para binário e aplica) #TODO operador >>>
		* 123 >> 2: move 2 bits para a direita
		* 123 << 2: move 2 bits para a esquerda
	* Não há operador de exponencial -> usa Math.pow
	* String
		* String é imutável! os métodos não alteram o objeto; 
			* String x = "a"; String y = "a"; x\==y (true), x.equals(y) (true) -> porque instanciando com o literal apenas, a JVM usa o pool de strings, daí associa ao mesmo objeto
			* String x = new String("a"); String y = new String("a"); x\==y (false), x.equals(y) (true) -> porque instanciando com construtor, já não usa o pool
		* métodos
			* charAt(int pos)
			* substring(int ini, int end) - o end é exclusivo!
			* s1 + s2 -> concatenação
			* System.out.prin**tf**("%s", s)
		* StringBuilder -> append(s); é mutável; operador + usa um StringBuilder
		* #TODO ver os principais métodos
	* Array -> todo array é um objeto! daí inicializa com new #TODO array multidimensional
		* { tipo deve ser definido, tamanho deve ser definido, não é permitida alteração }
		* int \[] idade = new int\[10]
		* idades.length
		* #TODO ver os principais métodos
	* Collections -> java.util.Collection #TODO ver artigo do baeldung sobre como escolher as melhores estruturas de dados em java
		* List - aceita elementos repetidos, é mutável; implementações ArrayList, LinkedList
			* List idades = new ArrayList(); -> desse jeito, é lista de Object!
			* List\<Integer> = new ArrayList\<Integer>(); -> aceita apenas Integer
			* idades.get(i), idades.add(x), idades.contains(x), idades.remove(i) ! cuidado, o parâmetro é o índice!
			* idades.forEach(num -> System.out.println(num)) ou idades.forEach(System.out::println)
		* Set - não aceita elementos repetidos; implementações HashSet, TreeSet, LinkedHashSet (! a ordem depende da implementação!!!)
			* ordem -> o LinkedHashSet mantém a ordem de insert; TreeSet mantém a ordem de acordo com um Sort (com String, por exemplo, ordem textual); HashSet não garante ordem
			* se.add(x), não tem pesquisa por índice, 
		* Map - não extend do Collection! não aceita chaves repetidas; implementações HashMap
			* m.put(x, y); (se a chave já existir, sobrescreve) m.get(x); m.keySet(), m.forEach((k, v) -> System.out.println(k, v));
		* Queue
		* Stack


Conversão de bases #TODO


Curiosidades
* Java tem perdido espaço em contextos efêmeros (aplicação tem tempo de vida curto, como em contâiners), porque é interessante usar linguagens com fast startup + otimização (pessoal passou a usar linguagens como Golang (compilada), Javascript etc)
	* a solução do java foi criar um compilador gerando código específico para plataforma, usando JVMs como a GraalVM
* nome de classe não é palavra reservada (String, por exemplo, pode ser usada como nome de variável!)
* por padrão, estão implícitos
	* import java.lang.*
	* class X *extends Object*
	* public metodo (int param) *throws RuntimeException*
* jshell -> shell similar ao do Python
* short a = 10; a = a + 1; (erro de compilação -> o resultado somando com 1 é int, é preciso fazer cast)
* 
