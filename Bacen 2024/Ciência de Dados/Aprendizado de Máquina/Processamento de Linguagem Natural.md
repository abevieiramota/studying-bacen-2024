* [[Grandes Modelos de Linguagem (LLM)]]

* Tasks
	* tradução automática
	* reconhecimento de fala
	* análise de sentimento
	* geração de texto
	* sumarização de texto
	* classificação de texto
	* extração de informações
* Problemas { ambiguidade/polissemia, diferenças de linguas, fonologia, análise morfológica/sintática, análise semântica/pragmática }
* Conceitos
	* corpus - conjunto de documentos em linguagem natural
	* gramática - especificação formal da linguagem
	* léxico - coleção de informações sobre palavras de uma linguagem (ex: OpLexicon, léxico de palavras para análise de sentimentos)
* pré-processamento
	* tokenização - divisão do texto em unidades, como palavras/símbolos
	* remoção de stop words - remoção de palavras com pouca semântica
	* normalização de texto - remoção de caracteres especiais, emojis, remoção de acentos etc
	* stemming - remoção de sufixos/prefixos para reduzir a raiz > reduz a complexidade do vocabulário (lematização tbm)
	* lematização - identificação de formas bases
	* part-of-speech tagging - identificação das funções das palavras na frase
	* detecção de entidades nomeadas
	* remoção de pontuação
	* correção ortográfica
	* remoção de palavras raras
	* substituição de sinônimos
	* expansão de abreviações
* representação
	* bag-of-words: representação do texto como um bag de tokens (map de palavras e quantidade); fácil de implementar; perde informação de ordem das palavras
	* tf-idf (term frequency-inverse documento frequency) - leva em consideração a frequência da palavra no texto (tf) e a frequência dela em todo o corpus (idf); representa a importância relativa da palavra no documento
	* word embeddings - representação de palavras em um espaço vetorial de alta dimensão
	* doc2vec - transforma texto em um vetor de numéricos que mantém certas informações