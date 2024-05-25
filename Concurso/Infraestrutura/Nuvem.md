* **Cloud computing** -> abstração de localidade, gerenciamento etc de aspectos do software { hardware, software, plataforma, serviços etc }
	* descreve { fornecimento, consumo, modelo de entrega } de serviços de TI baseados em protocolo de Internet
	* conteúdo não precisa mais estar armazenado/ser processado em máquinas do usuário/próximas dele
	* responsabilidades de { dev, storage, manutenção, atualização, backup, escalonamento etc } são terceirizados para o fornecedor
	* evolução e convergência de tecnologias de 
		* ! virtualização 
		* arquitetura orientada a serviços
	* objetivo: processar aplicações e armazenar dados fora do ambiente corporativo, otimizando o uso de recursos (lembrar da analogia com carro/taxi, de usar o veículo sem deixar ele ocioso)
	* mudança do modelo de aquisição de equipamentos para aquisição de serviços
	* definição do NIST (National Institute of Standards and Technology)
		* modelo que permite **de forma conveniente** o acesso à rede **sob demanda** para um **conjunto compartilhado de recursos de computação** configuráveis que podem ser **rapidamente provisionados** e lançados com o mínimo de esforço de gestão ou a interação de um prestador de serviço
		* características { auto serviço sob demanda, acesso à rede ampla, pool de recursos, elasticidade rápida, medição de serviço }
* **Características**
	* **elasticidade** -> disponibilização de recursos em função da necessidade
		* vantagem para quando a necessidade varia com o tempo -> por meio de aquisição de hardware, acaba sendo necessário adquirir solução com capacidade para atender a demanda máxima, ficando ociosa no resto do tempo, além do risco de superestimação ou subestimação
		* cria ilusão de recursos computacionais infinitos, permitindo 'eliminação do comprometimento antecipado da capacidade'
	* **acesso remoto a serviços**
	* **alta disponibilidade** -> normalmente há garantias/capacidade de configurar
	* **pagamento por uso**
	* **velocidade na disponibilização do recurso** -> diferente de uma aquisição de software, é rápido o provisionamento de recurso em cloud
	* diminuição da necessidade de recursos computacionais de hardware
	* diminuição da necessidade de tratar aspectos como backup, controle de segurança, manutenção etc
* **V**
	* menor custo de infra
	* alta disponibilidade
	* elasticidade / escalabilidade sob demanda
	* pagamento por uso
	* agilidade na disponibilização de recursos
	* aumento da segurança
	* acesso a aplicações sofisticadas -> similar à aquisição de hardware, pode ser muito caro adquirir todo um sistema, o que pode ser mais acessível caso se pague pelo uso
	* economia de energia -> infra é mantida pelo provedor
	* aumento da confiabilidade
* **DV**
	* vendor lock-in
	* dificuldade de customização, como para adequação a normas (ver que o serviço é prestado para uma gama enorme de usuários, com cenários diversos etc)
	* dificuldade de controlar plenamente a segurança
	* qualidade do suporte
	* viabilidade do provedor no longo prazo
* **Modelos de implantação**
	* **Nuvem pública** -> recursos disponibilizados para público **em geral** através da internet
	* **Nuvem comunitária** -> abrange apenas uma comunidade específica com interesses comuns (ex: nuvem específica para processamento de imagem) -> menor quantidade de usuários, menor a economia em escala
	* **Nuvem privada** -> operada exclusivamente para uma organização
	* **Nuvem híbrida** -> composição de dois ou mais tipos de nuvens; ex pub + priv
* **Modelos de serviço**
	* **SaaS** (Software as a Service) -> software + dados na nuvem; controle da infra e plataforma é feito pelo provedor; ex { outlook, gmail, calendar etc }
	* **PaaS** (Platform as a Service) -> plataforma (ambiente de computação) oferecida para os desenvolvedores criarem aplicações a serem executadas na nuvem; ex { Google App Engine etc }
	* **IaaS** (Infrastructure as a Service) -> infraestrutura de servidores, rede, storage, virtualizados; ex { AWS S3 etc }
	* outros pouco cobrados (não reconhecidos no NIST) { Testing as a Service, Database as a Service, }
	* **Cloud Storage** ~ armazenamento virtualizado, backup online
		* V { vantagens de nuvem, replicação/backup }
		* DV { segurança com dados confidenciais, potencial menor desempenho (necessidade de rede) }
* **Green datacenter**
	* consideração de aspectos socioambientais de desenvolvimento sustentável dos datacenters
* **Zona de disponibilidade** -> região geográfica específica em que provedores de nuvem oferecem redundância e alta disponibilidade para serviços hospedados nessa região