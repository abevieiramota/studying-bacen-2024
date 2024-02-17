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
* **Scikit-learn**:  #TODO ver documentação, principais libs, classes, interfaces
* **HDF5**: "*Utilize the HDF5 high performance data software library and file format to manage, process, and store your heterogeneous data. HDF5 is built for fast I/O processing and storage.*"
* 