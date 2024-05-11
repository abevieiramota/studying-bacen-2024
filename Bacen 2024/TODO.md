# TODO

```dataview
TABLE WITHOUT ID
	link(file.path, file.path) as "Nota", 
	todo as "TODO"
WHERE todo != NULL
FLATTEN todo
SORT todo
```



# Estudar mais (study_more)

```dataview
TABLE WITHOUT ID
	link(file.path, file.path) as "Nota", 
	study_more as "Estudar mais"
WHERE study_more != NULL
FLATTEN study_more
SORT study_more
```




# Próximos passos (next_step)

```dataview
TABLE WITHOUT ID
	link(file.path, file.path) as "Nota",
	next_step AS "Próximo passo"
WHERE next_step!=NULL
FLATTEN next_step
SORT next_step
```


# Adicionar ao Anki

```dataview
TABLE WITHOUT ID
	link(file.path, file.path) as "Nota",
	anki AS "Adicionar ao Anki"
WHERE anki!=NULL
FLATTEN anki
SORT anki
```