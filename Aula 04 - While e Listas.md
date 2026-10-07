# Aula 04 - While, Loop Infinito e Listas em Python

## Objetivos da aula

Ao final desta aula, o aluno deverá ser capaz de:

- Utilizar o `while` para criar estruturas de repetição;
- Criar loops infinitos controlados com `while True`;
- Utilizar `break` para interromper repetições;
- Criar e manipular listas;
- Percorrer listas utilizando estruturas de repetição;
- Utilizar funções como `len()`, `sum()`, `min()` e `max()`.

---

# 1. Estrutura de Repetição `while`

O `while` é utilizado quando queremos repetir um bloco de código **enquanto uma condição for verdadeira**.

Sintaxe:

```python
while condicao:
    # código executado enquanto a condição for verdadeira
```

Exemplo:

```python
contador = 1

while contador <= 5:
    print(contador)
    contador += 1
```

Saída:

```text
1
2
3
4
5
```

Nesse exemplo:

1. `contador` começa com `1`;
2. O Python verifica se `contador <= 5`;
3. Executa o código;
4. Incrementa o contador;
5. Volta para a condição;
6. Quando a condição se torna falsa, o loop termina.

---

# 2. Exemplo: Tentativa de Login

```python
senha_correta = "python123"
senha = ""

while senha != senha_correta:
    senha = input("Digite sua senha: ")

print("Login realizado com sucesso!")
```

Enquanto a senha estiver incorreta, o programa continuará solicitando uma nova tentativa.

Estruturas assim aparecem bastante em:

- Login;
- Validação de dados;
- Jogos;
- Menus;
- Sistemas que aguardam alguma ação do usuário.

---

# 3. Cuidado com Loop Infinito

Um loop infinito acontece quando a condição do `while` nunca se torna falsa.

Exemplo:

```python
numero = 1

while numero <= 10:
    print(numero)
```

Nesse caso, `numero` nunca é alterado.

O programa continuará mostrando:

```text
1
1
1
1
1
...
```

Para corrigir:

```python
numero = 1

while numero <= 10:
    print(numero)
    numero += 1
```

Agora `numero` aumenta a cada repetição e eventualmente a condição será falsa.

---

# 4. Loop Infinito Controlado com `while True`

Também podemos criar um loop infinito propositalmente:

```python
while True:
    print("Executando...")
```

A condição `True` sempre será verdadeira.

Então como podemos parar esse loop?

Utilizando `break`.

---

# 5. Utilizando `break`

O `break` encerra imediatamente o loop.

Exemplo:

```python
while True:

    comando = input("Digite um comando ou 'sair': ")

    if comando == "sair":
        break

    print("Comando recebido:", comando)

print("Programa encerrado.")
```

Enquanto o usuário não digitar `sair`, o programa continua executando.

Quando isso acontecer:

```python
if comando == "sair":
    break
```

o Python abandona o `while`.

Esse padrão é muito utilizado na construção de menus.

---

# 6. Listas em Python

Uma lista permite armazenar **vários valores dentro de uma mesma variável**.

Exemplo:

```python
alunos = ["Ana", "Carlos", "Marcos", "Julia"]
```

Em vez de:

```python
aluno1 = "Ana"
aluno2 = "Carlos"
aluno3 = "Marcos"
aluno4 = "Julia"
```

podemos agrupar essas informações.

```python
alunos = ["Ana", "Carlos", "Marcos", "Julia"]
```

Uma lista também pode conter números:

```python
notas = [8.5, 7.0, 9.5, 6.0]
```

---

# 7. Índices

Cada elemento possui uma posição chamada **índice**.

Em Python, os índices começam em `0`.

```python
alunos = ["Ana", "Carlos", "Marcos", "Julia"]

print(alunos[0])
print(alunos[2])
```

Resultado:

```text
Ana
Marcos
```

Visualmente:

```text
Índice:      0         1          2         3

Lista:     "Ana"    "Carlos"   "Marcos"   "Julia"
```

Também podemos acessar o último elemento utilizando `-1`:

```python
print(alunos[-1])
```

Resultado:

```text
Julia
```

---

# 8. Adicionando Elementos com `append()`

O método `append()` adiciona um elemento no final da lista.

```python
tecnologias = []

tecnologias.append("Python")
tecnologias.append("JavaScript")
tecnologias.append("PostgreSQL")

print(tecnologias)
```

Resultado:

```text
['Python', 'JavaScript', 'PostgreSQL']
```

---

# 9. Removendo Elementos

## `remove()`

Remove um determinado valor da lista.

```python
tecnologias = ["Python", "JavaScript", "Java"]

tecnologias.remove("Java")

print(tecnologias)
```

Resultado:

```text
['Python', 'JavaScript']
```

---

## `pop()`

O `pop()` remove um elemento utilizando seu índice.

```python
tecnologias = ["Python", "JavaScript", "Java"]

tecnologias.pop(1)

print(tecnologias)
```

Resultado:

```text
['Python', 'Java']
```

Se não informarmos o índice:

```python
tecnologias.pop()
```

o último elemento será removido.

---

# 10. Funções Úteis para Listas

Python possui várias funções prontas que facilitam bastante o trabalho com listas.

## `len()`

Retorna a quantidade de elementos.

```python
alunos = ["Ana", "Carlos", "Pedro"]

quantidade = len(alunos)

print(quantidade)
```

Resultado:

```text
3
```

---

## `sum()`

Soma todos os valores numéricos de uma lista.

```python
notas = [7.5, 8.0, 9.0, 6.5]

total = sum(notas)

print(total)
```

