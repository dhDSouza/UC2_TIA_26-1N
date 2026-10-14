# Aula 05 - Match-Case e Menus Interativos em Python

## Objetivos da aula

Ao final desta aula, o aluno deverá ser capaz de:

- Compreender a estrutura `match-case`;
- Selecionar ações de acordo com a opção informada pelo usuário;
- Utilizar `case _` para tratar opções desconhecidas;
- Agrupar alternativas utilizando `|`;
- Combinar `while`, `match-case` e `break` para criar menus interativos;
- Integrar menus com listas e laços `for`.

> O `match-case` está disponível a partir do **Python 3.10**. Utilize essa versão ou uma versão posterior para executar os exemplos.

---

# 1. O que é `match-case`?

O `match-case` permite verificar um valor e executar o bloco correspondente ao primeiro padrão que combinar com ele.

Nesta aula, utilizaremos padrões simples, como números e textos, para selecionar ações. A estrutura também permite comparar formatos de dados mais complexos, assunto que poderá ser aprofundado depois.

Imagine um programa com estas opções:

```text
1 - Cadastrar aluno
2 - Listar alunos
0 - Sair
```

Cada opção corresponde a uma ação diferente.

Sintaxe básica:

```python
opcao = "2"

match opcao:
    case "1":
        print("Cadastrar aluno")
    case "2":
        print("Listar alunos")
    case "0":
        print("Sair")
    case _:
        print("Opção inválida")
```

Saída:

```text
Listar alunos
```

Nesse exemplo:

1. `match opcao` verifica o valor de `opcao`;
2. Cada `case` apresenta um padrão possível;
3. O bloco de `case "2"` é executado;
4. Os demais casos são ignorados.

Observe os dois-pontos e a indentação: os `case` ficam dentro do `match`, e as ações ficam dentro de cada `case`.

---

# 2. Comparando com `if/elif/else`

Nas aulas anteriores, selecionamos ações utilizando condições:

```python
opcao = "1"

if opcao == "1":
    print("Cadastrar aluno")
elif opcao == "2":
    print("Listar alunos")
else:
    print("Opção inválida")
```

Para essas opções fixas, podemos escrever:

```python
opcao = "1"

match opcao:
    case "1":
        print("Cadastrar aluno")
    case "2":
        print("Listar alunos")
    case _:
        print("Opção inválida")
```

As duas versões apresentam o mesmo resultado nesse exemplo.

O `if/elif/else` continua sendo útil para condições como `nota >= 7` ou `idade < 18`. O `match-case` é uma boa opção quando queremos selecionar ações a partir de valores ou padrões conhecidos.

---

# 3. O Caso Padrão: `case _`

O símbolo `_` corresponde a qualquer valor. Colocado no final, ele trata os valores que não combinaram com os casos anteriores.

```python
cor = input("Digite uma cor do semáforo: ").strip().lower()

match cor:
    case "verde":
        print("Siga.")
    case "amarelo":
        print("Atenção.")
    case "vermelho":
        print("Pare.")
    case _:
        print("Cor desconhecida.")
```

Os métodos utilizados na entrada são:

- `.strip()`: remove espaços do início e do final do texto;
- `.lower()`: transforma as letras em minúsculas.

Assim, uma entrada como `" VERDE "` se transforma em `"verde"`.

O `case _` é opcional. Sem ele, se nenhum padrão combinar, nenhum bloco do `match` será executado. Quando utilizado, deve ficar por último, pois corresponde a qualquer valor.

---

# 4. Atenção ao Tipo do Valor

A função `input()` sempre retorna uma **string**, mesmo quando o usuário digita um número.

```python
opcao = input("Escolha uma opção: ")

match opcao:
    case "1":
        print("Você escolheu a opção 1.")
    case _:
        print("Opção inválida.")
```

Utilizamos `case "1"` porque a entrada é um texto.

Se o valor for um número inteiro, utilizamos um padrão numérico:

```python
numero = 1

match numero:
    case 1:
        print("Número um.")
    case 2:
        print("Número dois.")
    case _:
        print("Outro número.")
```

