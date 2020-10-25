# Álgebra Linear

**Definição** - A Álgebra Linear é o ramo da matemática que lida com espaços vetoriais.

## Vetores
Abstratamente, os vetores são objetos que podem ser somados juntos (para formar vetores novos) e que podem ser multiplicados pelos escalares (por exemplo, números), também para formar vetores novos. Concretamente (para nós), os vetores são pontos em algum espaço de dimensão finita. Apesar de você não pensar em seus dados como vetores, eles são uma ótima maneira de representar dados numéricos.

## Trabalhando com vetores
Frequentemente precisaremos de dois vetores. Os vetores se adicionam componente a componente. Isso significa que, se dois vetores v e w possuem o mesmo tamanho, sua soma é somente o vetor cujo primeiro elemento seja v[0] + w[0], cujo segundo elemento seja v[1] + w[1], e assim por diante. (Se eles não possuírem o mesmo tamanho, então não poderemos somá-los.) Por exemplo, somar os vetores [1, 2] e [2, 1] resulta em [1 + 2, 2 + 1] ou [3, 3].

### Somando os componentes de um vetor
Para implementar a função faremos de soma dos components do vetor faremos uso da função interna do python **zip** junto dela usaremos **List Comprehensions** para adicionar os elementos correspondentes
```python
# Adiciona dois vetores componente a componente
def vector_add(v, w):    
    return [v_i + w_i for v_i, w_i in zip(v, w)]
```

### Subtraindo os componentes de um vetor
```python
# Subtrai os componentes do vetor um a um
def vector_subtract(v, w):
    return [v_i - w_i for v_i, w_i in zip(v, w)]
```

### Somando os elementos de um vetor
Criando um novo vetor cujo primeiro elemento seja a soma de todos os primeiros elementos, cujo segundo elemento seja a soma de todos os segundos elementos, e assim por diante.
```python
# A função reduce(fun, seq) é usada para aplicar uma função passada como argumento a todos os elementos de uma lista. A função é definida no módulo 'functools'.
def vector_sum(vectors):
    return reduce(vector_add, vectors)

```
Multiplicando um vetor por um escalar:
```python
def scalar_multiply(scalarNumber, vector):
    return [scalarNumber * v_i for v_i in vector]
```

### Calculando a média de uma lista de vetores de mesmo tamanho
```python
def vector_mean(vectors):
    # computar o vetor cujo i-ésimo elemento é a média do i-ésimos elementos dos vetores de entrada
    n = len(vectors)
    return scalar_multiply(1 / n, vector_sum(vectors))
```

### Produto escalar
O produto escalar mede a distância a qual o vetor v se estende na direção de w. Por exemplo, se w = [1, 0] então dot(v, w) é o primeiro componente de v.
```python
def dot(v, w):
    # O produto escalar de dois vetores é a soma de seus produtos componente a componente.
    # v_1 * w_1 + ... + v_n * w_n
    return sum(v_i * w_i for v_i, w_i in zip(v, w))
```

### Calculando a soma dos quadrados de um vetor:
```python
def sum_of_squares(vector):
    """v_1 * v_1 + ... + v_n * v_n"""
    return dot(vector, vector)
```

### Calculando a magnitude (ou tamanho) de um vetor
```python
def magnitude(v):
    return math.sqrt(sum_of_squares(v))
```

### Calculando a distância entre dois vetores
```python
def distance(v, w):
   return math.sqrt(squared_distance(v, w))
```

## Matrizes
Uma matriz é uma coleção de números bidimensional.

## Trabalhando com matrizes

### Representação de uma matriz
```python
def shape(Matrix):
    num_rows = len(Matrix)
    num_cols = len(Matrix[0]) if Matrix else 0
    return num_rows, num_cols
```

### Buscando uma linha de uma matriz
```python
def get_row(Matrix, i):
    return Matrix[i]
```

### Buscando uma coluna de uma matriz
```python
def get_column(Matrix, i):
    rreturn [Matrix_i[j] for Matrix_i in Matrix]
```

### Criando uma matriz
```python
def make_matrix(num_rows, num_cols, entry_fn):
    # Retorna uma matriz num_rows x num_cols onde (i, j)-ésima entrada é a função definida entry_fn(i, j)
    return [[entry_fn(i, j) for j in range(num_cols)] for i in range(num_rows)]
```

**Todos os exemplos construídos podem ser feitos usando NumPy (http://www.numpy.org).**

## Referências
- [Vetor (matemática)](https://pt.wikipedia.org/wiki/Vetor_(matem%C3%A1tica))
- [Matriz (matemática)](https://pt.wikipedia.org/wiki/Matriz_(matem%C3%A1tica))
- [zip](http://devfuria.com.br/python/built-in-zip/)
- [List Comprehension](https://python-3-patterns-idioms-test.readthedocs.io/en/latest/Comprehensions.html)
- [math](https://docs.python.org/3/library/math.html)
- [Produto escalar](https://pt.wikipedia.org/wiki/Produto_escalar)
- [NumPy](http://www.numpy.org)