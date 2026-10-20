# Aula 06 - Funções em Python

## Objetivos da aula

Ao final desta aula, o aluno deverá ser capaz de:

- Criar e chamar funções utilizando `def`;
- Receber dados por parâmetros e fornecer argumentos nas chamadas;
- Retornar resultados com `return`;
- Diferenciar exibir um valor de retornar um valor;
- Utilizar parâmetros com valores padrão;
- Compreender o escopo local de variáveis;
- Organizar programas com listas, menus e funções.

---

# 1. O que é uma Função?

Uma função é um bloco de código que recebe um nome e pode ser executado quando necessário. Ela permite organizar tarefas e reutilizar código.

Nas aulas anteriores, já utilizamos funções prontas:

```python
print("Olá!")
quantidade = len(["Ana", "Bruno"])
total = sum([7, 8, 9])
```

Agora vamos criar nossas próprias funções.

Imagine que uma mensagem de boas-vindas precise aparecer em diferentes momentos do programa. Podemos colocar as instruções em uma função e chamá-la sempre que necessário.

---

# 2. Criando e Chamando uma Função

Utilizamos a palavra `def` para definir uma função:

```python
def mostrar_boas_vindas():
    print("Bem-vindo ao curso de Python!")
    print("Vamos aprender sobre funções.")


mostrar_boas_vindas()
```

Saída:

```text
Bem-vindo ao curso de Python!
Vamos aprender sobre funções.
```

Nesse exemplo:

1. `def` inicia a definição;
2. `mostrar_boas_vindas` é o nome da função;
3. Os parênteses fazem parte da definição e da chamada;
4. Os dois-pontos iniciam o bloco;
5. A indentação indica quais instruções pertencem à função;
6. `mostrar_boas_vindas()` chama a função e executa seu bloco.

**Definir uma função não executa seu corpo.** O bloco é executado quando fazemos a chamada.

Podemos chamar a mesma função várias vezes:

```python
def mostrar_boas_vindas():
    print("Bem-vindo ao curso de Python!")


mostrar_boas_vindas()
mostrar_boas_vindas()
```

> Utilize nomes que indiquem a tarefa realizada, como `calcular_media` ou `listar_alunos`. Para separar palavras, utilize sublinhado (`_`). Evite usar nomes de funções prontas, como `print`, `sum` ou `input`.

---

# 3. Parâmetros e Argumentos

Uma função pode receber dados para realizar sua tarefa.

```python
def cumprimentar(nome):
    print(f"Olá, {nome}!")


cumprimentar("Ana")
cumprimentar("Carlos")
```

Saída:

```text
Olá, Ana!
Olá, Carlos!
```

- **Parâmetro**: nome declarado na definição da função. No exemplo, `nome`;
- **Argumento**: valor fornecido na chamada. No exemplo, `"Ana"` ou `"Carlos"`.

A cada chamada, o parâmetro recebe o argumento correspondente.

Também podemos passar um valor obtido com `input()`:

```python
def cumprimentar(nome):
    print(f"Olá, {nome}!")


nome_usuario = input("Digite seu nome: ").strip()
cumprimentar(nome_usuario)
```

---

# 4. Funções com Mais de um Parâmetro

Separe os parâmetros por vírgulas:

```python
def mostrar_soma(numero1, numero2):
    print("Soma:", numero1 + numero2)


mostrar_soma(4, 6)
mostrar_soma(10, 3)
```

Saída:

```text
Soma: 10
Soma: 13
```

Na chamada `mostrar_soma(4, 6)`, `numero1` recebe `4` e `numero2` recebe `6`.

Podemos informar os argumentos pela posição ou pelo nome do parâmetro:

```python
def apresentar_aluno(nome, curso):
    print(f"{nome} estuda {curso}.")


apresentar_aluno("Ana", "Inteligência Artificial")
apresentar_aluno(curso="Python", nome="Bruno")
```

Quando utilizamos nomes na chamada, fica explícito qual valor corresponde a cada parâmetro.

---

# 5. Retornando Resultados com `return`

