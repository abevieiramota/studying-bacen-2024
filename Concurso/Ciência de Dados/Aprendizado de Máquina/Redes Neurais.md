[[Deep Learning]]

#TODO revisar e organizar, consultando outro material

Aurelion cap 10
* ANN são a base de Deep Learning, versátil, poderoso, escalável
* Perceptron, single layer de Threshold Logic Unit (ou Linear Threshold Unit), cada unidade calcula a soma ponderada das entradas e aplica uma step function (ex: 0, if z < 0; 1 else)
	* há prova de que o algoritmo de treinamento converge, caso os dados de treino sejam linearmente separáveis
* Multi-Layer Perceptron - multiplas (camadas de) Perceptron, consegue tratar problemas não lineares
	* Quando tem muitas camadas = Deep Neural Network
	* usa função logística (permite gradiente)
* fully connected layer/dense layer - todas unidades de uma camada conectadas a outra camada
* input layer > hidden layers > output layer 
	* input e hidden layers contêm uma unidade de bias (retorna 1 sempre)
	* pesos inicializados randomicamente
	* a função de ativação não precisa ser igual na rede toda
	* softmax activation function -> garante que todos os inputs são mapeados para o range [0, 1] e que a soma deles é igual a 1
* Hiperparâmetros { nº de hidden layers, epochs, learning rate, batch size, loss function, activation function, optimizer }
* Treinamento
	* reforço de conexões que reduzem erro - "*For every output neuron that produced a wrong prediction, it reinforces the connection weights from the inputs that would have contributed to the correct prediction.*"
	* backpropagation - "*it can find out how each connection weight and each bias term should be tweaked in order to reduce the error.*"
		* mini-batch
		* cada passagem pela base toda = epoch, roda várias epochs
		* "*for each training instance the backpropagation algorithm first makes a prediction (forward pass), measures the error, then goes through each layer in reverse to measure the error contribution from each connection (reverse pass), and finally slightly tweaks the connection weights to reduce the error (Gradient Descent step)*"


* Funções de ativação #anki
	* limiar = 0, se x < 0, 1, se x >= 0 (não traz não-linearidade, útil para aprender relações não lineares)
	* !Sigmoide/logistic = 1 / (1 + e^-x); range (0, 1)
	* Softmax = generalização da sigmoid para casos não binários, usada na camada de saída, gerando probabilidades por classes
	* Hyperbolic tangent = (e^x - e^-x) / (e^x + e^-x); range (-1, 1)
	* ReLU (Rectified Linear Unit) = max(0, x); range [0, oo)
	* Maxout = maior valor que entrou
	* Função Gaussiana = usada com rede RBF
	* parcialmente diferenciáveis { degrau, sinal, rampa simétrica }
* questões que peçam para calcular resultado de rede neural -> cuidado para aplicar a função de ativação em todas as saídas!
