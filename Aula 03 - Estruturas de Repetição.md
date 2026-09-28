# Aula 03 - Estruturas de Repetição `for` em Python

## Objetivo da Aula

Nesta aula, vamos aprender a utilizar o **laço de repetição `for`** em Python.

Além de compreender sua sintaxe, veremos como essa estrutura aparece em aplicações relacionadas à **Inteligência Artificial**, como:

- percorrer conjuntos de dados;
- analisar previsões;
- processar textos;
- trabalhar com dados de sensores;
- percorrer matrizes;
- executar operações repetidas em diferentes informações.

> Em aplicações de IA, dificilmente trabalhamos com apenas um único dado. Normalmente temos dezenas, centenas ou milhares de informações que precisam ser processadas. É justamente aí que estruturas de repetição começam a se tornar importantes.

---

# O que é o Laço de Repetição `for`?

Um laço de repetição, também chamado de `loop`, permite executar um bloco de código várias vezes.

O `for` é especialmente utilizado quando queremos **percorrer uma sequência de dados**.

Essa sequência pode ser:

- uma lista;
- uma string;
- uma sequência numérica;
- uma matriz;
- um conjunto de previsões;
- uma coleção de dados de treinamento;
- entre outras estruturas.

## Analogia

Imagine que um sistema de IA recebeu **1.000 imagens** e precisa verificar a classificação realizada para cada uma delas.

Fazer isso manualmente seria inviável:

```text
verificar imagem 1
verificar imagem 2
verificar imagem 3
verificar imagem 4
...
```

Com um `for`, podemos dizer:

```text
Para cada imagem:
    verificar classificação
```

O programa automaticamente repete a operação para todas as imagens.

---

# Sintaxe Básica do `for`

A estrutura básica é:

```python
for variavel in sequencia:
    # código executado durante a repetição
```

A variável recebe, a cada repetição, um elemento da sequência.

Por exemplo:

```python
dados = [10, 20, 30, 40, 50]

for dado in dados:
    print(dado)
```

Saída:

```text
10
20
30
40
50
```

A variável `dado` assume um valor diferente da lista em cada repetição.

---

# Percorrendo Dados com `for`

Em IA, normalmente trabalhamos com conjuntos de dados.

Podemos representar um pequeno conjunto utilizando uma lista.

```python
temperaturas = [23.5, 25.2, 26.8, 24.1, 27.3]

for temperatura in temperaturas:
    print(f"Temperatura registrada: {temperatura}°C")
```

Nesse exemplo, o programa percorre todas as temperaturas registradas.

Esse tipo de processamento poderia aparecer, por exemplo, em um sistema de **IA para agricultura**, monitoramento ambiental ou análise industrial.

---

# `range()`: Repetições com Contagem

Quando queremos executar algo uma determinada quantidade de vezes, podemos utilizar `range()`.

```python
for i in range(5):
    print(i)
```

Saída:

```text
0
1
2
3
4
```

Observe que:

```python
range(5)
```

gera valores de:

```text
0 até 4
```

O valor final não é incluído.

---

# Simulando Épocas de Treinamento

Durante o treinamento de modelos de Machine Learning e Deep Learning, é comum encontrarmos o conceito de **época**.

Uma época representa uma passagem do modelo pelo conjunto de dados de treinamento.

Podemos simular esse processo:

```python
for epoca in range(1, 6):
    print(f"Treinando época {epoca}")
```

Saída:

```text
Treinando época 1
Treinando época 2
Treinando época 3
Treinando época 4
Treinando época 5
```

Aqui ainda não estamos treinando uma IA de verdade.

Estamos apenas entendendo como uma repetição poderia controlar um processo desse tipo.

---

# Argumentos do `range()`

A função `range()` pode receber até três valores:

```python
range(inicio, fim, passo)
```

Onde:

- `inicio`: valor inicial;
- `fim`: valor final, não incluído;
- `passo`: quantidade incrementada a cada repetição.

Exemplo:

```python
for numero in range(0, 11, 2):
    print(numero)
```

Saída:

```text
0
2
4
6
8
10
```