Uma função pode calcular um resultado e devolvê-lo ao trecho do programa que a chamou.

```python
def somar(numero1, numero2):
    return numero1 + numero2


resultado = somar(4, 6)
print("Resultado:", resultado)
print("Dobro:", resultado * 2)
```

Saída:

```text
Resultado: 10
Dobro: 20
```

O `return` encerra a chamada atual da função e devolve o valor indicado. Instruções depois dele, no mesmo caminho de execução, não serão executadas.

Podemos usar condições para retornar resultados diferentes:

```python
def verificar_aprovacao(media):
    if media >= 7:
        return "Aprovado"
    return "Reprovado"


print(verificar_aprovacao(8))
print(verificar_aprovacao(5))
```

Saída:

```text
Aprovado
Reprovado
```

Quando a média é pelo menos `7`, o primeiro `return` encerra a função. Caso contrário, a execução chega ao segundo.

---

# 6. Diferença entre `print()` e `return`

`print()` exibe uma informação na tela. `return` devolve um resultado para que o programa possa utilizá-lo.

Compare as funções:

```python
def exibir_dobro(numero):
    print(numero * 2)


def calcular_dobro(numero):
    return numero * 2


valor_exibido = exibir_dobro(5)
valor_calculado = calcular_dobro(5)

print("Retorno de exibir_dobro:", valor_exibido)
print("Retorno de calcular_dobro:", valor_calculado)
```

Saída:

```text
10
Retorno de exibir_dobro: None
Retorno de calcular_dobro: 10
```

Uma função que termina sem executar um `return` com valor retorna `None`, que representa a ausência de um valor. Um `return` sem expressão também retorna `None`.

Utilize `return` quando precisar guardar o resultado, fazer outro cálculo ou tomar uma decisão com ele.

---

# 7. Parâmetros com Valores Padrão

Podemos definir um valor que será utilizado quando o argumento for omitido:

```python
def cumprimentar(nome, mensagem="Olá"):
    print(f"{mensagem}, {nome}!")


cumprimentar("Ana")
cumprimentar("Bruno", "Bom dia")
```

Saída:

```text
Olá, Ana!
Bom dia, Bruno!
```

Na definição acima, `nome` é obrigatório e `mensagem` possui um valor padrão. Nesse formato de definição, os parâmetros obrigatórios devem aparecer antes dos parâmetros com valor padrão.

> Para listas que serão modificadas, evite valores padrão como `def cadastrar(alunos=[]):`. Essa lista seria compartilhada entre chamadas que omitem o argumento. Nesta aula, criaremos as listas no programa e as passaremos explicitamente às funções.

---

# 8. Escopo: Variáveis Locais

Uma variável criada dentro de uma função é local: seu nome pertence àquela chamada da função.

```python
def calcular_media(nota1, nota2):
    media = (nota1 + nota2) / 2
    return media


resultado = calcular_media(8, 6)
print(resultado)
```

Saída:

```text
7.0
```

O programa utiliza `resultado` para guardar o retorno. O nome local `media` não fica disponível fora da função. Os parâmetros `nota1` e `nota2` também são locais.

Uma variável local pode ter o mesmo nome de uma variável externa:

```python
mensagem = "Mensagem do programa"


def mostrar_mensagem():
    mensagem = "Mensagem da função"
    print(mensagem)


mostrar_mensagem()
print(mensagem)
```

Saída:

```text
Mensagem da função
Mensagem do programa
```

Para deixar claras as entradas e saídas de uma tarefa, prefira receber os dados por parâmetros e devolver os resultados com `return`.

---

# 9. Funções com Listas

Podemos receber uma lista e percorrer seus elementos:

```python
def listar_alunos(alunos):
    if len(alunos) == 0:
        print("Nenhum aluno cadastrado.")
        return

    for aluno in alunos:
        print(f"- {aluno}")


turma = ["Ana", "Bruno", "Carla"]
listar_alunos(turma)
```

O `return` sem valor encerra a função quando a lista está vazia. Assim, o restante do bloco só é executado quando existem alunos.

