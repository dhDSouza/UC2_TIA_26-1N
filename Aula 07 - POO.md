# Aula 07 - Introdução à Programação Orientada a Objetos em Python

## Objetivos da aula

Ao final desta aula, o aluno deverá ser capaz de:

- Compreender os conceitos de classe e objeto;
- Definir classes utilizando `class`;
- Inicializar atributos com `__init__`;
- Utilizar `self` para acessar os dados de um objeto;
- Criar métodos que consultam e modificam atributos;
- Trabalhar com vários objetos e listas de objetos;
- Integrar objetos a um menu com `while` e `match-case`.

> Pré-requisitos: variáveis, condições, listas, laços e funções da Aula 06. O exemplo com `match-case` requer Python 3.10 ou posterior.

---

# 1. O que é Programação Orientada a Objetos?

Na Aula 06, organizamos tarefas em funções e armazenamos suas descrições em uma lista. Agora imagine que cada tarefa também precisa indicar se foi concluída.

Podemos representar cada tarefa como um **objeto**, reunindo seus dados e as operações relacionadas a eles.

A **Programação Orientada a Objetos (POO)** é uma forma de organizar programas em torno desses objetos.

| Conceito | Significado | Exemplo |
| --- | --- | --- |
| Classe | Define uma estrutura e os comportamentos dos objetos | `Tarefa` |
| Objeto ou instância | Um elemento criado a partir da classe | Uma tarefa de estudar Python |
| Atributo | Um dado associado ao objeto | Descrição e situação da tarefa |
| Método | Uma função definida na classe | Concluir a tarefa |

Uma classe pode originar vários objetos. Cada tarefa pode ter sua própria descrição e sua própria situação.

POO pode ser combinada com funções, listas e estruturas de controle que já conhecemos.

---

# 2. Criando uma Classe e seus Objetos

Vamos começar com uma classe que representa um aluno:

```python
class Aluno:
    def __init__(self, nome, curso):
        self.nome = nome
        self.curso = curso


aluno1 = Aluno("Ana", "Python")
aluno2 = Aluno("Bruno", "Inteligência Artificial")

print(aluno1.nome)
print(aluno2.nome)
print(aluno2.curso)
```

Saída:

```text
Ana
Bruno
Inteligência Artificial
```

Nesse exemplo:

1. `class Aluno:` inicia a definição da classe;
2. `__init__` inicializa os dados de cada nova instância;
3. `self.nome` e `self.curso` são atributos de instância;
4. `Aluno("Ana", "Python")` cria uma instância e inicializa seus atributos;
5. `aluno1` guarda uma referência ao objeto criado;
6. O ponto permite acessar um atributo, como em `aluno1.nome`.

Utilize nomes de classes como `Aluno`, `ContaBancaria` e `ModeloIA`, com iniciais maiúsculas e sem espaços. Para atributos e métodos, utilize nomes como `nome` e `calcular_media`.

---

# 3. Entendendo `__init__` e `self`

O método especial `__init__` é chamado automaticamente durante a instanciação, depois que a instância foi criada, para inicializar seus dados. Ele possui **dois sublinhados antes e depois** de `init`.

Na definição:

```python
class Aluno:
    def __init__(self, nome, curso):
        self.nome = nome
        self.curso = curso
```

- `nome` e `curso` são parâmetros locais do método;
- `self` se refere à instância que está sendo inicializada;
- `self.nome = nome` guarda o valor recebido no atributo do objeto.

Quando escrevemos `Aluno("Ana", "Python")`, fornecemos os argumentos de `nome` e `curso`. O Python passa a instância como `self` automaticamente.

O nome `self` é uma convenção da linguagem que devemos seguir. Ele também será o primeiro parâmetro dos métodos de instância desta aula.

> `__init__` não deve retornar um resultado com `return valor`. Sua responsabilidade é inicializar a instância.

---

# 4. Consultando e Alterando Atributos

Cada objeto do exemplo possui seus próprios atributos:

```python
class Aluno:
    def __init__(self, nome, curso):
        self.nome = nome
        self.curso = curso


aluno1 = Aluno("Ana", "Python")
aluno2 = Aluno("Bruno", "Python")

aluno1.curso = "Inteligência Artificial"

print(aluno1.curso)
print(aluno2.curso)
```

Saída:

```text
Inteligência Artificial
Python
```

A alteração em `aluno1.curso` não modifica `aluno2.curso`.

Entretanto, atribuir uma variável a outra não cria uma cópia do objeto:

```python
outro_nome = aluno1
outro_nome.curso = "Análise de Dados"

print(aluno1.curso)
```

Saída:

```text
Análise de Dados
```

Esse último trecho continua o exemplo anterior: `outro_nome` e `aluno1` se referem ao mesmo objeto, assim como duas variáveis podem se referir à mesma lista.

