```dataview
TABLE WITHOUT ID
	link(file.path, file.path) as "Nota",
	anki AS "Adicionar ao Anki"
WHERE anki!=NULL
FLATTEN anki
SORT anki
```