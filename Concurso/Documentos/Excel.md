* **geral**
	* na interface, há uns ícones no canto inferior direito para expandir as opções, opções detalhadas/avançadas
	* comentário -> clica com o direito onde quer inserir > inserir comentário
		* ==dá para fixar o comentário== -> clica com o direito e seleciona
	* clicar e arrastar -> copia fórmulas -> pode perder a formatação -> clica no ícone de baixo e marca para copiar sem mexer na formatação
	* insert slicer -> telinha com valores únicos de colunas, permitindo filtrar mais visualmente
* **referências**
	* relativas -> A10
	* absolutas -> $A$10
		* $A10 -> fixa apenas a coluna
		* A$10 -> fixa apenas a linha
		* $A$10 -> fixa linha e coluna
		* para fixar uma célular/intervalo selecionada -> F4
	* ao arrastar uma célula, o valor resultante irá ser gerado movendo as referências relativas da mesma forma, e mantendo as referências absolutas
* **tipos de dados**
	* página inicial > número > selecionar o tipo
* **data**
	* split text to columns
	* remove duplicates
* **review**
	* protect sheet -> impede alteração -> pode especificar espaços editáveis
* **draw**
* **funções**
	* condicionais
		* somase(intervalo; critérios; \[intervalo_soma\])
			* interval -> onde será aplicado os critérios
			* critérios
			* intervalo_soma -> onde será coletado o valor a ser somado
		* cont.se(intervalo; critérios)
	* texto
		* concat(x; y; z) -> o & serve para concatenar -> ex: =B1 & " " & B2
	* tempo
		* data(ano; mes; dia)
		* datadif(data_inicial; data_final) -> datadif(C3; HOJE(); "y") -> anos
	* ==procv== -> vlookup
		* procv(chave da pesquisa; tabela a pesquisar; índice da coluna a retornar; se deve ter correspondência exata)
	* seerro(expressão; valor a ser retornado)
		* ! usada para quando a expressão retorna erro quando falta algum valor etc, daí mostrar alguma mensagem, no lugar do \#N/D etc
	* agregações -> selecionar linhas e clicar no AutoSum
	* Name Manager -> criar variáveis nomeadas
* **formatação**
	* condicional -> seleciona e vai no menu > formatação condicional
		* ! é possível adicionar ícones -> mas as regras são fixas :(
		* é possível destacar os top/bottom
	* ==formatação como tabela== -> seleciona a tabela e papoca! ! já aparecem opções numa aba a parte, como incluir totais, filtros etc!
		* ==!!!!!!!!!!!!!!!!!!== permite referenciar colunas com \<nome da tabela\>\[nome da coluna\]
	* ==selecionar todas as células== > cells > format > auto fit height/width
	* ==format painter== -> clica na célular que quer copiar formatação -> format painter -> clica nas células para onde quer copiar
	* border -> draw border / border grid
* **impressão**
	* selecionar o intervalo > exibir > visualização da quebra de página -> dá para ver e alterar a forma de impressão -> CRTL+P
	* CRTL+P -> ajustar planilha -> tem opção de colocar tudo na página, ou toda coluna etc
* **shortcuts**
	* crtl + seta -> vai até o fim da planilha
	* ==auto soma==: seleciona tabela de valores e uma linha e coluna extra vazia + alt + =
	* crtl + h -> pesquisar
* **gráficos**
	* formatação { axis, labels etc }
* **bizus**
	* ver valores únicos -> seleciona células > filtro avançado -> copiar para outro local > marcar somente registros exclusivos
	* criar células com valores selecionáveis baseados em lista separada -> seleciona as células > validação de dados > lista -> seleciona as células com os valores
* ==**exercitar**==
	* group by -> uma tabela com categoria e valor -> uma coluna com as categorias únicas, adicionar ao lado o somatório de valores daquela categoria