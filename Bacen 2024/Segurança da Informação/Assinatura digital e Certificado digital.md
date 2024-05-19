* **Assinatura digital**: produz ==integridade== e ==autenticidade== (+ não repúdio) na troca de mensagens entre dois usuários
	* Muito utilizado atualmente, expandindo sua utilização a medida que a sociedade se torna cada vez mais digital, como com IPv6 e IoT
	* !cuidado, confidencialidade não é garantida com assinatura digital
	* **Recursos utilizados**:
		* **Criptografia assimétrica**: faz uso das chaves pública e privada do emissor
		* **Função Hash**: 
	* **Processo**:
		* **Emissor**:
			* Aplica função hash na mensagem
			* Cifra o resumo com sua chave privada
			* Envia a mensagem e o resumo cifrado
		* **Destinatário**:
			* Aplica função hash na mensagem
			* Descriptografa o resumo cifrado, usando a chave pública do emissor (daí a autenticidade)
			* Compara (daí a integridade)
	* **Temporalidade**: a assinatura digital pode estar associada a um timestamp para registrar o momento da assinatura (temporal), ou não (atemporal)
* **Certificado digital**: tecnologia que lida com os problemas de confiabilidade em chaves públicas divulgadas (é mesmo a chave pública da entidade? onde obtenho?)
	* Necessariamente envolve um terceiro confiável - Autoridades Certificadoras (AC) / Certificate Authority (CA)
	*  Envolve o uso de um arquivo que contém informações do responsável (física, jurídica, sistema, site etc), como:
		* chave pública do responsável
		* dados da entidade responsável
		* dados da entidade que gerou o certificado
		* assinaturas digitais da entidade que gerou o certificado
		* chave pública da CA
		* cadeia de confiança (laço de confiança entre as CA)
		* validade
	* Segue o padrão X.509, RFC 5280
	* Possibilita, em conjunto com assinatura digital, garantir { autenticidade, integridade, confidencialidade }
	* Podem ser revogados por:
		* Vencimento de prazo (fator temporal)
		* Integridade violada (ex: certificado roubado)
		* n_entendi::A CA deixou de ter responsabilidade sobre o certificado
	* **Tipos**:
		* **Certificados de assinatura digital (A)**: utilizados para confirmação da identidade na web (e-mail, transação online, VPN etc)
		* **Certificado de sigilo (S)**: usado em determinados cenários que não envolvam múltiplas interações (ex: envio de um e-mail), faz uso do próprio certificado para garantir confidencialidade da mensagem, cifrando ela
		* !Perceber que há uma hierarquia entre os níveis de certificados, que varia o nível de criticidade e, consequentemente, outros fatores, como prazos para revogação
		* **Certificados A1 e S1**: chaves geradas por software, podendo ser armazenadas em hardware ou repositório protegido por senha (não exige necessariamente senha para interações, como usar o certificado); tem validade máxima de 1 ano; prazo máximo para concluir revogação = 72h
		* **Certificados A2 e S2**: chaves geradas por software e armazenadas em smart card/token sem capacidade de geração de chaves, protegidas por senha; chaves com no mínimo 1024 bits; validade máxima de 2 anos; prazo máximo para concluir revogação = 54h
		* **Certificados A3 e S3**: chaves geradas e armazenadas em smart card/token com capacidade de geração de chaves, protegidos por senha; chaves com no mínimo 1024 bits; validade máxima de 3 anos; prazo máximo para concluir revogação = 36h
		* **Certificados A4 e S4**: chaves geradas e armazenadas em smart card/token com capacidade de geração de chaves, protegidos por senha; chaves com no mínimo ==2048 bits==; validade máxima de 3 anos; prazo máximo para concluir revogação = 18h
	* **Entidades associadas ao certificado**
		* e-CPF (pessoa física): tem mesma validade jurídica de um CPF; não serve para emissão de NFe; serve para declaração de IR, serviços gerais da RFB etc
		* e-CNPJ (pessoa jurídica): versão digital do CNPJ da empresa, amplamente utilizado na digitalização de processos; serve para serviços como declaração de IR, serviços com a RFB, com a Caixa etc
		* Certificados específicos para algumas classes profissionais, como advogados (e-Jurídico), médicos (e-Saúde) etc
		* Certificados para sistemas, sites etc
			* Certificado por domínio -> vale para todo diretório abaixo do domínio
			* Em caso de subdomínios, há duas opções:
				* Um certificado por subdomínio
				* Usar certificado wildcard, que inclui um wildcard no domínio - ex: www.*.estrategia.com.br
				* Usar Subject Alternate Name (SAN), com um domínio respondendo por domínios diversos (como ter um domínio .com respondendo por outros da mesma organização, como .com.br)
