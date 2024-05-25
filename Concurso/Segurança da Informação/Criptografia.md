* **Motivação**: comunicação confidencial, por meio de embaralhamento/ofuscação das informações 
	* em alguns casos, é possível obter também autenticidade e integridade
* **Conceitos**:
	* **Criptoanálise**: estudo de quebra/decifração de mensagens criptografradas
	* **Criptologia**: estudo sobre criptografia e criptoanálise
	* **Cifra**: ==método== de codificação de mensagens
	* **Computacionalmente seguro**: com o poder computacional disponível, o risco de a informação ser decifraca e isso gerar prejuízo é baixo
	* **Cifragem de bloco** (Cipher Block): aplica a cifra sobre blocos de dados de tamanho fixo
	* **Cifragem de fluxo**: aplica a cifra bit a bit
	* **Princípio de Kerckoff**: o algoritmo deve ser público, a robustez da criptografia vem da confidencialidade da chave
	* **Princípios de Shannon**:
		* **Difusão**: busca tornar o relacionamento estatístico entre o texto claro e o texto cifrado o mais complexo possível
		* **Confusão**: busca tornar o relacionamento entre o texto cifrado e o valor da chave de criptografia o mais complexo possível
	* **Salt**: recurso para contornar problemas de prefixo; acrescenta-se um prefixo variável à entrada, diminuindo a probabilidade de colisões; recurso nativo no Linux
* **Métodos de cifragem**:
	* **Substituição**: usa um mapa de substituição
	* **Transposição**: troca a posição dos dados
	* **Esteganografia**: oculta informação dentro de outroa (como esconder bits numa imagem)
	* !cuidado, algumas bancas costumam a associar substituição com criptografia simétrica, transposição com criptografia assimétrica (mas não há essa exclusividade de métodos)
* **Métodos de decifragem**:
	* **Recuperação direta**: busca obter a chave diretamente
	* **Força bruta**
	* **Método de dicionário**: retringe o conjunto de valores a serem testados e daí aplica força bruta