Para os menus desta aula, manteremos a opção como texto. Isso permite que uma entrada como `"abc"` seja tratada pelo `case _`, sem precisar convertê-la com `int()`.

> Escreva os textos entre aspas. Um nome isolado, como `case sair:`, captura o valor em uma variável; ele não compara a entrada com o texto `"sair"`.

---

# 5. Agrupando Alternativas com `|`

Podemos executar a mesma ação para mais de uma alternativa.

```python
comando = input("Digite iniciar, ajuda ou sair: ").strip().lower()

match comando:
    case "iniciar" | "começar":
        print("Iniciando o programa...")
    case "ajuda" | "?":
        print("Escolha iniciar para começar ou sair para encerrar.")
    case "sair" | "0":
        print("Encerrando o programa...")
    case _:
        print("Comando desconhecido.")
```

O padrão `"sair" | "0"` combina com qualquer uma dessas duas alternativas. Dentro de um padrão de `case`, utilizamos `|` para agrupá-las.

Esse exemplo processa apenas um comando. Para solicitar várias opções, precisamos de um laço de repetição.

---

# 6. Menu Interativo com `while True`

Um menu interativo deve reaparecer depois que uma ação termina, permitindo que o usuário escolha outra opção.

Vamos combinar:

- `while True`: repete a apresentação do menu;
- `input()`: recebe a escolha;
- `match-case`: seleciona a ação;
- `break`: encerra o laço quando o usuário escolhe sair.

Exemplo completo:

```python
while True:
    print("\n=== MENU PRINCIPAL ===")
    print("1 - Mostrar mensagem de boas-vindas")
    print("2 - Mostrar informações do curso")
    print("0 - Sair")

    opcao = input("Escolha uma opção: ").strip()

    match opcao:
        case "1":
            print("Bem-vindo ao curso de Python!")
        case "2":
            print("Estamos estudando decisões, repetições e listas.")
        case "0":
            print("Encerrando o programa...")
            break
        case _:
            print("Opção inválida. Tente novamente.")

print("Programa finalizado.")
```

## Como o programa funciona?

1. O `while` apresenta o menu;
2. O usuário digita uma opção;
3. O `match` executa o caso correspondente;
4. Ao terminar a ação, o programa volta ao início do `while`;
5. Se a opção for `"0"`, o `break` encerra o laço;
6. O programa executa a mensagem após o `while`.

> O `match` não precisa de `break` ao final de cada caso: somente o primeiro caso que combinar será executado. Neste menu, o `break` serve para sair do `while`, não para finalizar um `case`.

Se houver laços aninhados, `break` encerra apenas o laço mais próximo em que ele está inserido.

## Exemplo de interação

```text
=== MENU PRINCIPAL ===
1 - Mostrar mensagem de boas-vindas
2 - Mostrar informações do curso
0 - Sair
Escolha uma opção: 1
Bem-vindo ao curso de Python!

=== MENU PRINCIPAL ===
1 - Mostrar mensagem de boas-vindas
2 - Mostrar informações do curso
0 - Sair
Escolha uma opção: 9
Opção inválida. Tente novamente.

=== MENU PRINCIPAL ===
1 - Mostrar mensagem de boas-vindas
2 - Mostrar informações do curso
0 - Sair
Escolha uma opção: 0
Encerrando o programa...
Programa finalizado.
```

---

# 7. Menu com uma Variável de Controle

Também podemos controlar a repetição por uma variável, em vez de utilizar `while True` e `break`.

```python
executando = True

while executando:
    print("\n=== MENU ===")
    print("1 - Cumprimentar")
    print("0 - Sair")

    opcao = input("Escolha uma opção: ").strip()

    match opcao:
        case "1":
            print("Olá! Bons estudos.")
        case "0":
            executando = False
        case _:
            print("Opção inválida.")

print("Programa encerrado.")
```

Quando `executando` recebe `False`, a condição do `while` será falsa na próxima verificação e a repetição terminará.

---