Nesse caso, o programa avança de `2 em 2`.

---

# Analisando Previsões de uma IA

Imagine que um modelo realizou algumas previsões.

```python
previsoes = [
    "gato",
    "cachorro",
    "gato",
    "pássaro",
    "cachorro"
]

for previsao in previsoes:
    print(f"A IA classificou como: {previsao}")
```

Saída:

```text
A IA classificou como: gato
A IA classificou como: cachorro
A IA classificou como: gato
A IA classificou como: pássaro
A IA classificou como: cachorro
```

Essa é uma forma bastante simples de representar o processamento de resultados gerados por um modelo.

---

# Utilizando `for` com Condições

Podemos combinar o `for` com estruturas condicionais.

Imagine que temos valores de confiança de uma IA:

```python
confiancas = [0.95, 0.42, 0.87, 0.31, 0.76]

for confianca in confiancas:

    if confianca >= 0.7:
        print(f"{confianca} → previsão confiável")
    else:
        print(f"{confianca} → previsão com baixa confiança")
```

Saída aproximada:

```text
0.95 → previsão confiável
0.42 → previsão com baixa confiança
0.87 → previsão confiável
0.31 → previsão com baixa confiança
0.76 → previsão confiável
```

Aqui já começamos a combinar dois conceitos importantes:

```text
repetição + tomada de decisão
```

---

# Percorrendo Strings

Strings também podem ser percorridas utilizando `for`.

```python
palavra = "Python"

for letra in palavra:
    print(letra)
```

Saída:

```text
P
y
t
h
o
n
```

Cada caractere da palavra é processado individualmente.

---

# Exemplo com Processamento de Texto

Processamento de texto é extremamente importante em IA, especialmente em áreas como **Processamento de Linguagem Natural (NLP)**.

Considere:

```python
texto = "inteligencia artificial"

for caractere in texto:
    print(caractere)
```

O programa percorre cada caractere individualmente.

Também podemos contar quantas vezes uma determinada letra aparece:

```python
texto = "inteligencia artificial"

quantidade = 0

for letra in texto:

    if letra == "i":
        quantidade += 1

print(f"A letra 'i' apareceu {quantidade} vezes.")
```

Esse é um exemplo bastante simples de **análise de texto**.

---

# Percorrendo Palavras

Também podemos armazenar palavras em uma lista:

```python
tokens = [
    "inteligencia",
    "artificial",
    "machine",
    "learning",
    "python"
]

for token in tokens:
    print(f"Token processado: {token}")
```

> Em processamento de linguagem natural, o termo **token** é utilizado para representar unidades de um texto que serão processadas por um sistema.

Mais adiante veremos tokenização com muito mais detalhes.

---

# Contando Valores

Imagine que um sistema classificou imagens entre `"gato"` e `"cachorro"`.

```python
previsoes = [
    "gato",
    "cachorro",
    "gato",
    "gato",
    "cachorro",
    "gato"
]

quantidade_gatos = 0

for previsao in previsoes:

    if previsao == "gato":
        quantidade_gatos += 1

print(f"Quantidade de gatos detectados: {quantidade_gatos}")
```

Saída:

```text
Quantidade de gatos detectados: 4
```

Observe que:

```python
quantidade_gatos += 1
```

equivale a:

```python
quantidade_gatos = quantidade_gatos + 1
```

---

# Calculando a Média de Dados

Também podemos utilizar `for` para realizar cálculos.

```python
temperaturas = [25, 27, 24, 28, 26]

soma = 0

for temperatura in temperaturas:
    soma += temperatura

media = soma / len(temperaturas)

print(f"Temperatura média: {media}")
```

Saída:

```text
Temperatura média: 26.0
```

Aqui o programa:

1. percorre todas as temperaturas;
2. soma os valores;
3. divide pela quantidade de registros.

Esse é um exemplo simples de **processamento de dados**.

---

# Laços Aninhados

Também podemos colocar um `for` dentro de outro `for`.

Isso é chamado de **laço aninhado**.

```python
matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

for linha in matriz:

    for elemento in linha:
        print(elemento, end=" ")

    print()
```

