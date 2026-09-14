# 🚀 Aula 2 — Estruturas Condicionais Encadeadas e Aninhadas

## 🎯 Objetivos da Aula

Ao final da aula, os alunos deverão ser capazes de:

* Compreender decisões com múltiplas possibilidades;
* Utilizar estruturas `if`, `elif` e `else`;
* Criar estruturas condicionais dentro de outras condicionais;
* Utilizar operadores matemáticos, relacionais e lógicos;
* Combinar múltiplas condições;
* Resolver problemas utilizando lógica de decisão;
* Construir pequenos programas com diferentes regras de negócio.

---

# ➕ Operadores Matemáticos

Antes de criarmos regras mais complexas, é importante lembrar que muitas condições dependem de cálculos.

Python possui diversos operadores matemáticos.

| Operador | Operação         | Exemplo   |
| -------- | ---------------- | --------- |
| `+`      | Adição           | `10 + 5`  |
| `-`      | Subtração        | `10 - 5`  |
| `*`      | Multiplicação    | `10 * 5`  |
| `/`      | Divisão          | `10 / 5`  |
| `//`     | Divisão inteira  | `10 // 3` |
| `%`      | Resto da divisão | `10 % 3`  |
| `**`     | Potenciação      | `2 ** 3`  |

---

## 📌 Exemplo

```python
numero1 = 10
numero2 = 3

print(numero1 + numero2)
print(numero1 - numero2)
print(numero1 * numero2)
print(numero1 / numero2)
```

Resultado:

```text
13
7
30
3.3333333333333335
```

---

# ➗ Divisão Normal e Divisão Inteira

Em Python existem duas formas comuns de realizar divisões.

## Divisão normal

```python
print(10 / 3)
```

Resultado:

```text
3.3333333333333335
```

---

## Divisão inteira

```python
print(10 // 3)
```

Resultado:

```text
3
```

O operador `//` descarta a parte decimal da divisão.

---

# 🧩 Operador de Resto `%`

O operador `%` retorna o **resto de uma divisão**.

```python
print(10 % 3)
```

Resultado:

```text
1
```

Isso é extremamente útil para descobrir, por exemplo, se um número é **par ou ímpar**.

```python
numero = 10

if numero % 2 == 0:
    print("Número par")
else:
    print("Número ímpar")
```

Se o resto da divisão por `2` for `0`, o número é par.

---

# 🔍 Operadores de Comparação

Operadores de comparação são utilizados para comparar valores.

O resultado de uma comparação sempre será:

```python
True
```

ou:

```python
False
```

---

| Operador | Significado    |
| -------- | -------------- |
| `==`     | Igual          |
| `!=`     | Diferente      |
| `>`      | Maior          |
| `<`      | Menor          |
| `>=`     | Maior ou igual |
| `<=`     | Menor ou igual |

---

## 📌 Exemplos

```python
idade = 20

print(idade >= 18)
```

Resultado:

```text
True
```

Outro exemplo:

```python
nota = 6

print(nota >= 7)
```

Resultado:

```text
False
```

---

# ⚠️ `=` não é igual a `==`

Esse é um erro extremamente comum no início.

O operador:

```python
=
```

é utilizado para **atribuir um valor**.

Exemplo:

```python
idade = 18
```

Estamos dizendo:

> A variável `idade` recebe o valor `18`.

---

Já:

```python
==
```

é utilizado para **comparar dois valores**.

Exemplo:

```python
idade == 18
```

Estamos perguntando:

> A idade é igual a 18?

---

# 🧠 Operadores Lógicos

Às vezes uma única condição não é suficiente.

Por exemplo:

> Para dirigir, uma pessoa precisa ter pelo menos 18 anos **E** possuir CNH.

Ou:

> Um jogador pode entrar na área VIP se for administrador **OU** moderador.

Para essas situações utilizamos operadores lógicos.

Python possui três operadores principais:

```python
and
or
not
```

---

# 🔗 Operador `and`

O operador `and` significa:

> **E**

Todas as condições precisam ser verdadeiras.

```python
idade = 20
possui_cnh = True

if idade >= 18 and possui_cnh:
    print("Pode dirigir")
```

Nesse caso:

```text
idade >= 18
```

precisa ser verdadeiro **e**:

```text
possui_cnh
```

também precisa ser verdadeiro.

---

## 📊 Tabela do `and`

| Condição 1 | Condição 2 | Resultado |
| ---------- | ---------- | --------- |
| `True`     | `True`     | `True`    |
| `True`     | `False`    | `False`   |
| `False`    | `True`     | `False`   |
| `False`    | `False`    | `False`   |