# 8. Exemplo Prático: Sistema de Tarefas

Na Aula 04, aprendemos a armazenar dados em listas. Agora vamos utilizar um menu para escolher o que fazer com esses dados.

O sistema permitirá adicionar, listar, remover e contar tarefas.

```python
tarefas = []

while True:
    print("\n=== SISTEMA DE TAREFAS ===")
    print("1 - Adicionar tarefa")
    print("2 - Listar tarefas")
    print("3 - Remover tarefa")
    print("4 - Mostrar quantidade de tarefas")
    print("0 - Sair")

    opcao = input("Escolha uma opção: ").strip().lower()

    match opcao:
        case "1":
            tarefa = input("Digite a tarefa: ").strip()

            if tarefa == "":
                print("A tarefa não pode ficar vazia.")
            else:
                tarefas.append(tarefa)
                print("Tarefa adicionada com sucesso.")

        case "2":
            if len(tarefas) == 0:
                print("Nenhuma tarefa cadastrada.")
            else:
                print("Tarefas cadastradas:")
                for tarefa in tarefas:
                    print(f"- {tarefa}")

        case "3":
            tarefa = input("Digite o nome da tarefa a remover: ").strip()

            if tarefa in tarefas:
                tarefas.remove(tarefa)
                print("Tarefa removida com sucesso.")
            else:
                print("Tarefa não encontrada.")

        case "4":
            print(f"Quantidade de tarefas: {len(tarefas)}")

        case "0" | "sair":
            print("Encerrando o sistema...")
            break

        case _:
            print("Opção inválida. Escolha uma opção do menu.")
```

## Entendendo as estruturas utilizadas

| Estrutura | Função no programa |
| --- | --- |
| Lista `tarefas` | Armazena as tarefas durante a execução |
| `while True` | Mantém o menu em funcionamento |
| `match-case` | Seleciona a operação escolhida |
| `if/else` | Valida os dados dentro de uma operação |
| `for` | Percorre as tarefas para exibi-las |
| `append()` | Adiciona uma tarefa |
| `remove()` | Remove a primeira ocorrência da tarefa informada |
| `len()` | Informa a quantidade de tarefas |
| `break` | Encerra o menu |

A expressão `tarefa in tarefas` verifica se a tarefa existe na lista antes da remoção. Isso evita tentar remover um valor inexistente.

A lista fica **antes do `while`** para preservar os dados entre as escolhas. Se escrevêssemos `tarefas = []` dentro do laço, a lista seria esvaziada a cada repetição.

Os dados ficam apenas na memória: ao encerrar o programa, as tarefas não são salvas em um arquivo.

---

# 9. Utilizando `for` com `match-case`

Além dos menus, podemos utilizar `match-case` para processar cada elemento de uma lista.

Imagine que um modelo de IA produziu estas classificações:

```python
previsoes = ["gato", "cachorro", "gato", "pássaro", "desconhecido"]

gatos = 0
cachorros = 0
passaros = 0
outros = 0

for previsao in previsoes:
    match previsao:
        case "gato":
            gatos += 1
        case "cachorro":
            cachorros += 1
        case "pássaro":
            passaros += 1
        case _:
            outros += 1

print("Gatos:", gatos)
print("Cachorros:", cachorros)
print("Pássaros:", passaros)
print("Outros:", outros)
```

Saída:

```text
Gatos: 2
Cachorros: 1
Pássaros: 1
Outros: 1
```

O `for` percorre as previsões, enquanto o `match` seleciona qual contador deve ser atualizado. Os resultados são dados de exemplo; esse código não executa um modelo de IA.

---

# 10. Cuidados ao Criar Menus

- Compare entradas de `input()` com textos, como `case "1"`;
- Coloque `case _` depois dos casos específicos;
- Mantenha a leitura da opção dentro do `while`, para receber uma nova escolha a cada repetição;
- Inclua uma opção de saída que encerre o laço;
- Crie as listas antes do laço para manter os dados entre as operações;
- Valide dados antes de remover elementos ou calcular médias de listas vazias;
- Respeite a indentação para que cada ação pertença ao caso correto.