Resultado:

```text
31.0
```

Podemos combinar `sum()` e `len()` para calcular uma média:

```python
notas = [7.5, 8.0, 9.0, 6.5]

media = sum(notas) / len(notas)

print(media)
```

---

## `min()`

Retorna o menor valor existente na lista.

```python
notas = [7.5, 8.0, 9.0, 6.5]

menor = min(notas)

print(menor)
```

Resultado:

```text
6.5
```

---

## `max()`

Retorna o maior valor existente na lista.

```python
notas = [7.5, 8.0, 9.0, 6.5]

maior = max(notas)

print(maior)
```

Resultado:

```text
9.0
```

Portanto:

```python
notas = [7.5, 8.0, 9.0, 6.5]

print("Quantidade:", len(notas))
print("Soma:", sum(notas))
print("Menor nota:", min(notas))
print("Maior nota:", max(notas))
print("Média:", sum(notas) / len(notas))
```

Essas funções economizam bastante código.

---

# 11. Percorrendo uma Lista com `while`

Também podemos utilizar `while` para acessar cada posição de uma lista.

```python
linguagens = ["Python", "JavaScript", "Java", "C#"]

indice = 0

while indice < len(linguagens):

    print(linguagens[indice])

    indice += 1
```

Resultado:

```text
Python
JavaScript
Java
C#
```

Observe a condição:

```python
indice < len(linguagens)
```

Como a lista possui 4 elementos:

```text
len(linguagens) = 4
```

os índices utilizados serão:

```text
0
1
2
3
```

---

# 12. Cadastro Utilizando Lista e `while`

Podemos juntar os conceitos aprendidos.

```python
nomes = []

while True:

    nome = input("Digite o nome do aluno ou 'sair': ")

    if nome == "sair":
        break

    nomes.append(nome)

print("Alunos cadastrados:")

indice = 0

while indice < len(nomes):

    print(nomes[indice])

    indice += 1
```

Nesse pequeno sistema utilizamos:

- Lista;
- `while`;
- `while True`;
- `break`;
- `append()`;
- `len()`;
- Índices.

---

# Exercícios

## Exercício 1 — Contagem Regressiva

Solicite um número inteiro ao usuário.

Utilizando `while`, apresente uma contagem regressiva desse número até `0`.

Exemplo:

```text
Digite um número: 5

5
4
3
2
1
0
```

---

## Exercício 2 — Validação de Preço

Solicite ao usuário o preço de um produto.

Enquanto o valor informado for menor ou igual a `0`, o programa deverá solicitar o preço novamente.

Quando um valor válido for informado, apresente:

```text
Produto cadastrado com sucesso.
```

---

## Exercício 3 — Lista de Jogos

Crie inicialmente a seguinte lista:

```python
jogos = [
    "Minecraft",
    "Terraria",
    "Stardew Valley"
]
```

Solicite ao usuário o nome de mais dois jogos e adicione-os à lista.

Depois apresente:

- A lista completa;
- A quantidade total de jogos;
- O primeiro jogo;
- O último jogo.

---

## Exercício 4 — Controle de Estoque

Crie uma lista vazia:

```python
produtos = []
```

Permita que o usuário cadastre produtos até digitar:

```text
fim
```

Quando o cadastro terminar, apresente todos os produtos e a quantidade total cadastrada.

---

## Exercício 5 — Estatísticas de Notas

Utilize a seguinte lista:

```python
notas = [7.5, 8.0, 5.5, 9.0, 6.5, 10.0]
```

O programa deverá apresentar:

- Quantidade de notas;
- Soma das notas;
- Média da turma;
- Maior nota;
- Menor nota.

Utilize:

```python
len()
sum()
min()
max()
```

---

## Exercício 6 — Busca em Lista

Crie a seguinte lista:

```python
usuarios = [
    "admin",
    "maria",
    "joao",
    "pedro"
]
```

Solicite um nome de usuário.

Utilizando `while`, percorra a lista procurando pelo nome informado.

O programa deverá apresentar:

```text
Usuário encontrado.
```

ou:

```text
Usuário não encontrado.
```

---

## Exercício 7 — Carrinho de Compras

Crie duas listas:

```python
produtos = []
precos = []
```

O programa deverá permitir que o usuário cadastre produtos e seus respectivos preços.

O cadastro deverá continuar até o usuário digitar:

```text
sair
```

Ao final, apresente:

- Quantidade de produtos cadastrados;
- Valor total da compra;
- Produto mais barato;
- Produto mais caro.

> Dica: os índices das duas listas representam o mesmo produto.

Exemplo:

```python
produtos = ["Mouse", "Teclado", "Monitor"]
precos = [80, 150, 900]
```

O índice `0` representa:

```text
Mouse → R$ 80
```

---

## Exercício 8 — Sistema de Tarefas

Desenvolva um programa com o seguinte menu:

```text
1 - Adicionar tarefa
2 - Listar tarefas
3 - Remover tarefa
4 - Mostrar quantidade de tarefas
0 - Sair
```

As tarefas devem ser armazenadas em uma lista.

Exemplo:

```text
1 - Adicionar tarefa
2 - Listar tarefas
3 - Remover tarefa
4 - Mostrar quantidade de tarefas
0 - Sair

Escolha uma opção: 1

Digite a tarefa: Estudar Python

Tarefa adicionada com sucesso.
```

O menu deve continuar aparecendo enquanto o usuário não escolher `0`.

Utilize:

- `while True`;
- `break`;
- `if/elif`;
- Lista;
- `append()`;
- `remove()` ou `pop()`;
- `len()`.
