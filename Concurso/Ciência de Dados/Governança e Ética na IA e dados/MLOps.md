**M**achine **L**earning **Op**eration**s** - baseado em DevOps

* Gestão de código { revisão de código }
* Treinamento
* Implantação
* Monitoramento { modelos com desvios, erros, latência, consumo de recursos, desempenho do modelo }
* Versionamento de modelos e de dados { rastreabilidade, reproducibilidade }
* Automação do ciclo de produção { [[CI-CD]], reproducibilidade, consistência, escalabilidade, testes }


Deploy em produção de modelos de ML:
* simplificando manutenção e monitoramento
* eficiência { tempo até deploy/time to market, custos }
* escalabilidade { operação de vários modelos }
* mitigação de riscos { verificação regulatória, privacidade etc }
* automação
* X contínuo { integração, entrega, treinamento, monitoramento } contínuo


**Níveis** - [link 1](https://aws.amazon.com/pt/what-is/mlops/) e [link 2](https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning?hl=pt-br#mlops_level_0_manual_process)
* **Nível 0** - { manual, orientado por data scientists, deploy pouco frequente, pouco monitoramento, separação entre data scientists e operações } > implanta-se um modelo
* **Nível 1** - { experimentação com automatizações, treinamento contínuo em produção, pipeline replicado em ambientes de dev/hom/prod, reuso/modularização, gerenciamento de metadados } > implanta-se um pipeline
* **Nível 2** - { retreino frequente, deploy em escala, registro de modelos, orquestrador, armazenamento de recursos/features, rastreamento de experimentos }

![[Pasted image 20240130182351.png]]


Tópicos
* AIOps - uso de AI para automatizar funções de IT
* ITOA - análise automatizada de operações de IT
* DataOps - operações de conjuntos de dados
* ModelOps - operações de modelos de ML