* **Métodos de cifra de bloco**:
	* **Eletronic Code Book** (ECB): simples, o processamento de cada bloco é independente (permite paralelização), fragmentação da mensagem não randômica
		* blocos de 64 bits (!cuidado, não são kbits)
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
* **Criptografia simétrica**: criptografia que faz uso de 1 chave apenas para o processo de criptografia e descriptografia ^def-criptografia-simetrica
	* anki::!Visa garantir apenas o princípio da ==confidencialidade== (!cuidado, CESPE considera que garante também autenticidade)
	* como boa prática, normalmente usa-se compressão antes da encriptação
		* reduz o volume de dados a cifrar
		* dificulta o processo de criptoanálise
		* reduz o volume de dados a transferir/processar
	* chaves normalmente menores que nas chaves assimétricas ~256 bits (atualmente, 256 bits é computacionalmente seguro), enquanto nas assimétricas há chaves ~4k bits
	* por isso, normalmente usa-se criptografia simétrica para troca de conteúdo (maior volume) e a assimétrica para troca de chaves
	* **Algoritmos**:
		* **DES** (Data Encryption Standard): criado pela IBM e foi utilizado por muitos anos
			* Chave de 64 bits (sendo que só 56 bits são usados para definir a chave efetiva, com 8 bits para flags) + bloco de 64 bits
			* Quebrado em 1997 por força bruta em desafio do NIST
			* Utiliza cifra de bloco, usando técnicas de substituição e permutação
			* n_entendi::Utiliza conceito de "S-BOXES"
			* next_step::Faz uso de rede/cifra de Feistel: vai gerando chaves parciais, derivadas da chave, cada uma sendo usada em cada uma das 16 rodadas/rounds
		* **3-DES**: derivado do DES, aplica 3 rodados do fluxo principal
			* Chave de 192 bits, com força de 56 \* 3 = 168 bits (lembrar dos 8 bits em cada chave para flags)
				* pode utilizar apenas 2 chaves, com força de 112 bits
			* roda o processo de criptografia com uma chave, descriptografia com outra chave, criptografia com outra chave (Encrypt-Decrypt-Encrypt)
			* next_step::ler mais sobre DES e 3-DES
		* **RC** (Rivest Cipher):
			* Versões {  4, 5, 6 }
			* **RC4**:
				* Orientado a byte (trabalha byte a byte)
				* Tamanho de chave variável até 2048 bits
				* Trabalha com cifra de fluxo, byte a byte -> bom para fluxos contínuos, como mídia
				* Muito utilizado no protocolo de segurança TLS
				* Estrutura simples, com robustez na geração de sequências pseudoaleatórias
			* **RC5**: 
				* Cifra de bloco (!cuidado, diferente do RC4, que é cifra de fluxo)
				* Bloco de tamanho variável { 32, 64, 128 } bits
				* Tamanho de chave variável até 2048 bits
				* Quantidade de rodadas variáveis até 255
			* **RC6**:
				* Baseado no RC5 (logo, cifra de bloco)
				* Tem performance melhor que RC5, por uso de registradores de 4 bits para multiplicação
		* **AES** (Advanced Encryption Standard): principal protocolo utilizado atualmente, criado em substituição ao DES
			* Bloco fixo de 128 bits (!cuidado, o tamanho do bloco é fixo, mas o tamanho das chaves é variável)
			* Tamanho de chave variável { 128, 192, 256 } bits ~ { 10, 12, 14 } rodadas
			* No lugar da rede de Feistel, usa o algoritmo Rjindael
			* **Estrutura básica**: três estágios de substituição { SubBytes, MixColumns, AddRoundKey } e um de permutação { ShiftRows }
				* **SubBytes**: substituição byte a byte de acordo com uma tabela
				* **ShiftRows**: permutação simples
				* **MixColumns**: combinação lienar que utiliza aritmética sobre corpo finito
				* **AddRoundKey**: XOR bit a bit do bloco atual com uma parte da chave expandida
				* next_step::Estágios/estrutura do AES
* **Criptografia assimétrica** (ou de chave pública): criptografia que faz uso de 2 chaves, uma para criptografar e outra para descriptografar, base para assinaturas e [[Assinatura digital e Certificado digital|certificados digitais]] ^def-criptografia-assimetrica
	* **Conceitos**:
		* **chave privada**: conhecida apenas pelo dono
		* **chave pública**: amplo conhecimento
		* é computacionalmente inviável (não quer dizer que é impossível!) de, dado um par de chaves, descobrir uma a partir da outra
	* A depender da forma de uso das chaves, alcança-se aplicações diferentes
		* anki::**Confidencialidade**: emissor criptografa com a chave pública do destinatário e ele descriptografa com a chave privada correspondente (daí só quem recebe pode descriptografar, garantindo confidencialidade)
			* utilizado na troca de chaves simétricas entre pares à distância e sem se encontrarem
			* foco nas chaves do destinatário
		* anki::**Autenticidade**: criptografa com a privada do emissor e o destinatário descriptografa com a pública do emissor (daí qualquer um poderá verificar se eu detenho a chave privada, o que representa a minha identidade)
			* foco nas chaves do emissor
	* ! não necessariamente uma é apenas para criptografar e a outra descriptografar, os papéis podem inverter
	* **Algoritmos**:
		* **Diffie-Hellman** (DH): principal algoritmo para troca de chaves simétricas em meio inseguro sem conhecimento prévio do segredo
			* Utilizado no VPN-IPSec
			* Não é utilizado para criptografia/descriptografia de conteúdos e mensagens
			* Segurança baseada na complexidade e problema do logaritmo discreto
			* Pode ser utilizado em conjunto com algoritmos de curva elíptica, criando um processo chamado Perfect Forward Secrecy (PFS), aprimorando a resistência a ataques
		* **RSA** (Rivest, Shamir and Adelman): amplamente utilizado em aplicações como SSL/TLS
			* Usa como base do DH
			* Sua complexidade reside na dificuldade de se fatorar números extensos (fatorial?!)
			* Atualmente usa chaves de 2048 ou 4096 bits, mas suporta 1024
			* Usa dois números p e q primos grandes, calculas-se $n = p * q$, um inteiro $e$, de encryption, e $d$, de decryption, derivados de n, daí: 
				* texto (M) cifrado (usa e) = $C = M^e\ mod\ n$
				* texto decifrado (usa d) = $M = C^d\ mod\ n$
		* **El Gamal**: mais utilizado para troca de e-mails, mas usado também para transferência de assinaturas digitais/troca de chaves
			* robustez baseada na dificuldade do cálculo de logaritmos discretos em corpos finitos
			* muito utilizado no PGP (Pretty Good Privacy) - assinatura digital para e-mails
		* **One-Time Pad** (OTP): função teórica de referência que define as características de um modelo matemático inquebrável ou incondicionalmente seguro
			* utiliza combinação caractere por caractere com chave secreta aleatória e contínua (aleatório real! não programado)
			* possui, necessariamente, o mesmo tamanho da mensagem
			* chave utilizada uma única vez e destruída após
			* dificuldade de criar chaves com mesmo tamanho de mensagens, toda vez novas etc
