* Combinação popular das ferramentas { Elasticsearch, Logstash, Kibana } para realizar monitoração de sistemas
	* [[Elasticsearch]] -> ferramenta para pesquisa
	* [[Logstash]] -> ferramenta para coleta de dados
	* [[Kibana]] -> ferramenta para visualização de dados
* Possivelmente passará a ser menos adotada em comparação com ferramentas como OpenSearch, da Amazon, e a stak EFK (Elasticsearch, Fluentd, Kibana )
	* Fluentd -> open source log collector, baixo consumo de memória, CNCF, plugins escritos em Ruby, Kubernetes native, queue persistente (diferente do logstash)
	* Fluentbit -> agente de coleta, open source, light
	* Beat stack -> em Go