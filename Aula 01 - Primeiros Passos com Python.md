# 🐍 Aula 01 — Primeiros Passos com Python

# 🎯 Objetivos da Aula

Ao final desta aula, você deverá ser capaz de:

- criar e executar um arquivo Python;
- utilizar a função `print()`;
- compreender os parâmetros `sep` e `end`;
- criar variáveis simples;
- compreender os principais tipos básicos de dados;
- identificar o tipo de uma variável utilizando `type()`;
- receber informações do usuário utilizando `input()`;
- utilizar f-strings para apresentar informações;
- desenvolver pequenos programas utilizando entrada e saída de dados.

---

# 🚀 Nosso primeiro contato com Python

Nesta aula começaremos efetivamente a programar utilizando `Python`.

Nosso objetivo inicial será aprender como um programa pode:

```bash
armazenar informações
        ↓
receber informações
        ↓
processar informações
        ↓
apresentar informações
```

Hoje trabalharemos principalmente com as três primeiras ferramentas da nossa jornada:

```bash
print()
variáveis
input()
```

Mesmo parecendo simples, praticamente todos os programas utilizam esses conceitos de alguma forma.

---

# 📁 Criando nosso primeiro projeto

Crie uma pasta chamada:

```bash
algoritmos-python
```

Dentro dela, crie uma pasta:

```bash
aula01
```

E dentro dela crie o arquivo:

```bash
aula01.py
```

Nossa estrutura ficará assim:

```bash
algoritmos-python/
└── aula01/
    └── aula01.py
```

---

# ▶️ Executando um programa Python

Dentro do arquivo `aula01.py`, escreva:

```python
print("Olá, mundo!")
```

Para executar o programa pelo terminal:

```bash
python aula01.py
```

Dependendo da instalação do Python, também poderá ser:

```bash
py aula01.py
```

Resultado:

```bash
Olá, mundo!
```

---

# 🔎 O que aconteceu?

Podemos imaginar o funcionamento assim:

```bash
aula01.py
    ↓
Interpretador Python
    ↓
Execução das instruções
    ↓
Resultado no terminal
```

O VS Code é onde escrevemos nosso código.

Quem interpreta e executa o código é o Python.

---

# 🖨️ A função `print()`

A função `print()` é utilizada para apresentar informações no terminal.

Exemplo:

```python
print("Olá! Bem vindo ao Técnico em Inteligência Artificial.")
```

Resultado:

```bash
Olá! Bem vindo ao Técnico em Inteligência Artificial.
```

Também podemos imprimir números:

```python
print(10)
print(25)
print(3.14)
```

Resultado:

```bash
10
25
3.14
```

Também podemos executar vários `print()`:

```python
print("Aragorn")
print("Gimli")
print("Legolas")
```

Resultado:

```bash
Aragorn
Gimli
Legolas
```

Por padrão, cada `print()` termina com uma quebra de linha.

---

# 📦 Imprimindo vários valores

Podemos informar vários valores dentro do mesmo `print()`.

Exemplo:

```python
print("Aragorn", "Gimli", "Legolas")
```

Resultado:

```bash
Aragorn Gimli Legolas
```

Por padrão, Python separa os valores utilizando um espaço.

Esse comportamento pode ser alterado.

---

# 🔗 O parâmetro `sep`

O parâmetro `sep` define o que será utilizado para separar os valores de um `print()`.

Exemplo:

```python
print("Aragorn", "Gimli", "Legolas", sep="-")
```

Resultado:

```bash
Aragorn-Gimli-Legolas
```

Podemos utilizar qualquer texto como separador.

Exemplo:

```python
print("Python", "R", "Machine Learning", sep=" | ")
```

Resultado:

```bash
Python | R | Machine Learning
```

Outro exemplo:

```python
print("02", "09", "2026", sep="/")
```

Resultado:

```bash
31/09/2026
```

---

# 🔚 O parâmetro `end`

Por padrão, o `print()` termina com uma quebra de linha.

Por exemplo:

```python
print("Olá")
print("Mundo")
```

Resultado:

```bash
Olá
Mundo
```

Podemos alterar esse comportamento utilizando `end`.

Exemplo:

```python
print("Olá", end=" ")
print("Mundo")
```

Resultado:

```bash
Olá Mundo
```

Outro exemplo:

```python
print("Carregando", end="...")
print("concluído!")
```

Resultado:

```bash
Carregando...concluído!
```

---

# 🧪 Utilizando `sep` e `end` juntos

Também podemos utilizar os dois parâmetros:

```python
print("Aragorn", "Gimli", "Legolas", sep=" | ", end=" -> ")
print("Sociedade do Anel")
```

Resultado:

```bash
Aragorn | Gimli | Legolas -> Sociedade do Anel
```

> [!TIP]
> `sep` controla o que existe **entre os valores**.
>
> `end` controla o que acontece **ao final do print**.

