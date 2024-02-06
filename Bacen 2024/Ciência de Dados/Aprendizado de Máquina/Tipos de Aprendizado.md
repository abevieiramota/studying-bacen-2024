#lvl1
#TODO ler brevemente sobre os principais algoritmos e tomar nota em cards separados
#TODO ler sobre as métricas de performance

* **De acordo com ter dados com soluções**
	* Supervisionado { dados de treino contêm a solução }
		* Classificação {  k-NN, SVM, Random Forest, Stochastic Gradient Descent (SGD) Classifier, Naive Bayes }
			* Métricas de performance { acurácia, confusion matrix { precision = TP/(TP + FP), recall = TP/(TP + FN), F-Score = harmonic_mean(precision, recall) },  ROC Curve Area Under the Curve (ROC AUC) { ROC = TPR/FPR } }
				* harmonic_mean gives much more weight to low values (arithmetic mean treats all values equally)
				* The F1 score favors classifiers that have similar precision and recall.
				* precision/recall tradeoff (Aurelion p. 95)
				* precision-recall curve (Aurelion p. 97, pegar imagem)
				* ROC tradeoff "*Once again there is a tradeoff: the higher the recall (TPR), the more false positives (FPR) the classifier produces*"
				* ROC AUC -> perfect classifier = 1, random classifier ~ 0.5
			* multiclass - ex: classificação de imagens de números
			* multilabel - ex: identificação de pessoas em foto
		* Regressão { Lasso, Linear Regression, Ridge }
			* Métricas de performance { Root Mean Square Error (RMSE) }
	* Não Supervisionado { dados de treino não contêm a solução, unlabeled }
		* Clustering { K-means, DBSCAN, Hierarchical Cluster Analysis (HCA) }
		* Anomaly Detection { One-class SVM, Isolation Forest }
		* Visualization { Principal Component Analysis (PCA), Locally-Linear Embedding (LLE), t-distributed Stochastic Neighbor Embedding (t-SNE) }
		* Association Rule Learning { Apriori, Eclat }
	* Semi Supervisionado { parte dos dados com e sem solução }
		* Deep Belief Networks (DBNs)
	* Por Reforço { baseado em agentes, que observam ambiente, executam ações e avaliam reward/penality }
	* Por Transferência
		* Muito usado em [[Grandes Modelos de Linguagem (LLM)]]
		* Uma forma é inicializar uma rede usando pesos de outra rede treinada para outro problema
* De acordo com se aprende on the fly 
	* Batch { high resource consumption, necessidade de retrain }
	* Online { bom para sistema de stream, que precisa adaptar rapidamente, que tem pouco recurso } ! desafio - garantir que não serão utilizados dados de baixa qualidade, corrompendo o modelo
* De acordo com se só compara novo dado com dados da base, ou se extrai padrões
	* instance-based
	* model-based