Aurelion ch 11

* [[IA Generativa]]
* Transformers, redes convolucionais #TODO
* [[Grandes Modelos de Linguagem (LLM)]]

Arquiteturas
* Perceptron - uma camada
* Feed-Forward Network - multilayer
* Recurrent Neural Networks (RNNs) - para uso com dados sequenciais, de tamanho não fixo, como NLP
	* lembra o que foi visto no passado e aplica em predições futuras
	* tem estado interno que é atualizado com o input e passado também como input
* Long Short Term Memory Network (LSTM) - adiciona memória, permitindo 'lembrar' o que foi visto várias iterações anteriores, usando gates 
* Transformer Neural Network - RNN e LSTM são lentos para longas sequências de dados -> encoder-decoder structure que permite paralelização
* Convolutional Neural Networks (CNNs) - usado em processamento de imagens, NLP; camadas convolucionais, vão extraindo padrões cada vez mais alto nível { filters, pooling }
* Deconvolutional Neural Network (DNNs)
* Unsupervised Pretrained Networks
	* Autoencoders - usado para aprender codificação compacta de dados não rotulados
	* Deep Belief Networks (DBNs) - camadas de Restricted Boltzmann Machines (RBMs) para pretreino
	* Generative Adversarial Network (GAN) - geração de dados a partir de padrões identificados no input; unsupervised; { generator x discriminator - competitive }
* ResNet - dados de camadas são passados pulando camadas

Problemas comuns
* Vanishing/Exploding gradients - os gradientes vão se tornando menores a medida que vão chegando nas menores camadas, eventualmente deixando de alterá-las; ou o contrário, com gradientes ficando cada vez maiores;
	* ténicas para evitar esses problemas envolvem o controle da inicialização randômica dos pesos da rede; limitar os valores de gradientes; 
* overfitting
	* regularization - limita os valores dos pesos { L1 - estimula pesos esparsos (alguns 0), usada para seleção de features; L2 - estimula pesos pequenos } #anki
	* dropout - a cada iteração de treino, cada neurônio (exceto output layer) tem uma probabilidade de ser desconsiderado na iteração