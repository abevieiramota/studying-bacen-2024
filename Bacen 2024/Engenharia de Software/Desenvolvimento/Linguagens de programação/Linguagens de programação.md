* **Linguagens**:
	* [[Java]] e [[JavaEE]]
	* [[Python]]
* **Conceitos**:
	* def::**Linguagem fortemente tipada**: a variável só tem um tipo apenas ^def-lang-fort-tipada
	* def::**Linguagem estaticamente tipada**: definição de tipo em tempo de compilação ^def-lang-stat-tipada
	* **Máquina virtual**:
		* def::**Write One Run Anywhere** (WORA): capacidade de escrever o código apenas uma vez e ele ser utilizado em plataformas diversas
			* **Compilado**: compilada: em c, compila para uma plataforma
				* **V**: permite otimizações considerando plataforma + arquitetura
			* **Compilado e interpretado**: em Java, por exemplo, compila para bytecode (código de máquina virtual), jvm interpreta (! a entrada da JVM é bytecode, não é java!); a interpretação transforma bytecode em linguagem de máquina
				* **V**: { interoperabilidade, capacidade de otimizações on-the-fly (as compiladas apenas só conseguem otimizar na compilação) - ex: Just In Time compilaton } 