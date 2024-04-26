* Faz parte da **Contabilidade Social**, que trata de uma visão contábil da sociedade, sendo composta por (cada um com metodologia própria, padronizada, bem como um órgão para contabilização e objetivos específicos):
	* **Contas nacionais**
		* **Objetivo**: medir a produção/renda do país
		* **Responsável por apuração**: IBGE (Instituto Brasileiro de Geografia e Estatística)
		* **Padrão adotado no Brasil**: de acordo com o SNA (System of National Accounts), da ONU
	* **Balanço de pagamentos**
		* **Objetivo**: medir os fluxos internacionais (pagamentos entre países)
		* **Responsável por apuração**: Banco Central
		* **Padrão adotado no Brasil**: de acordo com o BPM (Balance of Payments and International Investment Position Manual), do FMI
	* **Contabilidade fiscal**
		* **Objetivo**: medir as contas do Governo
		* **Responsável pela apuração**: Banco Central (BCB) e Secretaria do Tesouro Nacional (STN)
		* **Padrão adotado no Brasil**: de acordo com o GFSM, do FMI
	* **Sistema monetário**
		* **Objetivo**: medir a moeda
		* **Responsável pela apuração**: BCB
		* **Padrão adotado no Brasil**: de acordo com o MFSM, do FMI
* **Tipos de variáveis**
	* **Fluxo**: variáveis mensuradas em determinado **período** (início e fim)
		* ex: salário -> salário mensal -> quanto recebe por um período de um mês trabalhado
		* mais utilizadas em contas nacionais (ex: qual foi a produção do Brasil *no ano*)
	* **Estoque**: variáveis mensuradas em determinado **momento/instante** ~ *fotografia*
		* ex: saldo bancário
	* Há relação entre esses tipos de variáveis -> fluxos impactam em estoques (ex: fluxo de produção de máquinas impacta no estoque de máquinas)
* **Conceitos básicos**
	* **Produção/Produto**: *valor* total de { bens, serviços } *finais* produzidos em *uma economia* em determinado período de tempo
		* mensurado em unidades monetárias (! não há o que se falar que o PIB foi de X unidades do bem Y)
		* necessário definir o escopo da economia (ex: país, estado etc)
		* bens e serviços finais são #TODO 
	* **Renda** Y: remuneração dos fatores de produção - em concurso, costumam cair apenas os fatores *capital* e *trabalho*
		* *trabalho* é remunerado com salários S (para empregados ou para autônomos)
			* salário do autônomo também é chamado de rendimento misto bruto (é tanto um salário pago a si próprio, quanto lucro do capital utilizado)
		* *capital* é remunerado com juros **J** (em empréstimos), lucros **L** (produtos), aluguéis **A** (máquinas)
			* também chamado Excedente Operacional Bruto (EOB) -> remuneração dos agentes, menos salários
		* [questões muito boas 08:00](https://www.estrategiaconcursos.com.br/app/dashboard/cursos/275496/aulas/2639683/videos/93767)
	* **Despesa**: total gasto pelos agentes econômicos { famílias, empresas, governo, resto do mundo }
		* família -> consumo C
		* empresas -> investimento I
			* em regra é o gasto da empresa, mas investimento é todo aumento de capital fixo -> uma compra de casa nova são tratados como investimento para fins de PIB
				* ! casa usada comprada não seria considerada no PIB! porque o PIB considera o valor no momento da produção
		* governo -> gastos de governo G
		* resto do mundo -> exportação menos importações X - M
	* **Poupança** S: parte da renda não destinada ao consumo
		* poupança normalmente é simbolizada com S, de savings
		* S = Y - C
	* **! Investimento** I: aumento da capacidade de produzir ~ acréscimo de estoque de capital
		* I = FBKF + ∆E
			* FBKF -> Fluxo/Formação Bruto de Capital Fixo
			* ∆E -> Variação de estoques
		* I_líquido = I - Depreciação
	* **! Consumo Total**: consumo das famílias e dos governos
		* CT = C + G
		* ! cuidado, não confundir consumo total e consumo de famílias (C sozinho é consumo de famílias)
	* **Absorção**:
		* **Absorção Interna** = C + I + G
			* manipulando equações, chega-se em = CT + FBKF + ∆E
		* **Absorção Externa** = X - M
* **Identidades macroeconômicas**
	* **! Identidade econômica fundamental** -> Y = P = D (Renda = Produto = Despesa), pode aparecer o símbolo ≡
		* não existe uma produção que não seja ao mesmo tempo uma despesa que não seja ao mesmo tempo uma renda
		* ![[Pasted image 20240417210016.png]]
		* **Fluxo circular da riqueza**
			* abstraindo para considerar apenas famílias e empresas, como agentes econômicos
				* famílias fornecem fatores de produção, empresas usam fatores de produção, remunerando as famílias (salário, juros, aluguel)
				* famílias demandam bens e serviços, remunerando as empresas
			* ![[Pasted image 20240417210423.png]]
			* fluxos monetários (em azul) -> fluxo de dinheiro
			* fluxos *reais* (em vermelho) -> fluxo de bens e serviços
	* **Óticas de mensuração do produto**
		* para mensurar a produção, considerando a identidade fundamental, eu posso olhar (ótica) para a renda, para a produção ou para a despesa
	* **Poupança = Investimento**
		* considerando, para simplificação, que a economia é fechada (não interage com o resto do mundo) e sem governo
		* 1) Y = C + S
		* 2) D = C + I
		* 3) Y = D (identidade fundamental)
		* 4) por (1), (2), (3) -> C + S = C + I -> S = I
		* ~ os gastos das empresas está associado à poupança das pessoas (aumenta disponibilidade de capital etc)
