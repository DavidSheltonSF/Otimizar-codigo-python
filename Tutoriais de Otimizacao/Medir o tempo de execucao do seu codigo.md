# Medir o tempo de execução do seu código

Quando queremos saber quanto tempo um código demora para rodar, podemos usar a biblioteca **time**, que já vem jundo com o python. Essa medição é útil quando desejamos saber se uma solução de código é ideal, se é muito lenta ou se pode melhorar.


1. Sintaxe:
```python
import time

# Início da contagem
start = time.time()

# <Seu código>

# Fim da contagem
end = time.time()

# Tempo total
time = end - start

```

2. Função test_speed():

Vamos criar uma função para testar o tempo de execução de outras funções
```python
def test_speed(func, *args):
    """Mede o tempo de que uma função demora para rodar
        Args:
            func: [Função]
            *args: [Argumentos que serão passados para a função]
    """
    
    import time  # lib de tempo
    
    start = time.time()
    # Chamada da função e passagem de argumentos
    func(*args) 
    end = time.time()
    
    # Tempo de execução
    tempo = end - start
    
    return tempo
```

Vamos ver agora 2 exemplos de funções com o mesmo objetivo que é encontrar e exibir na tela o primeiro número impar que encontrarem, porém, essas duas funções terão diferentes desempenhos.

Criaremos uma lista  de números pares muito grande e iremos inserir um número impar no centro

```python
# Esta lista possui 5600000 valores.
numeros = [10, 20, 8, 8, 6, 30, 90]  * 800000

# Inserimos um número ímpar no meio da lista
centro = int(len(numeros)/2)
numeros.insert(centro, 7)
```

1º Exemplo: Itera sobre uma lista porém não usa o comando **break**:
```python
def func1(lista):
   
    for num in lista:
        # Verifica se o número é impar
        if num % 2 != 0:
            print(num)

```

2º Exemplo: Itera sobre uma lista e usa o **break** quando encontra um número par:
```python
def func2(lista):
    
    for num in lista:
        # Verifica se o número é ímpar
        if num % 2 != 0:
            print(num)
            break

```

Agora vamos ver os resultados:

```python
time1 = test_speed(func1, numeros)
time2 = test_speed(func2, numeros)

print(f'A execução da func1 durou {time1} segs')
print(f'A execução da func2 durou {time2} segs')
```

Possíveis saídas:
```
A execução da func1 durou 1.1197242736816406 segs
A execução da func2 durou 0.5006024837493896 segs
```


Os testes e exemplos que vimos aqui possuem códigos muito pequenos, portanto é possível que a diferença de desempenho das duas soluções não pareçam muito significantes, porém vale lembrar que códigos profissionais podem conter milhares de linhas e demorar um tempo consideravel para serem executados.

Clique [aqui](https://www.youtube.com/watch?v=3ofsvEUzXCE) para ver um vídeo sobre o assunto.
