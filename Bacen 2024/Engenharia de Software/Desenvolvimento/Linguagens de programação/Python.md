```python
if __name__ == '__main__':
   n = 115
   n_i = input("Adivinhe: ")
   if n_i == n:
      print("Parabéns")
   else:
      print("Sorry")
```

* Similar ao [[Java]], é compilado (bytecode .pyc) e interpretado (mas em Python o executor já compila e executa)
* **Literais**:
	* **boolean**: `False/True` !cuidado, letra maiúscula
* **Variáveis**:
	* Nomes de inválidos: começar com \\d, ter -, espaço, #
	* [[Linguagens de programação#^def-lang-din-tipada|Dinâmicamente tipada]]
* **Operadores**: 
	* is (mesmo objeto), == (conteúdo igual)
	* **Precedência de operadores**: parênteses > exponencial > multi/div > resto
	* !não existe operador de pré/pós incremento! ++x é igual a x, basicamente colocou o sinal positivo na frente duas vezes
	* // -> divisão inteira - ex: `3//2 = 1`
* **String**:
	* `"oi" * 3 = "oioioi"`
	* !concatenação, apenas entre strings
	* !string é objeto imutável -> as funções que processam não alteram inplace, apenas retornam o resultado
		* faz uso de pool de strings (daí x = 'oi'; y = 'oi'; print(x is y) imprime True)
	* string pode ser acessada por índice 0-based
	* `'r' in my_str`
	  ```python
	  s.capitalize()
	  s.upper(), s.lower()
	  s.split('/')
	  s.strip(), s.lstrip(), s.rstrip()
	  s.find('ab')
	  s.startswith('pre_')
	  s.replace('a', '+')
	  s.title()
	  s.isupper(), s.islower()
	  s.count('a')
```
	* fstring (pode fazer cálculo dentro)
	* multiline `"""`
* **if**:
  ```python
  if n == 10:
     print('oi')
  elif n == 15:
     print('not oi')
  else:
     print('rs') 

  'kid' if age < 13 else 'teen' if age < 18 else 'adult'
```
* **Estruturas de dados**:
	* **list**:
	  ```python
	  a = list(), a = [] # inicialização
	  a[3], a[-3], a[:3], a[3:] # indexação
	  a = [1, 'Oi'] # heterogêna
	  a.append(x), a.insert()
	  a.find('a')
	  a.extend([1, 2, 3]) # concatena com outra lista
	  a.reverse(), a[::-1] # reverse é inplace
	  a.sort() # ordena inplace
	  a.pop(), a.pop(ix) # remove e retorna o último elemento (ou na posição ix, se for passado)
	  a[1000000] -> Exception # acesso a índice não existente
	  del a[3] # remove elemento no índice 3
	  
	  
```
	* **tuplas**:
	  ```python
	  a = tuple(), a = ()
	  a.count(10) # n ocorrências
	  a.index(10) # ix da 1ª ocorrência
```
		* similar a listas, mas são imutáveis
	* **set**:
	  ```python
	  a = set()
	  a.add(x)
	  a.remove(x)
	  a.union(x), a.intersection(x), a.difference(x), a.symmetric_difference(x)
	  a.isdisjoint(x), a.issubset(x), a.issuperset(x)
```
		* não garante ordem, não mantém repetições
	* **dictionary**:
	  ```python
	  a = dict(a=1, 'oi'=3), a = {'a': 123}
	  a['oi']
	  a.keys(), a.values(), a.items()
	  for k, v in a.items():
	  a.get(x, y) # retorna y, caso não haja entrada para x
	  a.update(d) # atualiza a com os items em d
	  a.pop(x) # remove item com chave x e retorna o seu valor
	  del a[x]
	  a.clear() # limpa o dict
	  x in a # true se houver item com chave x em a
	  dict_c = {**dict_a, **dict_b} # merge de dicionários -> realizado na ordem, similar a dict_a.update(dict_b), mas gerando novo dict
```
* **Funções**:
  ```python
  def f(x):
     return 10, x
  v, y = f(20)
  print() # printa e adiciona um newline - string adicionada ao fim pode ser alterada com o parâmetro end
  print(x, y) # printa separando com espaço - separador pode ser alterado com o parâmetro sep
  abs(), min(), max()
  sorted(), sum(), len()
  range(n) # gerador de 0 a n-1
  range(0, n, s) # gerador de 0 a n-1, com step s
  isinstance(x, C) # checa se x é instância da classe C
  callable(x) # checa se x é callable
  enumerate(l)
  hasattr(o, 'att') # verifica se o objeto o tem o atributo att
  reversed(l) # retorna um iterator reversed de l
  zip(x, y, z)
```
* **Exception**:
  ```python
  try:
	  # meu código
  except Excecao1 as e:
	  # meu tratamento
  except Excecao2:
	  # tratamento
  except (Excecao3, Excecao4):
	  # mais tratamento
  except:
	  # resto
  finally:
	  # finaliza!
  else:
	  # nenhuma exceção foi lançada
```
* **OO**:
  ```python
  class Casa:
	 k = 123 # atributo da classe
     def __init__(self, x, y): # métodos devem receber self
        self.x = x
        self.y = y

	 def __str__(self): # método chamado por str(), print()
	    return self.x
        
  class A(Casa): # classe vazia, apenas estende de Casa
     pass

  class B(A):
     def __init__(self, x, y, z):
        super().__init__(x, y)
        self.z = z
```
* **Walrus operator**: `print(x:=10)` -> atribui o valor e retorna
* **switch**:
  ```python
  match x:
     case 10:
        print('foi 10')
     case 20 | 30: # pode usar o or
        print('foi 20 ou 30')
     case _:
	    print('default')

  match l:
     case [a]:
        print('só tem um elemento: ' + str(a))
     case [a, b]:
	    print('tem 2 elementos, sendo o último: ' + str(b))
```
* **while**:
  ```python
  while cond:
     # do something
```
* Para modificar global variable dentro de uma função -> usa 'global variavel'
* `lambda x, y: x + y`
* todo::Ver os métodos mais usados das libs os, sys, collections etc
* todo::Ler sobre cpython, PEP