---

# 🔀 Operador `or`

O operador `or` significa:

> **OU**

Basta que uma das condições seja verdadeira.

```python
cargo = "admin"

if cargo == "admin" or cargo == "moderador":
    print("Acesso permitido")
```

O usuário poderá acessar se for:

```text
admin
```

**ou**

```text
moderador
```

---

## 📊 Tabela do `or`

| Condição 1 | Condição 2 | Resultado |
| ---------- | ---------- | --------- |
| `True`     | `True`     | `True`    |
| `True`     | `False`    | `True`    |
| `False`    | `True`     | `True`    |
| `False`    | `False`    | `False`   |

---

# 🔄 Operador `not`

O operador `not` inverte um valor lógico.

```python
ativo = False

if not ativo:
    print("Usuário desativado")
```

Nesse caso:

```python
ativo
```

é:

```text
False
```

Mas:

```python
not ativo
```

resulta em:

```text
True
```

---

# 🧩 Combinando Condições

Também podemos combinar vários operadores.

```python
idade = 20
possui_cnh = True
documento_valido = True

if idade >= 18 and possui_cnh and documento_valido:
    print("Pode dirigir")
```

Podemos ainda combinar `and` e `or`.

```python
idade = 20
cargo = "admin"

if idade >= 18 and (cargo == "admin" or cargo == "moderador"):
    print("Acesso permitido")
```

Os parênteses ajudam a deixar a regra mais clara.

---

# 🤔 O Que São Condicionais Encadeadas?

Condicionais encadeadas são utilizadas quando um programa possui **várias possibilidades de decisão**.

Imagine que uma escola possui as seguintes classificações:

* Nota ≥ 9 → Excelente
* Nota ≥ 7 → Aprovado
* Nota ≥ 5 → Recuperação
* Nota < 5 → Reprovado

Nesse caso precisamos verificar diferentes possibilidades em sequência.

Em Python utilizamos:

```python
if
elif
else
```

---

# 📌 Exemplo

```python
nota = 6

if nota >= 9:
    print("Excelente")

elif nota >= 7:
    print("Aprovado")

elif nota >= 5:
    print("Recuperação")

else:
    print("Reprovado")
```

Resultado:

```text
Recuperação
```

---

# 🧠 Como o Python Analisa?

O Python verifica as condições **de cima para baixo**.

Primeiro:

```python
nota >= 9
```

Se for falso, verifica:

```python
nota >= 7
```

Se também for falso, verifica:

```python
nota >= 5
```

Quando encontra uma condição verdadeira, executa aquele bloco e encerra aquela estrutura.

---

# 📊 Fluxograma

```text
             ┌───────────┐
             │ nota >= 9 │
             └─────┬─────┘
                   │
             Sim   ▼
              Excelente
                   │
             Não   ▼
             ┌───────────┐
             │ nota >= 7 │
             └─────┬─────┘
                   │
             Sim   ▼
               Aprovado
                   │
             Não   ▼
             ┌───────────┐
             │ nota >= 5 │
             └─────┬─────┘
                   │
             Sim   ▼
             Recuperação
                   │
             Não   ▼
              Reprovado
```

---

# ⚠️ A Ordem das Condições Importa

Imagine este código:

```python
nota = 10

if nota >= 5:
    print("Recuperação")

elif nota >= 7:
    print("Aprovado")

elif nota >= 9:
    print("Excelente")
```

Qual será o resultado?

```text
Recuperação
```

Mesmo a nota sendo `10`.

Isso acontece porque:

```python
nota >= 5
```

já é verdadeiro.

O Python executa aquele bloco e não testa os próximos `elif`.

Por isso devemos organizar as condições corretamente.

```python
if nota >= 9:
    print("Excelente")

elif nota >= 7:
    print("Aprovado")

elif nota >= 5:
    print("Recuperação")

else:
    print("Reprovado")
```

---

# 🏗️ O Que São Condicionais Aninhadas?

Uma estrutura condicional aninhada acontece quando colocamos um `if` **dentro de outro `if`**.

Exemplo:

```python
if condicao1:

    if condicao2:
        print("As duas condições foram atendidas")
```

Podemos pensar nisso como uma sequência de portas.

Primeiro precisamos passar pela primeira condição.

Somente depois podemos verificar a segunda.

---

# 🎮 Exemplo do Mundo Real

Para dirigir precisamos verificar:

1. A pessoa possui 18 anos ou mais?
2. A pessoa possui CNH?