---

# 5. Criando Métodos

Um método de instância é uma função definida na classe que recebe a instância como primeiro argumento. Ele pode utilizar os atributos do objeto para realizar uma tarefa.

```python
class Aluno:
    def __init__(self, nome, curso):
        self.nome = nome
        self.curso = curso

    def apresentar(self):
        return f"{self.nome} estuda {self.curso}."

    def alterar_curso(self, novo_curso):
        if novo_curso.strip() == "":
            return False

        self.curso = novo_curso.strip()
        return True


aluno = Aluno("Ana", "Python")
print(aluno.apresentar())

if aluno.alterar_curso("Inteligência Artificial"):
    print("Curso atualizado.")

print(aluno.apresentar())
```

Saída:

```text
Ana estuda Python.
Curso atualizado.
Ana estuda Inteligência Artificial.
```

A chamada `aluno.apresentar()` utiliza automaticamente `aluno` como `self`. Em `aluno.alterar_curso("Inteligência Artificial")`, o texto é recebido por `novo_curso`.

Como nas funções da Aula 06, o `return` devolve um resultado. O método `apresentar()` retorna uma mensagem; o `print()` fora da classe a exibe.

O método `alterar_curso()` reúne uma regra e uma alteração de estado: cursos vazios são recusados e o atributo anterior é preservado.

---

# 6. Atributos com Valores Iniciais

Nem todo atributo precisa receber um argumento. Podemos definir um estado inicial no próprio método `__init__`:

```python
class Tarefa:
    def __init__(self, descricao):
        self.descricao = descricao
        self.concluida = False

    def concluir(self):
        self.concluida = True

    def resumo(self):
        if self.concluida:
            situacao = "Concluída"
        else:
            situacao = "Pendente"

        return f"{self.descricao} - {situacao}"


tarefa = Tarefa("Estudar Python")
print(tarefa.resumo())

tarefa.concluir()
print(tarefa.resumo())
```

Saída:

```text
Estudar Python - Pendente
Estudar Python - Concluída
```

Cada nova tarefa começa com `concluida` igual a `False`. O método `concluir()` modifica esse estado para `True`.

Como `concluir()` não possui `return` explícito, seu retorno é `None`. Para observar a mudança, consultamos o objeto após a chamada.

---

# 7. Listas de Objetos

Uma lista pode armazenar objetos criados a partir de uma classe:

```python
class Tarefa:
    def __init__(self, descricao):
        self.descricao = descricao
        self.concluida = False

    def concluir(self):
        self.concluida = True


tarefas = [Tarefa("Estudar Python"), Tarefa("Resolver exercícios")]
tarefas[0].concluir()

for tarefa in tarefas:
    print(tarefa.descricao, tarefa.concluida)
```

Saída:

```text
Estudar Python True
Resolver exercícios False
```

`tarefas[0]` acessa o primeiro objeto da lista. No `for`, a variável `tarefa` se refere a um objeto a cada repetição.

## Cuidado com listas compartilhadas

Se cada objeto precisar de uma lista própria, crie essa lista em `__init__`:

```python
class Turma:
    def __init__(self, nome):
        self.nome = nome
        self.alunos = []

    def adicionar_aluno(self, nome):
        self.alunos.append(nome)


turma1 = Turma("Turma A")
turma2 = Turma("Turma B")

turma1.adicionar_aluno("Ana")

print(turma1.alunos)
print(turma2.alunos)
```

Saída:

```text
['Ana']
[]
```

Uma lista definida diretamente no corpo da classe, como `alunos = []` fora dos métodos, seria um atributo de classe, compartilhado pelas instâncias que o acessam sem substituí-lo. Para os dados individuais desta aula, utilizaremos atributos criados com `self` em `__init__`.

---

# 8. Exemplo Prático: Sistema de Tarefas com Objetos

Na Aula 06, cada tarefa era apenas um texto. Agora cada tarefa será um objeto com descrição, situação e métodos.

Copie o código completo para um arquivo Python:

