* **Teoria do consumidor**: o consumidor escolhe a melhor cesta de bens que ele pode adquirir ([resumo](https://www.estrategiaconcursos.com.br/app/dashboard/cursos/275496/aulas/2639682/videos/82662))
	* **Cesta de bens**: determinada variedade e quantidade de coisas/bens que podem satisfazer necessidades do consumidor
		* o comum em concurso é trabalhar apenas com dois bens (pode-se pensar que um bem representa o objeto de estudo e o outro representa todos os demais bens da cesta)
		* x = (q1, q2) 
			* x = cesta de bens
			* q1 = quantidade do bem 1
			* q2 = quantidade do bem 2
	* **Restrição orçamentária**: o poder adquirir (orçamento/renda limitada)
		* para traçar a reta de restrição orçamentária, basta ver os pontos com quantidade 0 em cada bem e depois traçar a reta
		* os pontos na reta esgotam a renda; abaixo -> sobra renda; acima -> extrapolam
		* a tangente do ângulo é usado para mensurar a inclinação da reta
			* ![[Pasted image 20240401170346.png]]
		* ! a tangente pode ser interpretada como 'se eu abrir mão de uma unidade do bem da abcissa, eu posso obter tangente bens da ordenada'
		* a inclinação é alterada quando há alterações nos preços dos bens, em proporções diferentes (se subirem, por exemplo, em 20% as duas, não muda a inclinação)
		* a posição da reta de restrição orçamentária pode ocorrer por alteração
			* na renda -> se aumenta, desloca a reta para a esquerda etc
			* nos preços (alterando na mesma proporção) -> se aumenta, a reta desloca para a direita etc
		* a inclinação da curva de restrição orçamentária depende apenas dos preços relativos dos bens! a renda não muda a inclinação!
	* **Preferências do consumidor** (! não confundir, apesar de a curva aqui também ser função das quantidades na cesta, trata-se de preferência, e não de restrição orçamentária)
		* Símbolos indicando preferência entre cestas de bens
			* A > B -> prefere A a B -> preferência forte
			* A >= B -> A é pelo menos tão preferível que B -> ==preferência fraca==
			* A ~ B -> tanto faz A ou B
		* Premissas das preferências do consumidor (são assumidas)
			* **Integralidade**: completude -> o consumidor sempre é capaz de comparar cestas e indicar preferência
			* **Reflexividade**: A >= A, A ~ A (cestas iguais são tão preferíveis quanto/indiferentes a si mesmas)
			* **Transitividade**: A > B e B > C -> A > C
			* **Monotonicidade**: cestas que pertencem a curva de indiferença totalmente à direita de outra curva são preferíveis a cestas da outra
				* ![[Pasted image 20240402145439.png]]
				* não é válido nesse caso! /\ esse gráfico só é válido para curvas de indiferença não bem comportadas (não monotônicas/reflexivas)
		* **Curvas de indiferença**: curvas no gráfico de restrição orçamentária que indicam cestas para as quais o consumidor tem preferência indiferente
		* **Taxa marginal de substituição (TMS)**
			* variação de um bem e de outro que mantém a cesta na mesma curva de indiferença (quanto o consumidor está disposto a ceder do bem_1 para ganhar uma unidade do bem_2)
			* em regra -> decrescente
			* inclinação da curva de indiferença em um ponto -> ! ela muda de acordo com o ponto!
			* tende a ser convexa -> lembra a curva de fronteira/possibilidade de produção! (! cálculo com derivada)
		* **Substitutos perfeitos**
			* a curva de indiferença é uma reta inclinada -> tanto faz a proporção entre os bens (ex: tanto faz 10 coca-colas ou 5 coca-colas + 5 pepsis)
			* TMS é constante
		* Complementares perfeitos
			* complementar perfeito -> só consumo os dois bens na medida de certa proporção
			* a curva de indiferença forma um L -> ex: pé esquerdo e pé direito do sapato -> só consome um se e somente se consumir o outro
				* é formada pelos pontos em {(n_sapatos, y) |  y \\in domínio } U { (x, n_sapatos) | x \\in domínio }
				* ![[Pasted image 20240402172912.png]]
			* TMS tende a 0 no eixo que está com excesso de bem #n_entendi 
			* TMS tende a infinito no eixo que está com falta de bem
		* Curvas côncovas
			* bens que não são consumidos juntos (ex: bacon e nutella) -> consumidor prefere especializar, consumir só um
			* TMS crescente - !é preciso receber muita nutella para abrir mão de pouco bacon, mas, a partir de certo ponto, isso inverte, eu troco pouco bacon por qualquer coisa de nutella
			* ![[Pasted image 20240402173320.png]]
		* bem x mal [não entendi bem 27:00](https://www.estrategiaconcursos.com.br/app/dashboard/cursos/275496/aulas/2639682/videos/82657) #TODO 
			* curva positivamente inclinada
	* **Utilidade**
		* valor numérico atribuído a uma cesta de bens para mensurar quanto o consumidor gosta/satisfação dessa cesta -> importa apenas a ordem entre cestas, a diferença entre quantidade não é considerada
		* a função de utilidade relaciona quantidade de bens na cesta à utilidade para o consumidor
			* ex: u(q1, q2) = q1 + q2
			* determina o formato das curvas de indiferença
			* !fórmulas comuns #anki 
				* substituto perfeito -> u(q1, q2) = a\*q1 + b\*q2
				* complementares perfeitos -> u(q1, q2) = min(q1, q2)
				* cobb-douglas -> u(q1, q2) = (q1^a) \* (q2^b) (curva côncava)
		* utilidade marginal -> utilidade adicionada quando se incrementa uma unidade de um bem
			* UMgx = delta U / delta qx
			* UMgx \* delta qx = - UMgy \* delta qy (considerando que a utilidade final não muda, daí adicionar de um bem, retirando o necessário do outro bem)
			* ![[Pasted image 20240403092120.png]]
				* a utilidade marginal de x dividida pela utilidade marginal de y é igual à TMS
		* **lei da utilidade marginal decrescente**
			* o incremento de utilidade em função do incremento na quantidade decai (ex: ganhar uma coca-cola no almoço é bom, duas coca-colas não traz o dobro do ganho, 1000 coca-colas não traz 1000 * a utilidade de uma coca-cola)
			* ![[Pasted image 20240403092456.png]]
			* a curva de utilidade total (a roxa) vai crescendo cada vez menos
			* mantido fixo o consumo de um bem, o incremento do outro vai decaindo com a quantidade do incremento
	* **Escolha do consumidor** -> escolhe a cesta de bens cuja curva de indiferença tangencia sua reta orçamentária
		* ![[Pasted image 20240409150502.png]]
			* curva vermelha -> curva de restrição orçamentária
			* curvas azuis -> curvas de utilidade/indiferença
			* a cesta no ponto C é a melhor escolha possível!
			* a cesta no ponto A é boa, mas não esgota sua renda
			* a cesta no ponto B é boa, mas tem menor nível de utilidade que C
		* mais formal, a escolha se dá quando a TMS é igual à inclinação da curva orçamentária
			* ![[Pasted image 20240409151024.png]]
		* exceções
			* ![[Pasted image 20240409151055.png]]
			* no caso dos substitutos perfeitos -> solução de canto (vai escolher o ponto na esquerda, que é onde são iguais)
			* nas curvas côncavas, escolhe o ponto na direita (no exemplo do gráfico) -> não é onde tangencia
		* no caso de funções de Cobb-Douglas ([questão em 15:30](https://www.estrategiaconcursos.com.br/app/dashboard/cursos/275496/aulas/2639682/videos/82659))
			* ![[Pasted image 20240409151520.png]]
			* ! não interessa se o x ou o y estão sendo multiplicados por algum escalar
			* quando a soma dos expoentes é igual a 1, o gasto ótimo com o bem X consiste em gastar um percentual da sua renda com X igual ao percentual do expoente
				* ![[Pasted image 20240409151722.png]]
				* gasto ótimo de X = 0.7 \* R / px
				* gasto ótimo de Y = 0.3 \* R / py
				* cuidado! a quantidade é o total gasto dividido pelo preço individual!
	* **Efeitos renda e substituição**
		* Ex: preço da internet diminuiu de 100 para 80 reais
			* efeito renda: variação na demanda em função do poder aquisitivo disponível = preço diminui (há mais poder aquisitivo) -> percepção de que há mais dinheiro disponível
				* bens normais -> preço aumenta, efeito renda negativo
				* bens inferiores -> preço diminui, efeito renda negativo (ex: preço da carne de 2ª diminui, posso comprar agora parte de 2ª e parte de 1ª)
			* efeito substituição: variação na demanda em função da percepção de preço relativo = preço diminui -> percepção de que o bem está mais barato em relação aos demais
				* sempre tem sinal inverso ao da variação no preço (ex: se o preço aumenta, o efeito substituição é negativo) -> se o preço subir, necessariamente o bem irá consumir, proporcionalmente, mais da renda (o que é negativo)
		* para calcular o efeito de substituição (de Hicks) -> com a mesma inclinação resultante do ajuste no preço, tangenciar a curva de indiferença anterior
		* ![[Pasted image 20240409194804.png]]
		* daí a diferença entre a quantidade anterior e a quantidade calculada com a lógica acima é o efeito substituição - o que sobrar, da variação total, é efeito renda
		* efeito total = efeito renda + efeito substituição
		* bens normais -> efeito renda e efeito substituição possuem mesmo sinal ('andam na mesma direção')
		* ![[Pasted image 20240409200028.png]]
		* bens inferiores /\\ efeito substituição de 4, efeito renda -1 -> efeito total = 3 (para bens inferiores, o efeito renda atenua o efeito substituição)
		* ![[Pasted image 20240409200201.png]]
		* bens de Giffen /\\ -> o efeito de renda negativo supera o efeito substituição positivo
			* 'o ovo até que está mais barato, vou consumir mais! (efeito substituição), mas vai sobrar mais dinheiro, vou consumir é filé (efeito renda)'
			* Questão V/F: Os bens de Giffen são bens inferiores cujo efeito substituição é superior ao efeito renda -> F (em módulo, o efeito renda supera o efeito substituição)
		* ![[Pasted image 20240409204701.png]]
	* **Curva de Engel** -> mostra como varia a demanda do bem em função da renda (com preço fixo!)
		* ![[Pasted image 20240409203920.png]]
			* gráfico /\\ de um bem normal -> para bens inferiores, a curva é espelhada, a demanda cai com a diminuição do preço
			* Questão V/F: Se um bem é inferior, a curva de Engels é positivamente inclinada -> F
	* **Curva Renda-Consumo** -> mostra como varia o consumo dos dois bens (x e y, no gráfico) em função da renda do consumidor
		* ![[Pasted image 20240409203842.png]]


