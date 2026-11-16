# Aula 08 - Análise de Dados com Pandas

## Objetivos da aula

Ao final desta aula, o aluno deverá ser capaz de:

- Compreender o papel da análise de dados;
- Criar e consultar tabelas com Pandas;
- Ler um arquivo CSV;
- Selecionar colunas e filtrar registros;
- Identificar e preencher valores ausentes;
- Calcular indicadores e agrupar informações;
- Exportar os resultados para um novo arquivo CSV.

**Material de apoio:** [vendas_aula08.csv](vendas_aula08.csv). Os dados são fictícios e representam vendas de uma papelaria.

---

# 1. O que é Análise de Dados?

Analisar dados é organizar e examinar informações para responder perguntas. Uma papelaria pode usar seus registros para descobrir:

- Quantas unidades foram vendidas?
- Qual foi o faturamento total?
- Qual produto gerou mais receita?
- Existem informações faltando?

O **Pandas** é uma biblioteca do Python que oferece ferramentas para trabalhar com tabelas.

| Conceito | Significado |
| --- | --- |
| DataFrame | Uma tabela com linhas e colunas |
| Series | Uma sequência de valores com índice, como uma coluna da tabela |
| Índice | Identifica as linhas; nos exemplos, começa em zero |
| CSV | Arquivo de texto que armazena registros separados por um delimitador |

Cada linha do nosso arquivo representa um registro de venda de um produto. Um produto pode aparecer em várias linhas.

---

# 2. Preparando o Ambiente

Em um ambiente local com Python, execute no terminal:

```bash
python -m pip install pandas
```

Crie um arquivo chamado `analise_aula08.py` na mesma pasta de `vendas_aula08.csv`. Abra o terminal nessa pasta para executar os exemplos.

Também é possível usar um notebook no Google Colab: envie o CSV para a área de arquivos da sessão antes de executar a leitura. Nesse ambiente, o Pandas normalmente já está disponível.

Importe a biblioteca no início do código:

```python
import pandas as pd
```

O nome `pd` é um apelido usado por convenção.

---

# 3. Criando uma Primeira Tabela

Podemos criar um DataFrame a partir de um dicionário de listas:

```python
import pandas as pd

dados = {
    "produto": ["Caderno", "Caneta", "Lápis"],
    "quantidade": [3, 10, 8]
}

exemplo = pd.DataFrame(dados)
print(exemplo)
```

As chaves do dicionário se tornam nomes de colunas. As listas devem ter o mesmo tamanho.

---

# 4. Lendo o Arquivo CSV

A partir desta seção, execute os exemplos em sequência, utilizando a variável `df`:

```python
import pandas as pd

df = pd.read_csv("vendas_aula08.csv", encoding="utf-8")
print(df)
```

O arquivo fornecido usa vírgula para separar colunas e ponto como separador decimal.

| Coluna | Significado |
| --- | --- |
| `produto` | Nome do produto vendido |
| `categoria` | Grupo do produto; há um campo vazio proposital |
| `quantidade` | Unidades vendidas naquele registro |
| `preco_unitario` | Preço de uma unidade, em reais |

Para arquivos que usam ponto e vírgula entre colunas e vírgula decimal, a leitura seria `pd.read_csv("outro_arquivo.csv", sep=";", decimal=",")`. Os parâmetros devem corresponder ao arquivo utilizado.

> Se aparecer `FileNotFoundError`, confira o nome do arquivo e a pasta em que o terminal está aberto. No Colab, confira se o CSV foi enviado para a sessão.

---

# 5. Conhecendo os Dados

```python
# Primeiras cinco linhas
print(df.head())

# Quantidade de linhas e colunas
print(df.shape)

# Nomes das colunas
print(df.columns)

# Tipos de dados e quantidade de valores preenchidos
df.info()

# Resumo estatístico das colunas numéricas
print(df.describe())
```

Antes de criar novas colunas, `df.shape` retorna `(6, 4)`: seis registros e quatro colunas.

O `describe()` apresenta contagem, média, desvio padrão, mínimo, quartis e máximo das colunas numéricas. A média da coluna `quantidade` representa a média de unidades por registro.

**Pergunta para a turma:** seis registros significam seis produtos diferentes?

Não. Para contar os produtos distintos:

```python
print(df["produto"].nunique())  # 4
```

---

# 6. Selecionando Colunas e Filtrando Linhas

## Uma coluna

```python
print(df["produto"])
```

O resultado é uma Series.

## Várias colunas

```python
print(df[["produto", "quantidade"]])
```

Passamos uma lista de nomes dentro dos colchetes. O resultado é um DataFrame.

## Filtrando por quantidade

```python
vendas_maiores = df[df["quantidade"] >= 5]
print(vendas_maiores)
```

A comparação verifica a condição em cada linha. O filtro mantém as linhas em que o resultado é verdadeiro.

## Filtrando por produto

```python
print(df[df["produto"] == "Caderno"])
```

## Combinando condições

```python
filtro = df[
    (df["categoria"] == "Escrita") &
    (df["quantidade"] >= 5)
]

print(filtro)
```

Use `&` para combinar condições com “e” e `|` para combinar com “ou”. Coloque cada condição entre parênteses; não use `and` e `or` para essas comparações entre colunas.

---

# 7. Tratando Valores Ausentes

