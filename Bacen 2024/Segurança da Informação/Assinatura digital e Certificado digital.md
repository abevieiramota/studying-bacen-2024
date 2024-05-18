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