Podemos representar isso utilizando condicionais aninhadas.

---

## Código

```python
idade = 20
possui_cnh = True

if idade >= 18:

    if possui_cnh:
        print("Pode dirigir")

    else:
        print("Precisa tirar CNH")

else:
    print("Menor de idade")
```

---

# 📊 Fluxograma

```text
             idade >= 18?
                  │
           ┌──────┴──────┐
           │             │
          Sim           Não
           │             │
           ▼             ▼
       Possui CNH?   Menor de idade
           │
     ┌─────┴─────┐
     │           │
    Sim         Não
     │           │
     ▼           ▼
Pode dirigir   Tirar CNH
```

---

# 🔍 Comparando Encadeado e Aninhado

## Condicional Encadeada

```python
if nota >= 9:
    print("Excelente")

elif nota >= 7:
    print("Aprovado")

else:
    print("Reprovado")
```

É utilizada quando temos **várias possibilidades diferentes**.

Exemplo:

```text
Excelente
Aprovado
Recuperação
Reprovado
```

---

## Condicional Aninhada

```python
if idade >= 18:

    if possui_cnh:
        print("Pode dirigir")
```

É utilizada quando **uma decisão depende de outra decisão anterior**.

---

# 💍 Pensando como uma Jornada

Imagine uma aventura.

Para entrar em Mordor:

```text
Possui o Anel?
        ↓
      Sim
        ↓
Chegou até Mordor?
        ↓
      Sim
        ↓
Pode tentar destruir o Anel
```

Podemos representar isso assim:

```python
possui_anel = True
chegou_mordor = True

if possui_anel:

    if chegou_mordor:
        print("Agora só falta jogar o Anel na Montanha da Perdição!")

    else:
        print("A jornada ainda não terminou.")

else:
    print("Talvez seja melhor voltar ao Condado procurar o Anel.")
```

Uma condição depende da anterior.

---

# 🎯 Exemplo Completo — Sistema de Acesso

Imagine um sistema que possui três regras:

* Usuário correto;
* Senha correta;
* Conta ativa.

---

```python
usuario = "admin"
senha = "1234"
ativo = True

if usuario == "admin":

    if senha == "1234":

        if ativo:
            print("Acesso liberado")

        else:
            print("Conta desativada")

    else:
        print("Senha incorreta")

else:
    print("Usuário não encontrado")
```

Perceba que cada verificação só acontece depois que a anterior foi validada.

---

# 🧠 Aninhamento ou Operadores Lógicos?

O exemplo anterior também poderia ser escrito utilizando operadores lógicos:

```python
usuario = "admin"
senha = "1234"
ativo = True

if usuario == "admin" and senha == "1234" and ativo:
    print("Acesso liberado")
else:
    print("Acesso negado")
```

Porém existe uma diferença importante.

No código aninhado conseguimos identificar **qual regra falhou**:

```text
Usuário não encontrado
Senha incorreta
Conta desativada
```

Já no segundo exemplo sabemos apenas:

```text
Acesso negado
```

Por isso, a melhor solução depende do problema que estamos resolvendo.

---

# 🎮 Exemplo Prático — Categoria de Campeonato

Vamos solicitar a idade do usuário.

```python
idade = int(input("Digite sua idade: "))

if idade < 12:
    print("Categoria Infantil")

elif idade < 18:
    print("Categoria Juvenil")

elif idade < 40:
    print("Categoria Adulto")

else:
    print("Categoria Master")
```

Observe que não precisamos escrever:

```python
idade >= 12 and idade < 18
```

Isso acontece porque, se o programa chegou ao primeiro `elif`, nós já sabemos que:

```python
idade < 12
```

é falso.

Portanto, a idade já é pelo menos `12`.

---

# 🧪 Outro Exemplo — Número Positivo, Negativo ou Zero

```python
numero = float(input("Digite um número: "))

if numero > 0:
    print("Número positivo")

elif numero < 0:
    print("Número negativo")

else:
    print("O número é zero")
```

---

# 🎯 Exercícios

## Exercício 1 — Faixa Etária

Solicite a idade do usuário.

Classifique como:

* Criança → até 12 anos;
* Adolescente → 13 a 17 anos;
* Adulto → 18 a 59 anos;
* Idoso → 60 anos ou mais.

### Exemplo

```text
Digite sua idade: 25

Adulto
```

---

# 🔺 Exercício 2 — Triângulo

Solicite três valores representando os lados de um triângulo.

Classifique como:

* **Equilátero** → todos os lados iguais;
* **Isósceles** → dois lados iguais;
* **Escaleno** → todos os lados diferentes.

### Exemplo

```text
Primeiro lado: 5
Segundo lado: 5
Terceiro lado: 3

Triângulo Isósceles
```

💡 Utilize operadores lógicos para comparar os lados.

---

# 💰 Exercício 3 — Desconto Progressivo

Solicite o valor de uma compra.

A loja possui as seguintes regras:

* Até R$ 100 → sem desconto;
* Acima de R$ 100 até R$ 300 → 5%;
* Acima de R$ 300 até R$ 500 → 10%;
* Acima de R$ 500 → 15%.

O programa deverá mostrar:

* Valor original;
* Percentual de desconto;
* Valor do desconto;
* Valor final da compra.

### Exemplo

```text
Valor da compra: 600

Valor original: R$ 600.00
Desconto: 15%
Valor do desconto: R$ 90.00
Valor final: R$ 510.00
```

---

# 🎓 Exercício 4 — Aprovação com Frequência

Solicite:

```text
Nota final
Frequência (%)
```

Primeiramente verifique a frequência.

Se ela for menor que `75%`:

```text
Reprovado por frequência
```

Caso contrário, analise a nota:

* Nota ≥ 7 → Aprovado;
* Nota ≥ 5 → Recuperação;
* Nota < 5 → Reprovado.

### Exemplo

```text
Digite sua nota: 8
Digite sua frequência: 70

Reprovado por frequência
```

Observe que mesmo possuindo uma boa nota, o aluno foi reprovado devido à frequência.

Esse exercício é um bom exemplo de **condicionais aninhadas**.

---

# ⚖️ Exercício 5 — Calculadora de IMC

Solicite:

* Peso em quilogramas;
* Altura em metros.

O cálculo do IMC é:

```text
IMC = peso / altura²
```

Em Python:

```python
imc = peso / (altura ** 2)
```

Classifique o resultado:

* Menor que 18.5 → Abaixo do peso;
* Menor que 25 → Peso normal;
* Menor que 30 → Sobrepeso;
* 30 ou mais → Obesidade.

### Exemplo

```text
Digite seu peso: 80
Digite sua altura: 1.80

IMC: 24.69
Classificação: Peso normal
```

---

# 🧮 Exercício 6 — Par ou Ímpar

Solicite um número inteiro.

Utilizando o operador `%`, determine se ele é:

```text
Par
```

ou:

```text
Ímpar
```

### Exemplo

```text
Digite um número: 17

O número é ímpar.
```

---

# 🎮 Exercício 7 — Sistema de Jogo

Um personagem pode entrar em uma dungeon somente se:

* Possuir nível 10 ou superior;
* E possuir uma espada **ou** um cajado.

Solicite:

```text
Nível
Possui espada?
Possui cajado?
```

Determine se o jogador poderá entrar na dungeon.

💡 Pense em como combinar:

```python
and
```

com:

```python
or
```

---

# 🧠 Desafio — Pedra, Papel ou Tesoura

Crie um jogo de:

```text
Pedra
Papel
Tesoura
```

O computador deverá escolher aleatoriamente uma opção.

Para gerar um número aleatório em Python primeiro importe:

```python
import random
```

Depois utilize:

```python
computador = random.randint(0, 2)
```

Os valores representam:

```text
0 = Pedra
1 = Papel
2 = Tesoura
```

Solicite ao jogador uma opção utilizando os mesmos valores.

Exemplo:

```text
0 - Pedra
1 - Papel
2 - Tesoura

Escolha uma opção: 1
```

O programa deverá determinar se ocorreu:

* Vitória;
* Derrota;
* Empate.

---

## 💡 Algumas regras

Pedra vence Tesoura:

```text
Pedra > Tesoura
```

Papel vence Pedra:

```text
Papel > Pedra
```

Tesoura vence Papel:

```text
Tesoura > Papel
```

Primeiro verifique se ocorreu empate:

```python
if jogador == computador:
    print("Empate!")
```

Depois pense nas condições necessárias para verificar as vitórias do jogador.

---

# 🧠 Desafio Extra — Sistema de Login

Crie um programa que solicite:

```text
Usuário
Senha
```

Considere:

```python
usuario_correto = "admin"
senha_correta = "1234"
```

O programa deverá informar:

```text
Login realizado com sucesso
```

ou:

```text
Usuário incorreto
```

ou:

```text
Senha incorreta
```

Tente resolver utilizando **condicionais aninhadas**.