* **Mensuração do produto**
	* critérios (prof. deu exemplo de mensuração de altura, critérios como se deve considerar cabelo, calçado etc)
		* produto interno x nacional -> em relação a se vai considerar a localização ou a propriedade
			* interno -> gerado no território do país
			* nacional -> gerado por nacionais, independente do local (como no exemplo do Itaú com filial no Chile)
				* no exemplo do PIB, PNB = PIB + RRE (Renda Recebida do Exterior) - REE (Renda Enviada ao Exterior)
				* RLEE (Renda Líquida Enviada ao Exterior) = REE - RRE
					* no Brasil é positiva, o saldo do envio/recebimento do exterior é positivo, envia mais que recebe
					* PIB = PNB + RLEE
		* produto bruto x líquido -> em relação a se vai considerar a depreciação
			* no exemplo da produção do pão, além de bens intermediários (ex: farinha de trigo), a empresa usa bens de capital (ex: forno), que sofrem depreciação
			* depreciação -> desgaste do bem de capital por obsolescência, pelo uso no processo produtivo, ou naturalmente
			* líquido -> bruto - depreciação
		* produto a preço de mercado x a custo de fatores -> impostos (ver no PIB)
		* produto real x nominal -> inflação
			* situação -> comparar PIB de anos diferentes
				* nominal -> sendo o valor corrente no momento da apuração, inclui a inflação -> pode ocorrer de a produção de bens cair, mas, com aumento dos preços, o PIB acabar aumentando
					* por isso é chamado de "preços correntes"
					* "não adianta você sair aumentando o preço, não vai deixar o país rico só assim"
				* real -> fixa-se o preço em um determinado ano e multiplica pela quantidade produzida no ano em análise 
					* por isso é chamado de "preços constantes"
					* ex: em 2017 produziu 100 a 20, resultando em 2000; em 2018 produziu 93 a 22, resultando em PIB nominal de 2046; fixando o preço de 2017, o PIB real foi de 1860
					* só cresce mesmo se a quantidade produzida crescer; noticiário costuma reportar PIB real
			* cálculo da inflação com base nos PIB nominal e PIB real (no fim das contas, é o preço atual / preço anterior)
				* $Deflator = \frac{PIB_N}{PIB_R}$
	* **PIB** = Produto Interno Bruto -> 
		* medida de todos os { bens, serviços } finais (exclui produtos intermediários) 
			* exemplo da produção de pão (bens intermediários > bem final):
				* empresa que produz sementes (50 reais)
				* empresa que produz trigo a partir das sementes (70 reais)
				* empresa que produz farinha de trigo a partir do trigo (100 reais)
				* empresa que produz pão a partir da farinha de trigo (150 reais)
				* o que é colocado à disposição do consumidor? o pão -> ele que é classificado como bem/serviço final
					* logo, no exemplo, o PIB, considerando valor final, é de 150 reais -> é a soma dos valores agregados em todas etapas produtivas
					* o restante é intermediário
		* gerados dentro das fronteiras do país, (critério geográfico)
			* não necessariamente as empresas precisam ser brasileiras! a produção da Nestlé, por exemplo, da França, é considerado no PIB!
			* de forma similar, empresa brasileira com filial em outro país não tem sua produção contabilizada
		* em determinado período de tempo, 
			* ! o bem/serviço é contabilizado no ano em que foi produzido #TODO decorar
			* ex: carro produzido em 2020, mantido em estoque e só vendido em 2022 -> entra no PIB em 2020 -> nos demais anos, é contado como variação de estoque das empresas
		* e avaliados a preço de mercado (é o padrão no PIB)
			* preço de mercado -> preço pago pelo consumidor
			* inconvenientes desse critério
				* só inclui bens/serviços públicos (ex: serviços domésticos no próprio lar não são contados)
				* não inclui atividades ilegais, como tráfico de drogas, jogo de bicho etc (do ponto de vista econômico, faz parte da riqueza, do emprego etc)
				* além de salários e lucros, inclui impostos
					* em especial, impostos indiretos (incidem sobre uma transação, quem paga não é quem recolhe)
					* não é interessante o crescimento do PIB em decorrência de aumento de impostos...
				* não inclui o valor subsidiado, reduzindo o PIB
				* impostos líquidos = impostos - subsídios
			* por conta desses inconvenientes, também trabalha-se com o **PIB a custo de fatores** = S + L + J + A (não considera impostos líquidos)
				* PIBcf = PIBpm - Imposto **in**direto + Subsídios #TODO decorar
	* Produto Interno Líquido (**PIL**) = PIB - depreciação
