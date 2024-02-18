* [[Tipos de Aprendizado]]
* [[Redes Neurais]]
* [[Processamento de Linguagem Natural]]
* [[Tools]]

* **Definições**
	* 1959, Arthur Samuel - '*Machine Learning is the field of study that gives computers the ability to learn without being explicitly programmed.*'
	* 1997, Tom Mitchell - '*A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E.*'
* Por que usar?
	* problema envolve muitas regras ou regras com mudança frequente (ex: spam filter)
	* problema muito complexo para outras abordagens ou não tem solução com algoritmo conhecido (ex: speech recognition)
* Análise { descritiva, diagnóstica, preditiva, prescritiva }
* Desafios
	* poucos dados de treino
	* dados pouco representativos { amostra pequena, amostra enviesada }
	* dados com baixa qualidade { outliers, missing values, wrong values }
	* irrelevant features
* Overfitting/Underfitting
	* Overfitting - modelo performa bem no treino, mas não generaliza bem
		* causas { modelo muito complexo, poucos dados de treino, dados de treino desbalanceados, ruídos, atributos pouco relevantes }
		* soluções { usar modelo + simples, reduzir atributos, regularização, coletar + dados, diminuir ruídos, validação cruzada, dropout, early stopping }
	* Underfitting - modelo muito simples para aprender o padrão dos dados
		* causas { modelo pouco complexo, dados insuficientes, atributos não representativos, regularização excessiva, erros de amostragem }
		* solução { usar modelo + complexo, obter melhores features, reduzir restrições do modelo }
* Teste e validação
	* não validar -> jogar em produção e validar com usuários -> ruim
	* dividir dados em base de treino, teste e validação -> treina, avalia com teste, seleciona o melhor modelo/hiperparâmetros e finalmente avalia com validação
* Bias - erro por suposições incorretas do modelo
* Variância - erro por sensibilidade excessiva do modelo
* Processo
	* [CRISP-DM](https://docs.google.com/presentation/d/18mJD0kUBMCaQDzhhJb-CLZsmjjjCWG5KsQUCFcvGtU0/edit?usp=sharing) #TODO
	* Data cleaning #TODO
		* OneHotEncoding
		* Normalization -> transforma para range [0, 1]
			* (x - min)/(max - min)
		* Standardization -> transforma para distribuição normal (menos afetado por outlier)
			* (x - mean)/std
* Conceitos #TODO
	* Correlação
	* Cross-validation
* Coleta de dados
	* Crawling - rastrear conteúdos indexando
	* Scrapping - extrair dados de páginas web (raspagem)
	* { questionário, entrevista, anotação manual, monitoramento de redes sociais, observações }