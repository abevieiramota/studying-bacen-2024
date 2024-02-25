* **Keras**: high-level deep learning API, usando como backend libs como { TensorFlow, Microsoft Cognitive Toolkit (CNTK), Theano }
	* há implementações para diversas plataformas, como browser, em javascript
	* modularidade, extensibilidade
	* model = keras.models.Sequential() - rede com camadas sequencialmente conectadas
	* model.add(keras.layers.Flatten(input_shape=[28, 28]))
	* model.add(keras.layers.Dense(100, activation="relu")) - camada com pesos
	* model.add(keras.layers.Dense(10, activation="softmax")) - output layer, softmax para ter output com valores exclusivos (classificação)
	* model.summary() - overview da rede
	* model.layers - lista de layers
	* model.compile(loss, optimizer, metrics)
	* model.fit(X, y, epochs, validation_data)
* **TensorFlow**: permite criar grafos de fluxo de dados, com nós de processamento (operators) e arestas entre eles (tensor)
	* funciona com diversas linguagens, como Python, C++, Java
	* abstração, tensor board, eager execution (para debugar, com tf 2.0 ativa com `tf.executing_eagerly()`)
* **PyTorch**: biblioteca de aprendizado de máquina de código aberto para Python
	* API/interface fácil, grafos computacionais, fácil de depurar/entender, grande parte da execução é feita em C++ e CUDA (API para computação paralela com GPU)
* **Scikit-learn**:
	* sklearn.base { BaseEstimator, ClassifierMixin, ... }
	* sklearn.cluster { DBSCAN, KMeans, ... }
	* sklearn.datasets { fetch_, load_, make_, ... }
	* sklearn.decomposition { PCA, ... }
	* sklearn.dummy { DummyClassifier/Regressor }
	* sklearn.ensemble { RandomForest, AdaBoost, ... }
	* sklearn.feature_extraction { DictVectorizer, ..., image { img_to_graph, ... }, text { CountVectorizer, TfidfTransformer, ...}, ... }
	* sklearn.feature_selection { SelectKBest, ... }
	* sklearn.impute { SimpleImputer, MissingIndicator, KNNImputer, ... }
	* sklearn.linear_model { LogisticRegression, Perceptron, RidgeClassifier, LinearRegression, Ridge, Lasso, ... }
	* sklearn.metrics { accuracy_score, auc, confusion_matrix, f1_score, precision_recall_curve, r2_score, mean_squared_error, silhouette_score, pairwise { euclidean_distances, manhattan_distances, ... }, ... }
	* sklearn.model_selection { KFold, LeaveOneOut, StratifiedKFold, GridSearchCV, cross_val_score, ... }
	* sklearn.naive_bayes { GaussianNB, MultinomialNB, ... }
	* sklearn.neighbors { KDTree, KNeighborsClassifier/Regressor, ... }
	* sklearn.neural_network { BernoulliRBM, MLPClassifier/Regressor }
	* sklearn.pipeline { FeatureUnion, Pipeline, make_pipeline, ... }
	* sklearn.preprocessing { LabelEncoder, MinMaxScaler, Normalizer, OneHotEncoder, PolynomialFeatures, StandardScaler, normalize, ... }
	* sklearn.svm { SVC, SVR, LinearSVC, ... }
	* sklearn.tree { DecisionTreeClassifier/Regressor, ... }
* **HDF5**: "*Utilize the HDF5 high performance data software library and file format to manage, process, and store your heterogeneous data. HDF5 is built for fast I/O processing and storage.*"
* 