Saída:

```text
1 2 3
4 5 6
7 8 9
```

O primeiro `for` percorre as linhas.

O segundo `for` percorre os elementos de cada linha.

---

# Matrizes e Inteligência Artificial

Matrizes são extremamente utilizadas em Inteligência Artificial.

Uma imagem pequena em tons de cinza, por exemplo, poderia ser representada de maneira simplificada assim:

```python
imagem = [
    [0, 255, 255],
    [255, 0, 255],
    [255, 255, 0]
]
```

Cada número poderia representar a intensidade de um pixel.

Podemos percorrer essa imagem:

```python
for linha in imagem:

    for pixel in linha:
        print(pixel, end=" ")

    print()
```

Por enquanto, nosso objetivo não é estudar processamento de imagens, mas perceber que o mesmo `for` que estamos aprendendo agora será utilizado posteriormente em aplicações muito mais complexas.

---

# `break`: Interrompendo uma Repetição

O comando `break` interrompe completamente o laço.

Exemplo:

```python
confiancas = [0.92, 0.85, 0.81, 0.20, 0.75]

for confianca in confiancas:

    if confianca < 0.5:
        print("Baixa confiança encontrada!")
        break

    print(f"Confiança: {confianca}")
```

Quando o programa encontrar:

```text
0.20
```

o laço será interrompido.

---

# Exemplo: Detectando um Valor Inválido

Imagine dados recebidos de sensores:

```python
temperaturas = [25, 27, 26, -999, 28]

for temperatura in temperaturas:

    if temperatura == -999:
        print("Erro no sensor!")
        break

    print(f"Temperatura: {temperatura}")
```

Nesse exemplo, `-999` representa um valor de erro.

Assim que ele aparece, o processamento é interrompido.

---

# `continue`: Ignorando uma Iteração

O comando `continue` não encerra o laço.

Ele apenas ignora a repetição atual e passa para a próxima.

```python
dados = [10, 20, None, 30, 40]

for dado in dados:

    if dado is None:
        continue

    print(dado)
```

Saída:

```text
10
20
30
40
```

O valor:

```python
None
```

foi ignorado.

---

# Exemplo: Ignorando Dados Inválidos

```python
temperaturas = [24, 26, -999, 27, 25]

for temperatura in temperaturas:

    if temperatura == -999:
        continue

    print(f"Processando temperatura: {temperatura}")
```

Nesse caso, o programa continua normalmente mesmo quando encontra um valor inválido.

---

# Exemplo Prático: Analisando Resultados de uma IA

Considere que uma IA retornou níveis de confiança para cinco previsões:

```python
confiancas = [0.91, 0.72, 0.45, 0.88, 0.39]
```

Queremos classificar os resultados.

```python
for confianca in confiancas:

    if confianca >= 0.8:
        print(f"{confianca}: alta confiança")

    elif confianca >= 0.5:
        print(f"{confianca}: confiança moderada")

    else:
        print(f"{confianca}: baixa confiança")
```

Saída:

```text
0.91: alta confiança
0.72: confiança moderada
0.45: baixa confiança
0.88: alta confiança
0.39: baixa confiança
```

Observe como estamos combinando:

```text
lista
+
for
+
if / elif / else
```

Esses conceitos formarão a base para programas cada vez mais interessantes.

---

# Exercícios Práticos

## 1. Simulação de Treinamento

Crie um programa que simule `10` épocas de treinamento de uma IA.

O programa deverá mostrar:

```text
Treinando época 1
Treinando época 2
...
Treinando época 10
```

Utilize `for` e `range()`.

---

## 2. Dados de Sensores

Considere:

```python
temperaturas = [22.5, 24.8, 27.1, 23.9, 26.5]
```

Percorra a lista utilizando `for` e exiba:

```text
Temperatura registrada: 22.5°C
Temperatura registrada: 24.8°C
...
```

---

## 3. Detectando Temperaturas Altas

Utilize:

```python
temperaturas = [22, 25, 31, 28, 35, 24]
```

Percorra os valores.

Quando a temperatura for maior que `30`, exiba:

```text
ALERTA: temperatura elevada!
```

Caso contrário, exiba a temperatura normalmente.

---

## 4. Classificação de Confiança

Considere:

```python
confiancas = [0.95, 0.65, 0.34, 0.82, 0.71]
```

Para cada valor:

- confiança maior ou igual a `0.8`: `"Alta confiança"`
- confiança entre `0.5` e `0.79`: `"Confiança média"`
- confiança abaixo de `0.5`: `"Baixa confiança"`

---

## 5. Contando Classificações

Considere as previsões:

```python
previsoes = [
    "gato",
    "cachorro",
    "gato",
    "pássaro",
    "gato",
    "cachorro"
]
```

Crie um programa que conte quantas vezes `"gato"` aparece.

Resultado esperado:

```text
Gatos detectados: 3
```

---

## 6. Média dos Dados

Considere:

```python
dados = [10, 15, 20, 25, 30]
```

Utilizando um `for`:

1. some todos os valores;
2. calcule a média;
3. exiba o resultado.

Evite utilizar `sum()` neste exercício.

---

## 7. Processamento de Texto

Peça ao usuário uma frase.

Utilizando `for`, conte quantas vezes a letra `"a"` aparece.

Exemplo:

```text
Digite uma frase: Inteligência Artificial

Quantidade de letras 'a': 3
```

Considere tanto `"a"` quanto `"A"`.

---

## 8. Ignorando Dados Inválidos

Considere:

```python
dados = [12, 15, None, 18, None, 21]
```

Utilizando `continue`, ignore os valores `None` e exiba apenas os números válidos.

---

# Desafios

## 9. Analisando Previsões

Considere:

```python
previsoes = [
    0.92,
    0.84,
    0.35,
    0.76,
    0.28,
    0.95
]
```

Crie um programa que mostre cada previsão.

Entretanto, se encontrar uma confiança menor que `0.30`, interrompa o processamento utilizando `break`.

---

## 10. Matriz de Pixels

Considere a seguinte representação simplificada de uma imagem:

```python
imagem = [
    [0, 255, 0],
    [255, 255, 0],
    [0, 0, 255]
]
```

Utilizando dois `for` aninhados, exiba:

```text
0 255 0
255 255 0
0 0 255
```

---

## 11. Contador de Classes

Considere:

```python
previsoes = [
    "gato",
    "cachorro",
    "gato",
    "gato",
    "cachorro",
    "pássaro",
    "gato"
]
```

Crie um programa que conte separadamente:

```text
Gatos: 4
Cachorros: 2
Pássaros: 1
```

Utilize variáveis contadoras e estruturas condicionais.

---

## 12. Sistema Simples de Detecção

Considere os dados:

```python
objetos = [
    "pessoa",
    "carro",
    "pessoa",
    "bicicleta",
    "carro",
    "pessoa"
]
```

Percorra todos os elementos e exiba:

```text
Objeto detectado: pessoa
Objeto detectado: carro
...
```

Ao final, informe quantas pessoas foram detectadas.

Resultado:

```text
Total de pessoas detectadas: 3
```

---

# Resumo

O `for` permite percorrer sequências e repetir operações automaticamente.

Sua estrutura básica é:

```python
for elemento in sequencia:
    # processamento
```

Também podemos utilizar:

```python
range()
```

para controlar uma quantidade específica de repetições:

```python
for i in range(10):
    print(i)
```

E controlar o funcionamento do laço utilizando:

```python
break
```

para interromper o loop e:

```python
continue
```

para ignorar determinada iteração.

Em Inteligência Artificial, estruturas de repetição serão constantemente utilizadas para trabalhar com:

```text
datasets
↓
amostras
↓
previsões
↓
tokens
↓
sensores
↓
pixels
↓
matrizes
↓
épocas de treinamento
```

Por enquanto, estamos trabalhando com exemplos pequenos.

Mas a lógica utilizada para percorrer:

```python
[0.91, 0.75, 0.42]
```

é conceitualmente a mesma que futuramente permitirá percorrer centenas ou milhares de dados durante o processamento de sistemas de Inteligência Artificial.