A categoria da borracha está vazia no CSV. O Pandas reconhece esse campo como ausente; a forma de exibição pode variar conforme o tipo da coluna.

```python
# Quantidade de valores ausentes em cada coluna
print(df.isna().sum())

# Linhas com categoria ausente
print(df[df["categoria"].isna()])
```

Neste exemplo, vamos preencher a categoria com um rótulo:

```python
df["categoria"] = df["categoria"].fillna("Não informada")
print(df.isna().sum())
```

Depois do preenchimento, todas as colunas terão zero valores ausentes.

Essa decisão depende do significado dos dados. Um preço ausente precisa ser investigado antes de ser substituído por zero, pois isso afeta o faturamento calculado.

---

# 8. Criando Colunas e Calculando Indicadores

O valor de cada venda é a quantidade multiplicada pelo preço unitário:

```python
df["valor_total"] = df["quantidade"] * df["preco_unitario"]
print(df[["produto", "quantidade", "preco_unitario", "valor_total"]])
```

O Pandas faz a operação linha a linha, sem precisarmos escrever um `for`.

```python
faturamento = df["valor_total"].sum()
unidades = df["quantidade"].sum()
media_por_registro = df["valor_total"].mean()

print(f"Faturamento total: R$ {faturamento:.2f}")
print(f"Unidades vendidas: {unidades}")
print(f"Valor médio por registro: R$ {media_por_registro:.2f}")
```

Saída esperada:

```text
Faturamento total: R$ 161.50
Unidades vendidas: 32
Valor médio por registro: R$ 26.92
```

O formato `.2f` exibe duas casas decimais. A receita calculada não representa lucro: o arquivo não contém os custos dos produtos.

---

# 9. Agrupando e Ordenando Dados

Para somar a receita de cada produto:

```python
receita_por_produto = (
    df.groupby("produto")["valor_total"]
    .sum()
    .sort_values(ascending=False)
)

print(receita_por_produto)
```

O `groupby()` reúne os registros por produto, `sum()` soma os valores de cada grupo e `sort_values()` organiza do maior para o menor.

| Produto | Receita (R$) |
| --- | ---: |
| Caderno | 100,00 |
| Caneta | 37,50 |
| Borracha | 12,00 |
| Lápis | 12,00 |

Para descobrir a quantidade de unidades por produto:

```python
unidades_por_produto = (
    df.groupby("produto")["quantidade"]
    .sum()
    .sort_values(ascending=False)
)

print(unidades_por_produto)
```

A caneta teve mais unidades vendidas: 15. O caderno gerou mais receita: R$ 100,00. Cada medida responde a uma pergunta diferente.

Para ordenar os registros individuais pelo valor de cada venda:

```python
print(df.sort_values("valor_total", ascending=False))
```

---

# 10. Salvando a Análise

```python
df.to_csv("vendas_analisadas.csv", index=False, encoding="utf-8-sig")
```

O novo arquivo contém a categoria preenchida e a coluna `valor_total`. O parâmetro `index=False` evita gravar o índice como uma coluna extra. A codificação `utf-8-sig` ajuda no reconhecimento de acentos em programas de planilha.

O caminho relativo salva o arquivo na pasta de execução. Execute o comando novamente apenas quando quiser atualizar esse arquivo de saída.

---

# 11. Exemplo Completo

Salve como `analise_aula08.py` e execute com `python analise_aula08.py`, no terminal aberto na pasta do CSV:

```python
import pandas as pd

df = pd.read_csv("vendas_aula08.csv", encoding="utf-8")

print("=== PRIMEIRAS LINHAS ===")
print(df.head())

print("\n=== VALORES AUSENTES ===")
print(df.isna().sum())

df["categoria"] = df["categoria"].fillna("Não informada")
df["valor_total"] = df["quantidade"] * df["preco_unitario"]

print("\n=== INDICADORES ===")
print(f"Registros de venda: {len(df)}")
print(f"Unidades vendidas: {df['quantidade'].sum()}")
print(f"Faturamento: R$ {df['valor_total'].sum():.2f}")

print("\n=== RECEITA POR PRODUTO ===")
print(
    df.groupby("produto")["valor_total"]
    .sum()
    .sort_values(ascending=False)
)

df.to_csv("vendas_analisadas.csv", index=False, encoding="utf-8-sig")
print("\nArquivo vendas_analisadas.csv salvo.")
```

---

# Exercícios

Utilize o CSV fornecido. Preencha a categoria ausente e crie `valor_total` antes dos exercícios que precisam dessas informações.

## Exercício 1 — Explorando a Tabela

Mostre as três primeiras linhas, a quantidade de registros e os nomes das colunas. Quantos produtos diferentes existem?

## Exercício 2 — Selecionando Informações

Exiba somente `produto` e `valor_total`.

## Exercício 3 — Filtrando Vendas

Mostre os registros com valor total superior a R$ 20. Depois, filtre apenas os registros de caneta.

## Exercício 4 — Quantidade por Produto

Calcule o total de unidades por produto e ordene do maior para o menor. Qual produto lidera?

## Exercício 5 — Receita por Categoria

Calcule o faturamento de cada categoria, incluindo `Não informada`.

## Exercício 6 — Exportando um Filtro

Salve as vendas com valor total superior a R$ 20 em `vendas_acima_20.csv`, sem exportar o índice.
