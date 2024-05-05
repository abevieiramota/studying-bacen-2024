```dataview
TABLE WITHOUT ID
	link(file.path, file.path) as "Nota", 
	todo as "TODO"
WHERE todo != NULL
FLATTEN todo
SORT todo
```