* **Funções Hash** (resumo criptográfico): algoritmos critpográficos unidirecionais -> não consegue recuperar o texto claro a partir do texto cifrado
	* Geram resumos/digests (hashes) de tamanhos fixos, independente da entrada
	* Baseados em cálculos e modelos matemáticos simples com baixo processamento
	* Aplica-se o conceito de **difusão** -> impossível modificar a mensagem original e gerar o mesmo hash
		* **Colisão**: quando duas entradas diferentes produzem a mesma saída (outra forma de dizer: há duas ou mais chaves com o mesmo índice na tabela)
	* **Usos**:
		* **Confidencialidade**: ex - armazenamento de senhas
		* **Integridade**: envio de texto claro + hash dele
		* **Autenticidade**: combinação com outros recursos para uso em assinatura digital
		* ! não usado para trabalhar disponibilidade
	* **Ataques relacionados**:
		* **Ataques de colisão**: busca por valores que gerem o mesmo hash (como para logar em site com senha de um usuário, quando é armazenada em hash); usam-se catálogos de hashs conhecidos
		* **Ataques de aniversário**: baseado em probabilidade, não é necessário acertar o valor/senha, mas sim valores que gerem o mesmo hash -> esforço de quebra $2^\frac{k}{2}$ onde k é o tamanho do digest -> o esforço para quebrar a função hash é 2 elevado à metade dos bits do digest
	* **Funções**:
		* **MD5**: produz hash de 128 bits
			* já possui várias colisões identificadas, diminuindo sua robustez
			* problema de colisão de prefixos -> entradas com prefixos iguais tendem a ter sufixos iguais
		* **SHA**: família de funções de hash
			* Variantes { SHA1, SHA-224, SHA-256, SHA-384, SHA-512 } - o N é a quantidade de bits do digest
		* **RIPEMD**: família de funções de hash RIPEMD{ 128, 160, 256, 320 }
* **Ferramentas de criptografia**: { Bitlocker, Veracypt, Diskcryptor, GNUpg, Apple disk image }


|                   | DES          | 3DES                                       | AES                                                |
| ----------------- | ------------ | ------------------------------------------ | -------------------------------------------------- |
| **Bloco**         | 64 bits      | 64 bits                                    | 128 bits                                           |
| **Chave bruta**   | 64 bits      | 128 bits (2 chaves)<br>192 bits (3 chaves) | 128, 192 ou 256 bits                               |
| **Chave efetiva** | 56 bits (-8) | 112 bits (-2 \* 8)<br>168 bits (-3 \* 8)   |                                                    |
| **Conceitos**     | S-box        | S-box                                      | Substituição e permutação<br>Trabalha com matrizes |