---

# Exercícios

## Exercício 1 — Dias da Semana

Solicite um número de `1` a `7`, mantendo a entrada como texto.

Utilize `match-case` para mostrar o dia correspondente, considerando `"1"` como segunda-feira e `"7"` como domingo.

Para qualquer outra entrada, mostre `"Dia inválido."`.

---

## Exercício 2 — Comandos de um Assistente

Solicite um comando e utilize `match-case` para tratar:

- `"oi"` ou `"olá"`: apresentar uma saudação;
- `"ajuda"` ou `"?"`: mostrar os comandos disponíveis;
- `"sair"` ou `"0"`: apresentar uma despedida;
- Qualquer outro texto: informar que o comando é desconhecido.

Utilize `.strip().lower()` e `|` para agrupar as alternativas. Neste exercício, processe apenas um comando.

---

## Exercício 3 — Menu de Estudos

Crie um menu que se repita utilizando `while True`:

```text
1 - Mostrar uma dica sobre Python
2 - Mostrar uma dica sobre inteligência artificial
3 - Mostrar uma mensagem de incentivo
0 - Sair
```

Utilize `match-case` para selecionar a mensagem, `case _` para entradas inválidas e `break` para sair.

Teste as opções `1`, `2`, `3`, uma opção inexistente e `0`.

---

## Exercício 4 — Cadastro de Alunos

Crie uma lista vazia e desenvolva este menu:

```text
1 - Cadastrar aluno
2 - Listar alunos
3 - Mostrar quantidade de alunos
0 - Sair
```

Requisitos:

- Impedir o cadastro de nomes vazios;
- Informar quando não houver alunos para listar;
- Utilizar `for` para mostrar os nomes;
- Manter os alunos cadastrados entre as escolhas;
- Repetir o menu até a opção de saída.

---

## Exercício 5 — Lista de Compras

Desenvolva um programa com as opções:

```text
1 - Adicionar produto
2 - Listar produtos
3 - Remover produto pelo nome
4 - Mostrar quantidade de produtos
0 - Sair
```

Utilize uma lista para armazenar os produtos. Antes de remover, verifique com `in` se o produto existe.

Aceite tanto `"0"` quanto `"sair"` para encerrar o programa.

---

## Exercício 6 — Classificando Resultados

Considere:

```python
resultados = ["positivo", "negativo", "positivo", "neutro", "erro", "negativo"]
```

Utilize `for` e `match-case` para contar resultados positivos, negativos, neutros e desconhecidos.

Resultado esperado:

```text
Positivos: 2
Negativos: 2
Neutros: 1
Desconhecidos: 1
```

---

## Exercício 7 — Menu de Estatísticas

Utilize a lista:

```python
notas = [7.5, 8.0, 5.5, 9.0, 6.5]
```

Crie um menu com `while` e `match-case`:

```text
1 - Listar notas
2 - Mostrar média
3 - Mostrar maior nota
4 - Mostrar menor nota
0 - Sair
```

Utilize `sum()`, `len()`, `max()` e `min()` conforme a opção escolhida.

---

# Desafio — Central de Análise de Previsões

Crie uma lista vazia chamada `previsoes` e implemente:

```text
1 - Adicionar classificação
2 - Listar classificações
3 - Mostrar quantidade de gatos
4 - Mostrar quantidade de cachorros
5 - Mostrar total de classificações
0 - Sair
```

Requisitos:

1. Utilize `while` e `match-case` para controlar o menu;
2. Aceite apenas `"gato"`, `"cachorro"` e `"pássaro"` no cadastro;
3. Normalize a entrada com `.strip().lower()`;
4. Utilize outro `match-case` para validar a classificação antes de adicioná-la;
5. Utilize `for` e uma variável contadora para as opções de contagem;
6. Informe quando a lista estiver vazia;
7. Trate opções inválidas e permita encerrar o sistema.

> Dica: no cadastro, `case "gato" | "cachorro" | "pássaro":` permite agrupar as classificações aceitas.

