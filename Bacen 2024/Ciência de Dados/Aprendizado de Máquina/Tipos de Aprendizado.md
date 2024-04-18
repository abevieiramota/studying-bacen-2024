#TODO ler brevemente sobre os principais algoritmos e tomar nota em cards separados
#TODO ler sobre as métricas de performance

* **De acordo com ter dados com soluções**
	* **Supervisionado** { dados de treino contêm a solução }
		* Classificação - modelos:
			* Árvore de decisão #TODO
			* k-NN - seleciona k vizinhos mais próximos (função de distância) e decide, de acordo com a classificação deles, a classificação do ponto avaliado; não-paramétrico!
				* distância euclidiana - distância em linha reta
			* SVM - classificação binária ou regressão; utiliza hiperplanos, com margens equidistantes de exemplos da classe positiva e da classe negativa
				* kernel trick - função para projetar os dados num outro espaço
				* soft margin - permitir que haja exemplos na margem contrária (suaviza a restrição)
			* Random Forest - classificação e regressão #TODO
			* Stochastic Gradient Descent (SGD) Classifier
			* Logistic Regression - usa a função logística 1/(1 + e^-x), range (0, 1)
				* multiclasse - calcula a probabilidade de cada classe separadamente
				* regressão logística ordinal - classes com ordem
			* Naive Bayes - P(A | B) = P(B | A) * P(A)/P(B), assume que há independência dos dados
		* Métricas de performance
			* acurácia
			* confusion matrix #anki
				* precision = TP/(TP + FP)
				* recall (sensibilidade, revocação) = TP/(TP + FN)
					* precision/recall tradeoff (Aurelion p. 95)
					* precision-recall curve (Aurelion p. 97, pegar imagem)
				* F-Score = harmonic_mean(precision, recall)
					* harmonic_mean gives much more weight to low values (arithmetic mean treats all values equally)
					* The F1 score favors classifiers that have similar precision and recall
				* ROC Curve Area Under the Curve (ROC AUC) { ROC = TPR/FPR } 
					* ROC tradeoff "*Once again there is a tradeoff: the higher the recall (TPR), the more false positives (FPR) the classifier produces*"
					* ROC AUC -> perfect classifier = 1, random classifier ~ 0.5
		* Multiclass - ex: classificação de imagens de números
			* Multilabel - ex: identificação de pessoas em foto
		* Regressão - previsão de valor numérico contínuo
			* Modelos
				* Regressão Linear - reta que denota correlação entre variáveis; resíduo = correto - predito; reg linear múltipla (>1 variável independente)
					* coeficiente de pearson - medida de correlação [-1, 1]
				* Redes neurais
				* Árvore de decisão - C4.5 #TODO
				* SVM
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
			* Eclat
			* Partition
			* FP-Growth
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

Ensemble/boosting #TODO (já caiu AdaBoost)