Podemos pensar assim:

```bash
valor 'SEP' valor 'SEP' valor 'END'
```

---

# 📦 Variáveis

Programas precisam armazenar informações durante sua execução.

Para isso utilizamos **variáveis**.

Exemplo:

```python
nome = "Aragorn"
```

Neste exemplo:

```bash
nome
```

é o nome da variável.

E:

```bash
"Aragorn"
```

é o valor armazenado.

Podemos imaginar uma variável como uma caixa:

```bash
nome
┌─────────────┐
│ "Aragorn"   │
└─────────────┘
```

---

# 🧪 Criando variáveis

Podemos criar várias variáveis:

```python
nome = "Aragorn"
idade = 87
altura = 1.98
rei = True
```

Depois podemos utilizar essas informações:

```python
print(nome)
print(idade)
print(altura)
print(rei)
```

Resultado:

```bash
Aragorn
87
1.98
True
```

---

# 🏷️ Nomes de variáveis

Podemos escolher os nomes das variáveis.

Exemplos válidos:

```python
nome = "Frodo"
idade = 50
nome_completo = "Frodo Bolseiro"
portador_do_anel = True
```

Evite nomes sem significado:

```python
x = "Frodo"
a = 50
b = True
```

Prefira:

```python
nome = "Frodo"
idade = 50
guardiao_anel = True
```

> [!TIP]
> O nome da variável deve ajudar outra pessoa a entender o que aquela informação representa.

---

# ⚠️ Algumas regras

Os nomes das variáveis não podem começar com números.

Incorreto:

```python
1nome = "Gandalf"
```

Correto:

```python
nome1 = "Gandalf"
```

> Vamos evitar usar números para nomear variáveis. Somente quando necessário.

Também não podemos utilizar espaços:

```python
nome completo = "Frodo Bolseiro"
```

Utilizamos normalmente `_`:

```python
nome_completo = "Frodo Bolseiro"
```

---

# 🐍 Padrão de nomes em Python

Em Python utilizamos normalmente o padrão chamado:

```bash
snake_case
```

Exemplos:

```python
nome_completo = "Bilbo Bolseiro"
idade_personagem = 111
quantidade_de_ouro ≅ ♾️
nome_do_jogador = "Daniel"
```

As palavras são separadas utilizando `_`.

---

# 🧬 Tipos básicos de dados

Uma variável pode armazenar diferentes tipos de informações.

Nesta aula conheceremos quatro tipos básicos:

```bash
str
int
float
bool
```

---

# 🧵 String — `str`

Strings representam textos.

Exemplo:

```python
nome = "Gandalf"
```

Também podemos utilizar aspas simples:

```python
nome = 'Gandalf'
```

Outros exemplos:

```python
cidade = "São Leopoldo"
curso = "Técnico em Inteligência Artificial"
classe = "Mago"
```

---

# 🔢 Integer — `int`

O tipo `int` representa números inteiros.

Exemplos:

```python
idade = 30
nivel = 10
quantidade = 25
```

Números inteiros não possuem casas decimais.

---

# 🔢 Float — `float`

O tipo `float` representa números com casas decimais.

Exemplos:

```python
altura = 1.75
peso = 82.5
temperatura = 27.3
```

> [!IMPORTANT]
> Em Python utilizamos `.` como separador decimal.
>
> Correto:
>
> ```python
> altura = 1.75
> ```
>
> Incorreto:
>
> ```python
> altura = 1,75
> ```

---

# ✅ Boolean — `bool`

O tipo `bool` representa valores lógicos.

Existem apenas dois:

```python
True
False
```

Exemplo:

```python
ativo = True
```

Outro exemplo:

```python
possui_arma = False
```

Podemos imaginar valores booleanos como perguntas de **sim ou não**:

```bash
Está ativo?
True

Possui arma?
False

Está logado?
True
```

---

# 🔍 Descobrindo o tipo de uma variável

Podemos utilizar a função:

```python
type()
```

Exemplo:

```python
nome = "Frodo"
idade = 50
altura = 1.20
possui_anel = True

print(type(nome))
print(type(idade))
print(type(altura))
print(type(possui_anel))
```

Resultado:

```bash
<class 'str'>
<class 'int'>
<class 'float'>
<class 'bool'>
```

---

# 🧪 Testando tipos

Observe:

```python
idade = 30
```

Temos um `int`.

Agora:

```python
idade = "30"
```

Temos uma `str`.

Apesar de visualmente parecerem semelhantes:

```bash
30
"30"
```

para o Python são informações diferentes.

Um é um número.

O outro é um texto.

Essa diferença será muito importante nas próximas aulas.

---

# ⌨️ Entrada de dados com `input()`

Até agora nossos valores estavam definidos diretamente dentro do código.