Uma função também pode modificar a lista recebida:

```python
def adicionar_aluno(alunos, nome):
    alunos.append(nome)


turma = ["Ana"]
adicionar_aluno(turma, "Bruno")
print(turma)
```

Saída:

```text
['Ana', 'Bruno']
```

O parâmetro `alunos` e a variável `turma` se referem à mesma lista nessa chamada. Por isso, `append()` altera a lista utilizada pelo programa. Nenhuma cópia é criada automaticamente.

Atribuir `alunos = []` dentro da função apenas faria o nome local apontar para outra lista; isso não esvaziaria `turma`.

---

# 10. Exemplo Prático: Sistema de Tarefas com Funções

Na Aula 05, escrevemos as ações dentro dos casos do menu. Agora vamos organizar essas ações em funções.

O exemplo completo utiliza apenas entradas de texto:

```python
def mostrar_menu():
    print("\n=== SISTEMA DE TAREFAS ===")
    print("1 - Adicionar tarefa")
    print("2 - Listar tarefas")
    print("3 - Remover tarefa")
    print("4 - Mostrar quantidade de tarefas")
    print("0 - Sair")


def adicionar_tarefa(tarefas, descricao):
    if descricao == "":
        return False

    tarefas.append(descricao)
    return True


def listar_tarefas(tarefas):
    if len(tarefas) == 0:
        print("Nenhuma tarefa cadastrada.")
        return

    print("Tarefas cadastradas:")
    for tarefa in tarefas:
        print(f"- {tarefa}")


def remover_tarefa(tarefas, descricao):
    if descricao in tarefas:
        tarefas.remove(descricao)
        return True

    return False


tarefas = []

while True:
    mostrar_menu()
    opcao = input("Escolha uma opção: ").strip().lower()

    match opcao:
        case "1":
            descricao = input("Digite a tarefa: ").strip()
            if adicionar_tarefa(tarefas, descricao):
                print("Tarefa adicionada com sucesso.")
            else:
                print("A tarefa não pode ficar vazia.")

        case "2":
            listar_tarefas(tarefas)

        case "3":
            descricao = input("Digite a tarefa a remover: ").strip()
            if remover_tarefa(tarefas, descricao):
                print("Tarefa removida com sucesso.")
            else:
                print("Tarefa não encontrada.")

        case "4":
            print(f"Quantidade de tarefas: {len(tarefas)}")

        case "0" | "sair":
            print("Encerrando o sistema...")
            break

        case _:
            print("Opção inválida.")
```

## Entendendo a organização

| Parte | Responsabilidade |
| --- | --- |
| `mostrar_menu()` | Exibir as opções |
| `adicionar_tarefa()` | Validar a descrição e adicionar uma tarefa |
| `listar_tarefas()` | Exibir as tarefas ou informar que a lista está vazia |
| `remover_tarefa()` | Remover a primeira ocorrência da descrição, se existir |
| `while` e `match-case` | Receber escolhas e chamar as funções correspondentes |

As funções de cadastro e remoção retornam `True` quando realizam a operação e `False` quando não conseguem realizá-la. O `if` utiliza esse retorno para selecionar a mensagem.

A lista é criada antes do laço e passada às funções. Os dados permanecem disponíveis entre as escolhas, mas são perdidos quando o programa termina.

> O exemplo utiliza `match-case`. O `return` encerra a função atual; o `break` do menu encerra o `while`.

---

# 11. Cuidados ao Trabalhar com Funções

- Execute a definição antes de chamar a função. Nos exemplos, as definições ficam no início do arquivo;
- Utilize parênteses na chamada: `mostrar_menu()`;
- Forneça os argumentos obrigatórios;
- Respeite a indentação do corpo da função;
- Utilize `return` quando precisar aproveitar um resultado;
- Evite depender de variáveis externas para realizar cálculos;
- Crie funções com responsabilidades claras;
- Ao trabalhar com listas, considere se a função deve consultar ou modificar os dados.

---

# Exercícios

## Exercício 1 — Mensagem de Abertura

