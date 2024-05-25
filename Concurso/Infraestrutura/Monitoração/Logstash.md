* open source log collector -> coleta, transforma (formatação, anonimização/exclusão de dados sensíveis, agregação, parsing) e envia, por meio de agentes
* high data throughput, escalável, dados estruturados ou não
* on-memory queue -> usa redis para ser stateful (caso não use, diante de um crash/restore pode se perder)
* lightweight { FileBeat, MetricBeat, PacketBeat etc} -> serviços mais simples
* [plugins](https://www.elastic.co/guide/en/logstash/current/filter-plugins.html) { input, filter, output }
	* input { file, beats, syslog, http, tcp, udp, stdin } + { plain, json, csv }
		* file beat -> tcp
		* packet beat -> http
	* filter -> processa logs { grok, date, mutate, drop etc }
		* anki::grok -> parse de dados não estruturados; mais poderoso e menos performático que o dissect, por trabalhar com regex
			* 
		* mutate -> operações de alteração
	* output { file, csv, s3 }
* é possível programar regras condicionais (ex; não processar logs de warning)
* nós shipper { coletam e enviam para o indexer } e indexer  { indexa e envia para o destino }
* next_step::ver documentação de filters, input e output plugins
* next_step::ver página inicial


![[Pasted image 20240429070218.png]]