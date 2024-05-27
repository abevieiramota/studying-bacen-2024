* **De acordo com ter dados com soluções**:
	* def::**Aprendizado Supervisionado**: dados de treino contêm a solução/target
		* **Classificação**: algoritmos de aprendizado supervisionado cujo target é categórico
			* **Algoritmos**:
				* **Árvore de decisão**: algoritmo não-paramétrico que aprende um conjunto de regras de decisões simples usando os dados; essas decisões são estruturadas como uma árvore, com o procesos de decisão iniciando pela decisão raiz e seguindo até chegar em uma folha
					* quanto mais profunda a árvore, mais complexo o modelo
					* **V**:
						* interpretável, white-box ([exemplo de interpretação com scikit-learn](https://scikit-learn.org/stable/auto_examples/tree/plot_unveil_tree_structure.html#sphx-glr-auto-examples-tree-plot-unveil-tree-structure-py))
						* requer pouca preparação dos dados, não exigindo, por exemplo, normalização
						* o custo de usar é logarítmico em relação à quantidade de dados de treino
						* lida com dados numéricos e categóricos (!scikit-learn suporta apenas numérico)
						* permite validação do modelo com testes estatísticos
					* **DV**:
						* tendência a overfitting (!principalmente com alta quantidade de features em relação a samples) -> evita-se controlado { pruning, mínimo de samples nos nós folhas, máxima profundidade, dimensionality reduction }
						* não é bom com extrapolação (~a região de decisão é composta por diversas regiões de decisões com formato 'quadrado')
						* o treinamento de uma árvore ótima é NP-completo -> usam-se heurísticas para melhorar a performance, resultando em árvores subótimas -> mitiga-se usando ensembles
						* dificuldade para representar alguns conceitos, como XOR
						* cria modelos enviesados, caso haja classe dominante -> mitiga-se balanceando o dataset
					* Complexidade de treino: $O(n_{features} * n_{samples} * log(n_{samples}))$
					* Complexidade de uso: $O(log(n_{samples}))$
					* **Algoritmos**: { ID3, C4.5, CART }
					* next_step::ver no livro do Mitchell
				* **K-NN**: algoritmo não-paramétrico que seleciona k vizinhos mais próximos (função de distância) e decide, de acordo com a classificação deles, a classificação do ponto avaliado
					* Pode usar qualquer métrica de distância, como a distância Euclidiana - distância em linha reta
					* Instance-based learning -> apenas armazena os dados de treino e usa eles para classificar dados novos
					* O hiperparâmetro K, quanto maior, mais lida com ruído, mas, em contrapartida, "*makes the classification boundaries less distinct*"
					* No scikit-learn, por padrão, cada nó vizinho tem o mesmo peso na decisão; isso pode ser ajustado alterando o parâmetro `weights` de `uniform` para `distance`, dando maior peso para vizinhos mais próximos
					* Algoritmos para busca de vizinhos mais próximos:
						* **Brute-force**: complexidade $O(DN^2)$, sendo D a dimensionalidade/n_features, e N a quantidade de samples
						* **KD Tree**: faz uso da lógica "se A está muito longe de B e C está muito próximo de B, então A está muito longe de C" para melhorar a performance de busca por meio do uso de árvores, resultando numa complexidade $O(DN * log(N))$
						* **Ball Tree**: criado para lidar com cenários com alta dimensionalidade, em que KD Tree é ineficiente; faz uso de hyper-spheres, tendo maior custo de construção, mas menor custo de query
				* **Radius-NN**: similar ao K-NN, mas trabalha com um raio em torno do ponto, utilizando os samples dentro desse raio para gerar novas classificações
				* **SVM**: algoritmo paramétrico que utiliza hiperplanos, com margens equidistantes de exemplos da classe positiva e da classe negativa
					* kernel trick - função para projetar os dados num outro espaço
					* soft margin - permitir que haja exemplos na margem contrária (suaviza a restrição)
					* **V**:
						* adequado para alta dimensionalidade, mesmo quando o número de dimensões é superior ao número de samples
						* memory efficient
						* versátil, por meio de uso de kernel functions
					* **DV**:
						* com número de dimensões muito maior que número de samples, é preciso selecionar bem kernel function e aplicar regularização, para evitar overfitting
						* não provê estimativas de probabilidade
					* Complexidade de treino: entre $O(n_{features} * n_{samples}^2)$ e $O(n_{features} * n_{samples}^3)$
					* Classes no scikit-learn: { SVC, NuSVC, LinearSVC }
						* Tratam problemas multiclass usando a abordagem "one-versus-one", criando $\frac{n (n - 1)}{2}$ classificadores
						* Possuem hiperparâmetro C, que controla regularização (quanto menor, maior a regularização)
				* **Random Forest**: ensemble de árvores de decisão, gerados segunido uma estratégia de "perturb-and-combine", adicionando fator aleatório ao treinamento de cada árvore, feito com amostra com reposição dos dados de treino (bootstrap sample); os fatores aleatórios adicionam variance ao modelo de árvore de decisão
				* **Stochastic Gradient Descent** (SGD) Classifier: algoritmo que trabalha com otimização de funções convexas, amplamente utilizado em problemas de classificação de texto/NLP, por escalar bem para datasets esparsos
					* **V**: { eficiência, facilidade de desenvolvimento (o que traz mais facilidade de otimização) }
					* **DV**: { exige boa definição de hiperparâmetros (regularização, número de iterações), sensível a feature scaling (recomenda-se escalar todas as features para a mesma escala) }
					* Complexidade de treino: $O(knp')$ onde k = número de iterações/epochs, n é o número de samples, p' é o número médio de atributos não-zero
				* **Logistic Regression** (logit regression, Maximum-entropy classification): usa a função logística $\frac{1}{1 + e^{-x}}$, range (0, 1)
					* multiclasse - calcula a probabilidade de cada classe separadamente
					* regressão logística ordinal - classes com ordem
				* **Naive Bayes**: algoritmos baseados no teorema de Bayes, que tem como premissa a independência entre cada par de feature (daí o "naive"); $P(y\ |\ x) = \frac{P(y)P(x\ |\ y)}{P(x)}$ 
			* **Métricas**:
				* **Acurácia**: $\frac{TP + TN}{TP + TN + FP + FN}$
				* **Confusion matrix**:
					* **Precision**: $\frac{TP}{(TP + FP)}$
					* **Recall** (sensibilidade, revocação): $\frac{TP}{(TP + FN)}$
						* precision/recall tradeoff (Aurelion p. 95)
						* precision-recall curve (Aurelion p. 97, pegar imagem)
					* **F-Score**: $harmonic\_mean(precision, recall)$
						* harmonic_mean gives much more weight to low values (arithmetic mean treats all values equally)
						* The F1 score favors classifiers that have similar precision and recall
					* **ROC Curve Area Under the Curve** (ROC AUC) { ROC = TPR/FPR } 
						* ROC tradeoff "*Once again there is a tradeoff: the higher the recall (TPR), the more false positives (FPR) the classifier produces*"
						* ROC AUC -> perfect classifier = 1, random classifier ~ 0.5
			* def::**Multiclass**: problema de classificação em que o target tem domínio com mais de 2 valores possíves; ex: classificação de imagens de números
			* def::**Multilabel**: problema de classificação em que o target envolve mais de um valor; ex: identificação de pessoas em foto
		* **Regressão**: algoritmo de aprendizado supervisionado cujo target é numérico ordinal
			* **Modelos**:
				* **Regressão Linear**: reta que denota correlação entre variáveis; minimiza o resíduo quadrático (resíduo = correto - predito); reg linear múltipla (>1 variável independente)
					* def::**Multicolinearidade**: característica de duas features que se encontram altamente correlacionadas -> afeta a qualidade do modelo e dificulta a interpretação dos resultados
						* "*Por exemplo, imagine que você queira estimar o efeito da escolaridade e renda na satisfação com a vida. Aqui no Brasil, renda e escolaridade são altamente correlacionadas. Isso pode dificultar a interpretação dos resultados do modelo, uma vez que a contribuição de cada variável para explicar a variável dependente fica menos clara.*" [fonte](https://www.blog.psicometriaonline.com.br/o-que-e-multicolinearidade)
					* **Complexidade de treinamento**: $O(n_{samples} n_{features}^2)$, assumindo n_samples >= n_features; complexidade de um SVD na matriz (samples, features)
					* **Variações**:
						* **Ridge**: regressão linear com imposição de penalidade (norma L2) sobre os coeficientes; "*The ridge coefficients minimize a penalized residual sum of squares*", com parâmetro $\alpha$ controlando o "encolhimento" dos pesos (quanto maior $\alpha$, menor liberdade para os pesos); tem mesma complexidade da regressão linear ordinária
						* **Lasso**: regressão linear com imposição de penalidade (norma L1) sobre os coeficientes; tende a estimar pesos esparsos, útil em contextos em que faça sentido reduzir o número de features das quais o modelo é dependente -> ex: compressão, seleção de features
						* **Elastic-Net**: combina a regularização com normas L1 (Lasso) e L2 (Ridge), com hiperparâmetro para determinar o peso de cada regularização (no scikit-learn, parâmetro `l1_ratio`)
				* Redes neurais
				* Árvore de decisão - CART
				* **SVR** (Support Vector Regression): SVM adaptado para regressão
			* Métricas de performance { Root Mean Square Error (RMSE) } #TODO há mais?
	* **Não Supervisionado** { dados de treino não contêm a solução, unlabeled }
		* **Clustering** - tarefa descritiva!
			* distância intra-cluster minimizada; distância inter-cluster maximizada (! cuidado, se falar em 'similaridade', é o inverso)
			* depende de medida de proximidade, critério de agrupamento
			* importante dados na mesma escala
			* Modelos - particionais - divide em k grupos
				* K-means - fixa k centróides de maneira aleatória, um para cada cluster; associa os pontos ao centróide mais próximo e calcula o novo centróide
					* funciona bem quando os clusters são esféricos e bem separados, com volumes aproximadamente iguais, com quantidades semelhantes de pontos
			* Modelos - hierárquicos - forma árvore/dendograma; bottom-up/aglomerativo ou top-down/divisivo
				* Agglomerative Hierarchical Clustering
				* Hierarchical Cluster Analysis (HCA)
			* Modelos - density-based
				*  DBSCAN #TODO 
		* **Anomaly Detection** { One-class SVM, Isolation Forest } #TODO ver em contexto de fraud detection
		* **Visualization** { Principal Component Analysis (PCA), Locally-Linear Embedding (LLE), t-distributed Stochastic Neighbor Embedding (t-SNE) }
		* **Redução de dimensionalidade** - reduzir o número de variáveis do dataset mantendo o máximo possível de informações
			* Seleção de atributos - seleciona atributos
				* LDA (Linear Discriminant Analysis) - Análise Discriminante Linear
			* Extração de atributos - transforma em novos
				* PCA - Análise de Componentes Principais - novos atributos gerados ordenados de acordo com a variância #TODO como avaliar o resultado dos autovalores gerados
		* **Association Rule Learning** - regra que associa dois ou mais elementos
			* Apriori #TODO
				* suporte = *proporção* de vezes que a regra aparece na base
				* confiança = proporção de vezes em que os dois aparecem juntos, em relação às vezes em que o antecedente aparece
			* Eclat #TODO
			* Partition
			* FP-Growth #TODO
	* **Semi Supervisionado** { parte dos dados com e sem solução }
		* Deep Belief Networks (DBNs)
	* **Por Reforço** { baseado em agentes, que observam ambiente, executam ações e avaliam reward/penality }
	* **Por Transferência**
		* Muito usado em [[Grandes Modelos de Linguagem (LLM)]]
		* Uma forma é inicializar uma rede usando pesos de outra rede treinada para outro problema
* **De acordo com se aprende on the fly** 
	* Batch { high resource consumption, necessidade de retrain }
	* Online { bom para sistema de stream, que precisa adaptar rapidamente, que tem pouco recurso }
		* desafio - garantir que não serão utilizados dados de baixa qualidade, corrompendo o modelo
* **De acordo com se só compara novo dado com dados da base, ou se extrai padrões**
	* instance-based
	* model-based
* def::**Ensemble**: "*combine the predictions of several base estimators built with a given learning algorithm in order to improve generalizability / robustness over a single estimator.*" ([scikit-learn](https://scikit-learn.org/stable/modules/ensemble.html#ensembles-gradient-boosting-random-forests-bagging-voting-stacking))
	* def::**Bagging**: estratégia de ensemble que treina um conjunto de modelos, usando um estimador base, usando amostras com reposição dos dados de treino, de forma a ganhar variância em relação ao estimador base
	* def::**Stacked generalization**: estratégia de ensemble que utiliza estimadores base, cujos resultados são passados como features para um estimador final, que calcula a predição
	* def::**AdaBoost**: "*The core principle of AdaBoost is to fit a sequence of weak learners (i.e., models that are only slightly better than random guessing, such as small decision trees) on repeatedly modified versions of the data. The predictions from all of them are then combined through a weighted majority vote (or sum) to produce the final prediction. The data modifications at each so-called boosting iteration consists of applying weights to each of the training samples. Initially, those weights are all set to, so that the first step simply trains a weak learner on the original data. For each successive iteration, the sample weights are individually modified and the learning algorithm is reapplied to the reweighted data. At a given step, those training examples that were incorrectly predicted by the boosted model induced at the previous step have their weights increased, whereas the weights are decreased for those that were predicted correctly. As iterations proceed, examples that are difficult to predict receive ever-increasing influence. Each subsequent weak learner is thereby forced to concentrate on the examples that are missed by the previous ones in the sequence*" ([scikit-learn](https://scikit-learn.org/stable/modules/ensemble.html#adaboost))
	* Estratégias para decidir a classificação a partir de um ensemble: { majority (hard voting), weighted average probabilities (soft voting) }
	* 
* Sampling

Ensemble/boosting #TODO (já caiu AdaBoost)