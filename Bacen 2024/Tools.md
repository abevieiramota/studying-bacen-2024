```dataview
TABLE WITHOUT ID
	link(file.path, file.path) as "Nota", 
	tool AS "Ferramenta"
WHERE tool!=NULL
FLATTEN tool
SORT tool
```