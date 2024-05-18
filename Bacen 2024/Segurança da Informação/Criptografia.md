* **Motivação**: comunicação confidencial, por meio de embaralhamento/ofuscação das informações 
	* em alguns casos, é possível obter também autenticidade e integridade
* **Conceitos**:
	* **Criptoanálise**: estudo de quebra/decifração de mensagens criptografradas
	* **Criptologia**: estudo sobre criptografia e criptoanálise
	* **Cifra**: ==método== de codificação de mensagens
	* **Computacionalmente seguro**: com o poder computacional disponível, o risco de a informação ser decifraca e isso gerar prejuízo é baixo
	* **Cifragem de bloco** (Cipher Block): aplica a cifra sobre blocos de dados de tamanho fixo
	* **Cifragem de fluxo**: aplica a cifra bit a bit
* **Métodos de cifragem**:
	* **Substituição**: usa um mapa de substituição
	* **Transposição**: troca a posição dos dados
	* **Esteganografia**: oculta informação dentro de outroa (como esconder bits numa imagem)
* **Métodos de decifragem**:
	* **Recuperação direta**: busca obter a chave diretamente
	* **Força bruta**
	* **Método de dicionário**: retringe o conjunto de valores a serem testados e daí aplica força bruta
* **Métodos de cifra de bloco**:
	* **Eletronic Code Book** (ECB): simples, o processamento de cada bloco é independente (permite paralelização), fragmentação da mensagem não randômica
		* blocos de 64 bits
		* não seguro, por causar repetições (determinístico)
		* sujeito a análise de comportamento de dados
		* dada a independência dos blocos, erro em um bit causa problema apenas no bloco a que pertence
	* **Cypher Block Chaining** (CBC): método mais utilizado, utiliza operações XOR, a cifragem de um bloco depende da cifragem de todos os blocos anteriores
		* faz uso de um seed/vetor de inicialização, que precisa ser conhecido pelas duas partes
		* depende da recepçãop dos blocos de maneira sequencial (pode impactar na rede, porque vai precisar aguardar chegada de blocos anteriores, caso cheguem fora de ordem)
		* erros se propagam
	* **Cipher FeedBack** (CFB): muito utilizado, suporta qualquer tamanho de entrada, usado para quando há necessida de transmissão imediata
		* depende da recepção sequencial dos blocos
		* performance melhor que o CBC
	* **Outros**: Output Feedback (OFB), Counter (CTR)
* **Cifra de fluxo** - Stream Cypher: não necessita aguardar o processamento de toda a mensagem, dinâmico/ágil, aplicação de algoritmo de forma contínua
	* amplamente difundido em transmissão de mídias
	* pode-se usar um buffer e processar em janelas
* **Criptoanálise**: 
	* Única cifragem incondicionalmente segura é OTP, modelo apenas teórico
	* Trabalhas-se com cifras computacionalmente seguros
	* **Tipos**:
		* **Apenas texto cifrado** - Cypher Text-Only: o analista tem acesso apenas ao texto cifrado
		* **Texto claro conhecido** - Known-plaintext: o analista tem pares de texto cifrado e texto claro
		* **Texto claro escolhido** - Choosen Plain Text: o analista é capaz de gerar novos pares de texto claro e texto cifrado
		* **Texto cifrado escolhido** - Choosen Cypher Text: o analista é capaz de, a partir de um texto cifrado, gerar o texto claro
		* **Texto escolhido** - Chosen Text: há plena capacidade de gerar texto cifrado a partir de claro e vice-versa
	* **Métodos**:
		* **Recuperação direta**: obtém a senha/segredo de maneira direta
		* **Pré-computado**: usa uma lista extensa pré-computada de pares de texto claro e texto cifrado, buscando matches; quanto maior a chave, maior o custo computacional para gerar essas tabelas
		* **Força bruta**: alto custo de processamento, matematicamente é infalível
		* **Dicionário**: misto de pré-computador com força bruta
		* **Probabilístico**: faz uso de estatísticas de sequência de dados, como de caracteres em texto numa língua
* Criptografia simétrica ^def-criptografia-simetrica
* Criptografia assimétrica ^def-criptografia-assimetrica
	* criptografia de chave pública
	* Algoritmos { RSA, Diffie-Hellman etc }
* **Ferramentas de criptografia**: { Bitlocker, Veracypt, Diskcryptor, GNUpg, Apple disk image }