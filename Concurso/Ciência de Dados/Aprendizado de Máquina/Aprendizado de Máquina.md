* [[Tipos de Aprendizado]]
* [[Redes Neurais]]
* [[Ciência de Dados/Aprendizado de Máquina/Tools]]

* def::**Aprendizado de Máquina**: '*Machine Learning is the field of study that gives computers the ability to learn without being explicitly programmed.*' (1959, Arthur Samuel)
* def::**Aprendizado de Máquina**: '*A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E.*' (1997, Tom Mitchell)
* **Por que usar**: quando programação explícita é menos adequada
	* problema envolve muitas regras 
	* problema envolve regras com mudança frequente (ex: spam filter)
	* problema muito complexo para outras abordagens
	* problema não tem solução com algoritmo conhecido (ex: speech recognition)
* **Tipos de análise**: { descritiva, diagnóstica, preditiva, prescritiva }
* **Desafios**:
	* baixa quantidade de dados
	* baixa qualidade de dados:
		* dados pouco representativos - amostra enviesada
		* outliers
		* missing values
			* def::**Missing Completely At Random** (MCAR): a causa da missing data não tem relação com os dados coletados (ex: usuário não respondeu à pergunta porque espirrou no momento e esqueceu)
			* def::**Missing At Random** (MAR): a causa da missing data tem relação com dados coletados, mas não com o fenômeno avaliado (ex: pesquisa sobre depressão, homens respondendo menos que tiveram depressão)
			* def::**Missing Not At Random** (MNAR): a causa da missing data tem relação com o fenômeno avaliado (ex: pesquisa sobre depressão, pessoas respondendo menos que tiveram depressão por consequência da própria depressão)
		* wrong values
		* irrelevant features
* **Processo**:
	* [[CRISP-DM]]
	* **Pré-processamento**:
		* def::**OneHotEncoding**: codifica uma feature categórica em N features booleanas, uma para cada valor da categoria
		* def::**OrdinalEncoding**: codifica uma feature categória em uma feature ordinal, associando cada valor do domínio original a um inteiro do range \[0, len(dom)\]
		* def::**MinMaxScaler**: $\frac{x - min}{max - min}$ -> transforma para range \[0, 1\]
		* def::**Standardization**: $\frac{x - \mu}{\sigma}$ -> transforma uma distribuição normal $N(\mu, \sigma^2)$ qualquer para uma distribuição normal padrão $N(0, 1)$ (menos afetado por outlier)
			* "*For instance, many elements used in the objective function of a learning algorithm (such as the RBF kernel of Support Vector Machines or the l1 and l2 regularizers of linear models) may assume that all features are centered around zero or have variance in the same order. If a feature has a variance that is orders of magnitude larger than others, it might dominate the objective function and make the estimator unable to learn from other features correctly as expected.*" [fonte](https://scikit-learn.org/stable/modules/preprocessing.html#standardization-or-mean-removal-and-variance-scaling)
			* É preciso cuidado com dados com outliers, porque eles podem influenciar bastante a média e desvio padrão -> scikit-learn oferece um scaler mais apropriado para esses casos, [RobustScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.RobustScaler.html#sklearn.preprocessing.RobustScaler)
		* def::**Normalization**: escala os dados para ter norma unitária, usando uma das seguintes normas, que são medidas de tamanho de vetores:
			* L1 (Manhattan distance): $\sum{x_j}$ 
			* L2 (Euclidian distance): $\sqrt{\sum{x_j^2}}$
			* Max: $max(x_j)$
			* o vetor escalado é igual ao vetor original dividido pela norma
		* def::**MaxAbsScaler**: similar a um MinMaxScaler, mas escalando para o range \[-1, 1\]
		* def::**Discretization**: codifica uma feature contínua numa feature discreta
	* **Teste e validação**:
		* para avaliar a qualidade do modelo, idealmente separa-se parte dos dados para teste e parte para treino
		* o treinamento envolve otimização de parâmetros, feito num esquema de separação dos dados entre treino e validação -> treina com treino, avalia com validação, apura os melhores parâmetros
		* otimizados os parâmetros, treina-se o modelo com todos os dados de treino e finalmente se avalia ele com os dados de teste
		* def::**Cross-validation**: esquemas para separação de conjuntos de treino e de validação, a serem utilizados na seleção de hiperparâmetros:
			* **KFold**: divide-se o conjunto de treino em K partes, treinando com K-1 partes e avaliando na parte remanescente, fazendo isso K vezes; ao fim, reporta-se a média das métricas de avaliação
			* **RepeatedKFold**: aplica o KFold n vezes (em cada uma retornando um particionamento aleatório)
			* **LeaveOneOut**: separa os dados em treino e validação removendo um elemento por vez para validação, ficando o resto em treino; variação, com P elementos de validação = **LeavePOut**
			* **ShuffleSplit**: gera partições aleatórias dos dados, respeitando uma proporção especificada de treino e validação
			* **StratifiedKFold**: variação do KFold para problemas de classificação, que busca garantir uma distribuição uniforme dos dados nas partes, de acordo com o target
			* **StratifiedShuffleSplit**: variação do ShuffleSplit, que busca garantir uma distribuição uniforme dos dados nas partes, de acordo com o target
			* **TimeSeriesSplit**: variação do KFold para timeseries, particionando os dados de forma a respeitar a ordem temporal e incluindo no validation set dados posteriores ao training set
* **Conceitos**:
	* def::**Covariance**: medida de variação conjunta de variáveis $cov(X, Y) = E[(X - E[X]) (Y - E[Y])]$; covariance positiva, as duas variáveis mudam na mesma direção; negativa, mudam em direções contrárias
	* def::**Correlação**: statistical summary of the relationship between variables
		* **Pearson's correlation**: lida com relacionamentos lineares = $cov(X, Y) / (stdv(X) * stdv(Y))$
		* **Spearman's correlation**: lida com relacionamentos não-lineares = $cov(rank(X), rank(Y)) / (stdv(rank(X)) * stdv(rank(Y)))$
	* def::**Overfitting**: característica de um modelo que performa bem nos dados de treino, mas não generaliza bem para os dados de teste/uso real
		* **Causas**: { modelo muito complexo, poucos dados de treino, dados de treino desbalanceados, ruídos, atributos pouco relevantes }
		* **Soluções**: { usar modelo + simples, reduzir atributos, regularização, coletar + dados, diminuir ruídos, cross-validation, dropout, early stopping }
	* def::**Underfitting**: característica de um modelo que performa mal para os dados de treino
		* **Causas**: { modelo pouco complexo, dados insuficientes, atributos não representativos, regularização excessiva, erros de amostragem }
		* **Solução**: { usar modelo + complexo, obter melhores features, reduzir restrições do modelo }
	* def::**Bias**: parte do erro de um modelo causada por suposições incorretas do modelo
	* def::**Variância**: parte do erro de um modelo causada por sensibilidade excessiva do modelo
* **Coleta de dados**
	* def::**Crawling**: processo de rastreamento de conteúdos indexando
	* def::**Scrapping**: processo de extração de dados de páginas web, também conhecido como "raspagem"
	* { questionário, entrevista, anotação manual, monitoramento de redes sociais, observações }