Exemplo:

```python
nome = "Aragorn"
```

Mas podemos permitir que o usuário informe um valor.

Para isso utilizamos:

```python
input()
```

Exemplo:

```python
nome = input("Digite seu nome: ")
```

Quando o programa executar, aparecerá:

```bash
Digite seu nome:
```

O programa ficará esperando o usuário digitar algo.

---

# 🧪 Nosso primeiro programa interativo

```python
nome = input("Digite seu nome: ")

print(nome)
```

Execução:

```bash
Digite seu nome: Legolas
Legolas
```

O valor digitado pelo usuário foi armazenado na variável `nome`.

Podemos imaginar assim:

```bash
Usuário
   ↓
input()
   ↓
"Legolas"
   ↓
variável nome
```

---

# 💬 Combinando texto e variáveis

Podemos imprimir uma mensagem e uma variável:

```python
nome = input("Digite seu nome: ")

print("Olá,", nome)
```

Exemplo:

```bash
Digite seu nome: Gimli
Olá, Gimli
```

Mas Python possui uma forma muito interessante de trabalhar com textos e variáveis.

---

# 🧵 F-Strings

F-strings permitem inserir valores de variáveis dentro de textos.

Exemplo:

```python
nome = "Legolas"

print(f"Olá, {nome}!")
```

Resultado:

```bash
Olá, Legolas!
```

Observe o `f` antes das aspas:

```python
f""
```

E as chaves:

```python
{nome}
```

O Python substitui:

```bash
{nome}
```

pelo valor armazenado na variável.

---

# 🧪 Outro exemplo

```python
nome = "Gandalf"
classe = "Mago"

print(f"{nome} pertence à classe {classe}.")
```

Resultado:

```bash
Gandalf pertence à classe Mago.
```

---

# 🎮 Criando uma ficha de personagem

Agora podemos combinar tudo que aprendemos:

```python
nome = input("Nome do personagem: ")
classe = input("Classe do personagem: ")
origem = input("Local de origem: ")

print()
print("===== FICHA DO PERSONAGEM =====")
print(f"Nome: {nome}")
print(f"Classe: {classe}")
print(f"Origem: {origem}")
```

Execução:

```bash
Nome do personagem: Aragorn
Classe do personagem: Guerreiro
Local de origem: Gondor

===== FICHA DO PERSONAGEM =====
Nome: Aragorn
Classe: Guerreiro
Origem: Gondor
```

---

# ⚠️ Uma observação importante sobre `input()`

Observe:

```python
idade = input("Digite sua idade: ")
```

Mesmo que o usuário digite:

```bash
30
```

o valor recebido pelo `input()` será um texto.

Ou seja:

```python
"30"
```

Podemos verificar:

```python
idade = input("Digite sua idade: ")

print(type(idade))
```

Resultado:

```bash
<class 'str'>
```

> [!NOTE]
> Por enquanto apenas lembre:
>
> **`input()` sempre retorna uma `str`.**
>
> Na próxima aula veremos como transformar esse valor em número para realizar cálculos.

---

# 🧪 Prática Guiada — Cadastro de Jogador

Crie um programa que solicite:

```bash
Nome
Nickname
Jogo favorito
Plataforma favorita
```

Depois apresente:

```bash

# Exemplo

===== PERFIL DO JOGADOR =====
Nome: Daniel
Nickname: Mithrandir
Jogo favorito: Red Dead Redemption 2
Plataforma favorita: PlayStation 5
```

---

# 🧠 Antes dos exercícios

Nesta aula trabalhamos com:

```bash
print()
   ↓
saída de dados

variáveis
   ↓
armazenamento de dados

input()
   ↓
entrada de dados
```

Podemos representar um programa simples assim:

```bash
ENTRADA
   ↓
PROCESSAMENTO
   ↓
SAÍDA
```

Hoje ainda tivemos pouco processamento.

Nas próximas aulas começaremos a realizar cálculos e tomar decisões.

---

# 📝 Exercícios

## Exercício 01 — Apresentação

Crie um programa que apresente no terminal:

```bash
Olá!
Meu nome é __________.
Estou aprendendo Python.
```

Utilize pelo menos três `print()` diferentes.

---

## Exercício 02 — `sep`

Utilizando apenas um `print()`, apresente:

```bash
Senac | TIA | Python é legal
```

Utilize o parâmetro `sep`.

---

## Exercício 03 — Data Atual

Utilizando apenas um `print()`, apresente a data atual no formato `dd/mm/yyyy`.

**Dica: Utilize o parâmetro `sep`**.

---

## Exercício 04 — `end`

Utilize três comandos `print()` diferentes para produzir apenas uma linha:

```bash
Python é muito legal!
```

**Utilize o parâmetro `end`**.

---

## Exercício 05 — Criando variáveis

Crie variáveis para armazenar:

- seu nome;
- sua idade;
- sua cidade;
- seu curso.

Depois apresente todas as informações utilizando `print()`.

---

## Exercício 06 — Tipos de dados

Crie as seguintes variáveis:

```bash
nome
idade
altura
matriculado
```

Utilize tipos adequados para cada informação.

Depois utilize `type()` para descobrir o tipo de cada variável.

---

## Exercício 07 — Personagem

Crie as variáveis:

```bash
nome
classe
nivel
possui_equipamento
```

Utilize valores de tipos adequados.

Depois apresente algo semelhante a:

```bash
===== PERSONAGEM =====
Nome: Aragorn
Classe: Guerreiro
Nível: 10
Possui Equipamento: True
```

---

## Exercício 08 — Entrada de dados

Crie um programa que pergunte:

```bash
Qual é o seu nome?
Qual é a sua cidade?
Qual é o seu jogo favorito?
```

Depois apresente uma frase semelhante a:

```bash
Olá, Daniel! Você mora em São Leopoldo e seu jogo favorito é Red Dead Redemption 2.
```

**Utilize uma `f-string`**.

---

## Exercício 09 — Curso

Crie um programa que solicite:

```bash
Nome do aluno
Nome do curso
Unidade
Turno
```

Depois apresente:

```bash
===== MATRÍCULA =====

Aluno: ...
Curso: ...
Unidade: ...
Turno: ...
```

---

# ⚔️ Desafio — Ficha de Aventureiro

Crie um programa que permita cadastrar um personagem.

O programa deverá perguntar:

```bash
Nome do personagem:
Raça:
Classe:
Local de origem:
Arma principal:
```

Depois apresente uma ficha semelhante a:

```bash
================================
       FICHA DO AVENTUREIRO
================================

Nome: Aragorn
Raça: Humano
Classe: Guerreiro
Origem: Gondor
Arma: Andúril

================================
```

Utilize:

- variáveis;
- `input()`;
- `print()`;
- `f-strings`;
- `sep` ou `end` em pelo menos algum ponto do programa.

---

# ⭐ Desafio Extra

Crie uma pequena tela de apresentação para um jogo.

Exemplo:

```bash
================================
   AS CRÔNICAS DA TERRA MÉDIA
================================

Digite seu nome: Daniel
Digite o nome do personagem: Boromir
Digite sua classe: Guerreiro

Bem-vindo, Daniel!

Seu personagem é Boromir.
Classe escolhida: Guerreiro.

A aventura está prestes a começar...
```

Tente organizar a saída para que ela fique visualmente agradável.

> [!TIP]
> Programas não precisam apenas funcionar.
>
> A forma como as informações são apresentadas também influencia a experiência de quem utiliza o sistema.

---

# 🧠 Questões para pensar

Sem executar o código, tente responder:

### 1.

Qual será o tipo da variável?

```python
nome = "25"
```

---

### 2.

Qual será o tipo?

```python
idade = 25
```

---

### 3.

O que será exibido?

```python
print("A", "B", "C", sep="-")
```

---

### 4.

O que será exibido?

```python
print("Olá", end=" ")
print("Mundo")
```

---

### 5.

Qual será o tipo da variável `idade`?

```python
idade = input("Digite sua idade: ")
```

Mesmo que o usuário digite:

```bash
20
```

---

# 🗺️ Onde estamos?

Nossa jornada agora está assim:

```bash
✅ Entrada e saída
      ↓
✅ Variáveis
      ↓
✅ Tipos básicos
      ↓
⬜ Conversão de tipos
      ↓
⬜ Operadores
      ↓
⬜ Estruturas condicionais
      ↓
⬜ Estruturas de repetição
      ↓
⬜ Estruturas de dados
      ↓
⬜ Funções
      ↓
⬜ Orientação a Objetos
```

Ainda estamos construindo os fundamentos.

Esses conceitos parecerão simples futuramente, mas praticamente todo programa Python que desenvolvermos utilizará variáveis, tipos, entrada e saída de dados.

---

# ✅ Checklist da Aula

Ao finalizar esta aula, verifique se você consegue:

- [ ] criar um arquivo `.py`;
- [ ] executar um programa Python;
- [ ] utilizar `print()`;
- [ ] imprimir vários valores;
- [ ] utilizar `sep`;
- [ ] utilizar `end`;
- [ ] criar variáveis;
- [ ] utilizar nomes de variáveis seguindo `snake_case`;
- [ ] identificar `str`;
- [ ] identificar `int`;
- [ ] identificar `float`;
- [ ] identificar `bool`;
- [ ] utilizar `type()`;
- [ ] utilizar `input()`;
- [ ] entender que `input()` retorna uma `str`;
- [ ] utilizar `f-strings`;
- [ ] desenvolver um pequeno programa com entrada e saída de dados.