```python
class Tarefa:
    def __init__(self, descricao):
        self.descricao = descricao
        self.concluida = False

    def concluir(self):
        self.concluida = True

    def resumo(self):
        if self.concluida:
            situacao = "Concluída"
        else:
            situacao = "Pendente"

        return f"{self.descricao} - {situacao}"


def mostrar_menu():
    print("\n=== SISTEMA DE TAREFAS ===")
    print("1 - Adicionar tarefa")
    print("2 - Listar tarefas")
    print("3 - Concluir tarefa pela descrição")
    print("4 - Mostrar quantidade de pendentes")
    print("0 - Sair")


def buscar_tarefa(tarefas, descricao):
    for tarefa in tarefas:
        if tarefa.descricao.lower() == descricao.lower():
            return tarefa

    return None


tarefas = []

while True:
    mostrar_menu()
    opcao = input("Escolha uma opção: ").strip().lower()

    match opcao:
        case "1":
            descricao = input("Digite a tarefa: ").strip()

            if descricao == "":
                print("A descrição não pode ficar vazia.")
            elif buscar_tarefa(tarefas, descricao) is not None:
                print("Já existe uma tarefa com essa descrição.")
            else:
                tarefas.append(Tarefa(descricao))
                print("Tarefa adicionada.")

        case "2":
            if len(tarefas) == 0:
                print("Nenhuma tarefa cadastrada.")
            else:
                for tarefa in tarefas:
                    print(tarefa.resumo())

        case "3":
            descricao = input("Digite a tarefa a concluir: ").strip()
            tarefa = buscar_tarefa(tarefas, descricao)

            if tarefa is None:
                print("Tarefa não encontrada.")
            elif tarefa.concluida:
                print("Essa tarefa já foi concluída.")
            else:
                tarefa.concluir()
                print("Tarefa concluída.")

        case "4":
            pendentes = 0
            for tarefa in tarefas:
                if not tarefa.concluida:
                    pendentes += 1

            print(f"Tarefas pendentes: {pendentes}")

        case "0" | "sair":
            print("Encerrando o sistema...")
            break

        case _:
            print("Opção inválida.")
```

## Entendendo a organização

| Parte | Responsabilidade |
| --- | --- |
| Classe `Tarefa` | Representar os dados e o comportamento de uma tarefa |
| `concluir()` | Alterar a situação do objeto |
| `resumo()` | Retornar uma mensagem com os dados do objeto |
| `buscar_tarefa()` | Localizar um objeto na lista ou retornar `None` |
| Lista `tarefas` | Manter referências aos objetos cadastrados |
| `while` e `match-case` | Receber escolhas e coordenar as operações |

`is None` verifica se a busca retornou a ausência de resultado. `is not None` verifica se ela encontrou um objeto. Já `not tarefa.concluida` será verdadeiro quando o atributo for `False`.

A busca retorna o próprio objeto da lista. Por isso, chamar `tarefa.concluir()` modifica a tarefa armazenada, sem precisar substituí-la na lista.

As descrições são comparadas sem diferenciar maiúsculas de minúsculas, mas o texto original é preservado para exibição. A validação de descrições vazias e repetidas fica no cadastro deste programa; a classe `Tarefa`, isoladamente, não faz essas verificações.

Os dados permanecem apenas na memória e são perdidos ao encerrar o programa.

## Roteiro de teste

1. Liste as tarefas antes de cadastrar: o programa deve informar que a lista está vazia;
2. Cadastre `Estudar Python`: a tarefa deve aparecer como pendente;
3. Tente cadastrar ` estudar python `: o programa deve recusar a repetição;
4. Tente cadastrar apenas espaços: o programa deve recusar a descrição;
5. Consulte a quantidade de pendentes: deve ser `1`;
6. Conclua `ESTUDAR PYTHON`: a tarefa deve aparecer como concluída e a quantidade de pendentes deve ser `0`;
7. Tente concluir a mesma tarefa novamente e uma descrição inexistente: confira as mensagens;
8. Digite uma opção desconhecida e depois `0` para encerrar.

---

# 9. Organização e Encapsulamento

Ao reunir dados e operações em uma classe, podemos concentrar as regras relacionadas a um objeto em seus métodos. Esse é um primeiro contato com **encapsulamento**.

No exemplo de `Aluno`, `alterar_curso()` verifica o texto antes de alterar o atributo. Porém, os atributos usados nesta aula são públicos: escrever `aluno.curso = ""` ainda é permitido e contorna a validação do método.

Portanto, criar um método não impede automaticamente o acesso direto aos atributos. Nesta etapa, seguiremos a organização proposta e chamaremos os métodos para executar operações com regras.

Herança e polimorfismo são outros conceitos de POO que podem ser estudados após consolidar classes, instâncias e métodos.

---

# 10. Cuidados ao Trabalhar com Classes

- Respeite a indentação: os métodos ficam dentro da classe e suas instruções dentro dos métodos;
- Escreva `__init__` com dois sublinhados de cada lado;
- Utilize `self` como primeiro parâmetro dos métodos de instância;
- Use `self.nome` para guardar um atributo; apenas `nome` seria um nome local;
- Crie uma instância antes de chamar seus métodos de instância;
- Use parênteses para executar um método: `tarefa.concluir()`;
- Crie listas individuais dentro de `__init__`;
- Lembre-se de que atribuir um objeto a outra variável não o copia;
- Diferencie o retorno de um método da alteração dos atributos do objeto.

---

# Exercícios

## Exercício 1 — Cadastro de Livros

Crie a classe `Livro` com os atributos `titulo` e `autor`, recebidos em `__init__`.

