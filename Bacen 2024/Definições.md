```dataview
TABLE WITHOUT ID
	link(file.path, file.path) as "Nota", 
	def AS "Definição"
WHERE def!=NULL
FLATTEN def
SORT def
```