* def::**Infraestrutura de Chaves Públicas - ICP** (ou Public Key Infraestructure - PKI): todo conjunto de hardware, software, pessoal, políticas, procedimentos etc necessários para criar e implementar uma infraestrutura de certificação digital
	* Trata a demanda de garantia de confiabilidade em chaves públicas em um contexto de alta escala
	* Além do aspecto de confiabilidade, trata de aspectos como auditabilidade e controle
	* **Protocolos de gerenciamento**:
		* **Registro**: processo em que um usuário se faz conhecido por uma CA (diretamente ou por meio de uma RA), antes de haver emissão de certificado
		* n_entendi::**Inicialização**: instalação de materiais chave (key materials) etc de forma que o cliente seja considerado seguro pela CA
		* **Certificação**: processo em que a AC emite o certificado para o cliente
		* **Recuperação do par de chaves**: é possível recuperar os pares de chaves por meio de informações bases (key materials)
		* **Atualização do par de chaves**: todas as chaves precisams er renovadas periodicamente, gerando novos pares de chaves e novos certificados (!mudou alguma coisa, é preciso gerar novo certificado digital)
		* **Requisição de revogação**: pessoa ou instância autorizada solicita ao AC a revogação (por situações anormais, como violação de integridade)
		* n_entendi::**Certificação cruzada**: duas ACs trocam (...)
	* **Papéis** (funções básicas { registro, emissão, validação }):
		* **Autoridade Registradora (AR)** / Registration Authority (RA): entidade responsável pelos pedidos de registro, funcionando como intermediário na comunicação entre cliente requisitante e o AC, desonerando este
			* !Entidade não obrigatória
			* Tem função exclusiva de registro, funcionando como 'postos avançados' para realizar essas etapas iniciais pré emissão
			* Ações { receber e aceitar registros, distribuir chaves, validar requisições de verificação de certificados }
				* n_entendi::o que significa a AR 'receber e aceitar registros', 'validar requisições de verificação de certificados'
		* **Autoridade Certificadora (AC)** / Certificate Authority (CA): entidade responsável pela emissão de certificados
			* Certificado digital é documento público
			* Processa requisições de emissão de certificados, que seguem a estrutura { informação de requisição, assinatura digital da informação requisição, algoritmos de criptografia a serem usados }
			* Gerencia as LCR
			* Responsável por responder a consultas de verificação de certificados emitidos por ela
		* **Certificados digitais**
		* **Lista de Certificados Revogados (LCR)** / Certification Revocation List (CRL): informações de apoio para verificação de certificados não mais válidos, revogados antes da validade (recebo o certificado, se está nessa lista, já rejeito)
			* !A responsabilidade por emissão de LCRs é de todas ACs, não apenas da AC raiz
	* **Estrutura hierárquica**
		* Leva à noção de cadeia de certificados: problemas em um certificado num nível mais alto invalidam todos os certificados em níveis abaixo; o certificado de uma CA é emitido pela CA de nível imediatamente superior
		* CA raiz:
			* como não tem CA acima, faz uso de certificado digital auto assinado
			* a ausência de CA acima torna necessários outros meios de legitimação da entidade, como normas, reconhecimento da comunidade etc
			* deve ser amplamente divulgada e conhecida
			* pode envolver relação de confiança entre ACs raízes (como entre o AC raiz do Brasil e o AC raiz da Argentina) -> se o AC raiz do Brasil confia no AC raiz da Argentina, aqui no Brasil a gente confia no AC raiz da Argentina
	* **Online Cerificate Status Protocol** (OCSP): protocolo criado para tratar a troca de LCRs; no lugar de ficar baixando LCRs, faz consulta usando esse protocolo, que retorna status
	* **ICP - Brasil**
		* Controlada e gerenciada pelo Governo Brasileiro, com diretrizes definidas pelo Comitê Gestor da ICP Brasil
		* Produz validade jurídica
		* ACs e ARs não se restringem a órgãos de governo (há empresas como Certsign, bancos privados) - [estrutura](https://estrutura.iti.gov.br/)
		* 