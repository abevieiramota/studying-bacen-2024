#lvl1
#TODO ler brevemente sobre os principais algoritmos e tomar nota em cards separados
#TODO ler sobre as métricas de performance

* **De acordo com ter dados com soluções**
	* Supervisionado { dados de treino contêm a solução }
		* Classificação {  k-NN, SVM, Random Forest, Stochastic Gradient Descent (SGD) Classifier }
			* Métricas de performance { acurácia, confusion matrix { precision = TP/(TP + FP), recall = TP/(TP + FN), F-Score = harmonic_mean(precision, recall) },  }
				* harmonic_mean gives much more weight to low values (arithmetic mean treats all values equally)
				* The F1 score favors classifiers that have similar precision and recall.
				* precision/recall tradeoff (Aurelion p. 95)
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
* De acordo com se aprende on the fly 
	* Batch { high resource consumption, necessidade de retrain }
	* Online { bom para sistema de stream, que precisa adaptar rapidamente, que tem pouco recurso } ! desafio - garantir que não serão utilizados dados de baixa qualidade, corrompendo o modelo
* De acordo com se só compara novo dado com dados da base, ou se extrai padrões
	* instance-based
	* model-based