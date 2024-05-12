# Atividades de estudo

* Ver o site oficial das ferramentas, as páginas home, tutorial Hello World, FAQ, troubleshooting, dicas, principais comandos
* Executar um tutorial básico

```dataview
TABLE WITHOUT ID
	link(file.path, file.path) as "Nota", 
	tool AS "Ferramenta"
WHERE tool!=NULL
FLATTEN tool
SORT tool
```