Crie a função `mostrar_abertura()`, sem parâmetros, para exibir o nome do curso e uma mensagem de boas-vindas.

Chame a função duas vezes e observe a repetição das mensagens.

---

## Exercício 2 — Apresentação do Aluno

Crie a função `apresentar_aluno(nome, curso)` para exibir uma frase com os dados recebidos.

Solicite os dados com `input()` fora da função e passe-os na chamada. Depois, faça outra chamada utilizando argumentos nomeados.

---

## Exercício 3 — Calculando uma Área

Crie a função `calcular_area_retangulo(base, altura)` que retorne a área do retângulo.

Solicite base e altura com `float()`, chame a função e mostre o resultado fora dela. Considere entradas numéricas positivas.

Teste: base `5` e altura `3` devem produzir área `15.0`.

---

## Exercício 4 — Verificando Números Pares

Crie a função `eh_par(numero)` que retorne `True` para números pares e `False` para ímpares.

Utilize o retorno em um `if` para exibir a classificação fora da função.

Teste os números `0`, `7`, `10` e `-4`.

> Dica: `numero % 2 == 0` verifica se o resto da divisão por `2` é zero.

---

## Exercício 5 — Saudação Personalizada

Crie `saudar(nome, saudacao="Olá")` para **retornar** uma mensagem de saudação.

Faça uma chamada utilizando a saudação padrão e outra informando `"Boa noite"`. Exiba os retornos com `print()`.

---

## Exercício 6 — Média de uma Lista

Crie `calcular_media(notas)` para retornar a média de uma lista de notas. Se a lista estiver vazia, retorne `None`.

Fora da função, verifique `resultado is None` antes de exibir a média. Essa expressão verifica se o resultado é `None`.

Teste:

| Entrada | Retorno esperado |
| --- | --- |
| `[8.0, 6.0, 10.0]` | `8.0` |
| `[0.0, 0.0]` | `0.0` |
| `[]` | `None` |

> Uma média igual a zero é um resultado válido. A lista vazia precisa ser tratada antes da divisão por `len(notas)`.

---

## Exercício 7 — Contando Classificações

Considere as classificações de exemplo:

```python
previsoes = ["gato", "cachorro", "gato", "pássaro", "gato"]
```

Crie `contar_classificacao(previsoes, categoria)` para percorrer a lista com `for` e retornar quantas vezes a categoria aparece.

Teste `"gato"`, `"cachorro"` e `"peixe"`. Os retornos esperados são `3`, `1` e `0`, respectivamente.

Esses dados simulam resultados de classificação; o exercício não executa um modelo de IA.

---

# Desafio — Cadastro de Alunos com Funções

Desenvolva um programa com uma lista de alunos e o seguinte menu:

```text
1 - Cadastrar aluno
2 - Listar alunos
3 - Buscar aluno
4 - Remover aluno
5 - Mostrar quantidade de alunos
0 - Sair
```

Requisitos:

1. Crie `mostrar_menu()` para exibir as opções;
2. Crie `cadastrar_aluno(alunos, nome)` para impedir nomes vazios ou repetidos, adicionar nomes válidos e retornar `True` ou `False`;
3. Crie `listar_alunos(alunos)` para mostrar os nomes com `for` e tratar a lista vazia;
4. Crie `buscar_aluno(alunos, nome)` para retornar `True` se o nome existir e `False` caso contrário;
5. Crie `remover_aluno(alunos, nome)` para remover um nome existente e retornar se a remoção foi realizada;
6. Receba os dados com `input()` no programa principal e normalize os nomes com `.strip().lower()` antes de passá-los às funções;
7. Utilize `while` e `match-case` para controlar as escolhas;
8. Utilize os retornos para decidir quais mensagens exibir;
9. Mantenha a lista fora do laço e passe-a como argumento;
10. Trate opções inválidas e permita encerrar o programa.

Teste o cadastro de um nome, a tentativa de cadastrar o mesmo nome novamente, uma entrada contendo apenas espaços, a busca por um nome inexistente e a remoção de um aluno. Depois, liste os dados para conferir as alterações.
