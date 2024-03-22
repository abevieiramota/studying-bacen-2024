* [Memcached](https://memcached.org/)
	* "*Free & open source, high-performance, **distributed memory object caching system**, generic in nature, but intended for use in speeding up dynamic web applications by alleviating database load.*"
	* "*Memcached is an **in-memory key-value** store for small chunks of arbitrary data (strings, objects) from results of database calls, API calls, or page rendering.*"
	* "*Items are made up of a **key**, an **expiration time**, **optional flags**, and **raw data**. It does not understand data structures; you must upload data that is pre-serialized. Some commands (incr/decr) may operate on the underlying data, but in a simple manner.*"
	* LRU cache por padrão
* Redis
	* tem mais features, mais tipos de dados, operações etc
* Conceitos
	* eviction -> dropar dados do cache (antigo, pouco usado, volumoso etc)
	* 