* **Economia aberta com governo**
	* 1) D = C + I + G (Gasto do Governo) + X - M
	* 2) Y = C + S + T (pagamento de Tributos) + RLEE - TUR
		* TUR -> Transferências Unilaterais Recebidas -> dinheiro recebido sem contrapartida (ex: doações)
	* 3) D = R (identidade fundamental)
	* por (1), (2) e (3) -> 
		* C + I + G + X - M = C + S + T + RLEE - TUR
		* I + G + X - M = S + T + RLEE - TUR
		* I = S + T - G + M - X + RLEE - TUR -> Investimentos = Poupança total = Poupança privada + Poupança do Governo + Poupança Externa
			* S = poupança privada
			* T - G = Tributação - Gastos do Governo = poupança pública
			* M - X + RLEE - TUR = poupança externa
				* M - X -> importações - exportações
				* RLEE - TUR -> o que o resto do mundo recebe menos o que ele gasta conosco
			* os investimentos são financiados pela combinação das poupanças (privada, do governo, externa)
			* poupança interna = poupança privada + poupança do governo
			* ! não confundir poupança externa com reservas internacionais -> não é a poupança que o Brasil tem no exterior!
* **Renda nacional** ! decorar
	* quando falar apenas "Renda nacional", considerar Renda Nacional Líquida a Custo de Fatores
	* **Renda Pessoal** = Renda nacional - Lucros retidos - Impostos sobre Lucros - Contribuições (ex: previdênciária) + Transferências de rendas
		* Lucros retidos -> lucros que a empresa não distribuiu para os investidores
		* Transferências de rendas -> distribuição do governo
	* **Renda Pessoal Disponível** = Renda pessoal - Impostos diretos (ex: imposto sobre renda, sobre patrimônio etc) -> é a renda pessoal que sobra após pagar os impostos
	* Renda Disponível Bruta (**RDB**) = Renda Nacional Bruta + TUR
	* Renda Líquida do Governo (**RLG**) = Impostos diretos + Impostos Indiretos (I.I.) - transferências do governo - subsídios -> impostos - transferências/subsídios
	* Renda Privada Disponível = RDB - RLG = C + S (é o que sobra da renda depois que pagou o que deve pagar)
* ![[Pasted image 20240424195317.png]]
	* #TODO decorar
	* [questão muito boa 26:40](https://www.estrategiaconcursos.com.br/app/dashboard/cursos/275496/aulas/2639683/videos/93767)