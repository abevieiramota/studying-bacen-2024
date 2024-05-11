* [[SQL]]
* [[Modelagem Relacional]]
* [[Procedural SQL]]
* [[Álgebra relacional]]

* **Linguagens do SGBD**:
	* **DDL** - Data Definition Language - esquema conceitual ! truncate é DDL
	* **DML** - Data Manipulation Language - insert, delete, update, select
	* **DCL** - Data Control Language
	* **VDL** - View Definition Language - esquema externo
	* **SDL** - Storage Definition Language - esquema interno
* next_step::**Componentes**: ver melhor no Elsmari
	* gerenciador de dados armazenados
	* compilador de DDL
	* compilador DML
	* processador do DB em runtime
	* compilador de consultas - transforma em álgebra relacional
	* pré-compilador
* **Transação**:
	* next_step::**2PL**: ver melhor no Elsmari
		* Fase de crescimento (Growing Phase): Durante essa fase, a transação pode adquirir novos bloqueios, mas não pode liberar nenhum bloqueio já adquirido. Isso significa que a transação só pode aumentar a quantidade de recursos que está bloqueando;
		* Fase de encolhimento (Shrinking Phase): Nesta fase, a transação pode liberar bloqueios, mas não pode adquirir novos bloqueios. Isso garante que, uma vez que uma transação comece a liberar recursos, ela não poderá mais adquirir novos recursos, evitando deadlock.
		* apenas obtém lock, depois apenas libera lock