Crie dois objetos e exiba seus dados. Altere o título de apenas um deles e confira que o outro permanece com seu título original.

---

## Exercício 2 — Apresentação de um Produto

Crie a classe `Produto` com os atributos `nome` e `preco`.

Implemente `resumo()` para retornar uma mensagem com o nome e o preço com duas casas decimais. Utilize `print()` fora da classe para exibir o retorno.

Teste com `Produto("Caderno", 15.5)`: o resumo deve apresentar o preço `15.50`.

> Dica: em uma f-string, `{self.preco:.2f}` formata o valor com duas casas decimais. Considere preços numéricos não negativos neste exercício.

---

## Exercício 3 — Contador

Crie a classe `Contador`, cujo atributo `valor` começa em `0`.

Implemente os métodos `incrementar()` e `zerar()`. Crie dois contadores, incremente apenas o primeiro três vezes e exiba os valores dos dois.

Resultado esperado: `3` e `0`. Depois, zere o primeiro e confira o resultado.

---

## Exercício 4 — Retângulo

Crie a classe `Retangulo` com `base` e `altura`.

Implemente `calcular_area()` e `calcular_perimetro()`, ambos com retorno. Considere medidas numéricas positivas.

Teste com base `5` e altura `3`: a área deve ser `15` e o perímetro deve ser `16`.

---

## Exercício 5 — Aluno com Notas

Crie a classe `Aluno` com `nome` e uma lista `notas` inicialmente vazia, criada em `__init__`.

Implemente:

- `adicionar_nota(nota)`: aceitar apenas números entre `0` e `10`, adicionar a nota válida e retornar `True`; fora do intervalo, retornar `False` sem alterar a lista;
- `calcular_media()`: retornar a média ou `None` quando a lista estiver vazia.

Considere que os argumentos de notas já são numéricos. Crie dois alunos e confira que adicionar notas a um deles não altera as notas do outro.

Teste notas `8` e `6`, cuja média é `7.0`, e tente adicionar `-1` e `11`. Fora da classe, trate o retorno `None` antes de formatar ou comparar a média.

---

## Exercício 6 — Resultados de Classificação

Crie a classe `ResultadoClassificacao` com `categoria` e `confianca`. Considere que a confiança recebida é um número entre `0` e `1`.

Implemente `eh_confiavel(limite=0.8)` para retornar `True` quando a confiança for maior ou igual ao limite, ou `False` caso contrário.

Armazene três objetos em uma lista e utilize `for` para mostrar a categoria e o retorno do método.

Teste as confianças `0.95`, `0.8` e `0.6`: com o limite padrão, os retornos devem ser `True`, `True` e `False`.

Esses objetos representam resultados simulados; o exercício não executa um modelo de IA.

---

## Exercício 7 — Reabrindo Tarefas

Adicione à classe `Tarefa` do exemplo completo o método `reabrir()`, que altera `concluida` para `False`.

Inclua no menu uma opção para reabrir uma tarefa pela descrição. Trate tarefa inexistente e tarefa que já está pendente.

Cadastre duas tarefas, conclua apenas uma, reabra essa tarefa e confira a lista e a contagem de pendentes após cada operação.

---

# Desafio — Biblioteca com Objetos

Desenvolva um sistema com uma lista de objetos da classe `Livro` e o seguinte menu:

```text
1 - Cadastrar livro
2 - Listar livros
3 - Emprestar livro pelo título
4 - Devolver livro pelo título
5 - Mostrar quantidade de livros disponíveis
0 - Sair
```

Requisitos:

1. Inicialize cada livro com `titulo`, `autor` e `disponivel = True`;
2. Crie `emprestar()` para retornar `False` se o livro já estiver emprestado; caso contrário, altere `disponivel` para `False` e retorne `True`;
3. Crie `devolver()` para retornar `False` se o livro já estiver disponível; caso contrário, altere `disponivel` para `True` e retorne `True`;
4. Crie `resumo()` para retornar título, autor e situação do livro;
5. Crie a função `buscar_livro(livros, titulo)` para retornar o objeto encontrado ou `None`;
6. No cadastro, remova espaços das extremidades e recuse títulos e autores vazios;
7. Impeça títulos repetidos e faça buscas sem diferenciar maiúsculas de minúsculas. Neste sistema simplificado, cada título representa um único exemplar;
8. Utilize `while`, `match-case` e uma lista criada antes do laço;
9. Use os métodos dos objetos para emprestar, devolver e obter os resumos;
10. Trate lista vazia, livro inexistente e opção inválida.

Teste o cadastro de dois livros, um título repetido e campos contendo apenas espaços. Empreste um livro, tente emprestá-lo novamente, devolva-o e tente devolvê-lo outra vez. Confira a contagem de disponíveis após cada mudança e teste a busca por um título inexistente.
