
Abaixo está uma lista organizada dos principais erros que podem ocorrer desde a Aula 01.

---

# Guia de Erros Mais Comuns em Machine Learning

## Aulas 01, 02 e 03

---

# 1. ModuleNotFoundError

## Erro

```python
ModuleNotFoundError: No module named 'pandas'
```

## Significado

A biblioteca não está instalada.

## Como resolver

No Google Colab normalmente já está instalada.

No computador:

```python
pip install pandas
```

ou

```python
pip install scikit-learn
```

---

# 2. NameError

## Erro

```python
NameError: name 'pd' is not defined
```

## Exemplo

```python
df = pd.DataFrame(dados)
```

sem executar

```python
import pandas as pd
```

---

## Solução

Importe primeiro:

```python
import pandas as pd
```

---

# 3. FileNotFoundError

## Erro

```text
FileNotFoundError:
No such file or directory
```

---

## Significado

O Python não encontrou o arquivo.

---

## Exemplo

```python
df = pd.read_csv("arquivo.csv")
```

Mas o arquivo não existe.

---

## Solução

No Google Colab:

```python
from google.colab import files

files.upload()
```

Depois:

```python
df = pd.read_csv("arquivo.csv")
```

---

# 4. UnicodeDecodeError

## Erro

```text
UnicodeDecodeError
```

---

## Significado

O arquivo CSV foi salvo em outra codificação.

---

## Solução

```python
df = pd.read_csv(
    "arquivo.csv",
    encoding="latin1"
)
```

ou

```python
encoding="ISO-8859-1"
```

---

# 5. ParserError

## Erro

```text
ParserError:
Error tokenizing data
```

---

## Significado

O separador do CSV está errado.

---

Arquivo

```csv
Nome;Idade
João;20
```

Código

```python
pd.read_csv("arquivo.csv")
```

---

## Solução

```python
pd.read_csv(
    "arquivo.csv",
    sep=";"
)
```

---

# 6. KeyError

## Erro

```python
KeyError: 'idade'
```

---

## Exemplo

```python
df["idade"]
```

Mas a coluna chama:

```text
Idade
```

---

## Solução

Verifique:

```python
print(df.columns)
```

---

# 7. AttributeError

## Erro

```python
AttributeError:
'DataFrame' object has no attribute 'heads'
```

---

## Exemplo

```python
df.heads()
```

---

## Correto

```python
df.head()
```

---

# 8. SyntaxError

## Erro

```python
print("Olá"
```

---

## Significado

Faltou fechar parênteses.

---

## Correto

```python
print("Olá")
```

---

# 9. IndentationError

## Erro

```python
if idade > 18:
print("Maior")
```

---

## Correto

```python
if idade > 18:
    print("Maior")
```

---

# 10. ValueError

## Erro

```python
ValueError:
could not convert string to float
```

---

## Exemplo

```python
float("vinte")
```

---

## Correto

```python
float("20")
```

---

# 11. TypeError

## Erro

```python
TypeError:
unsupported operand type(s)
```

---

## Exemplo

```python
"20" + 5
```

---

## Correto

```python
int("20") + 5
```

---

# 12. IndexError

## Erro

```python
IndexError:
list index out of range
```

---

## Exemplo

```python
lista = [1,2,3]

print(lista[5])
```

---

## Correto

```python
print(lista[2])
```

---

# 13. DecisionTree ainda não treinada

## Erro

```text
NotFittedError
```

---

## Exemplo

```python
modelo.predict(X)
```

antes de

```python
modelo.fit(X,y)
```

---

## Correto

```python
modelo.fit(X,y)

modelo.predict(X)
```

---

# 14. Número errado de Features

## Erro

```text
ValueError:
X has 1 features,
but DecisionTreeClassifier
is expecting 2
```

---

## Exemplo

Modelo treinado com

```python
idade
salario
```

Depois:

```python
modelo.predict([[25]])
```

---

## Correto

```python
modelo.predict([[25,3000]])
```

---

# 15. Ordem das Features

## Erro

```text
Feature names should match
```

---

Treinamento

```python
idade
salario
```

Previsão

```python
salario
idade
```

---

## Correto

Sempre utilizar a mesma ordem.

---

# 16. Erro ao usar Pandas

## Exemplo

```python
df["idade","salario"]
```

---

## Correto

```python
df[["idade","salario"]]
```

Observe os **dois pares de colchetes**.

---

# 17. Erro com predict()

## Errado

```python
modelo.predict([25,3000])
```

---

## Correto

```python
modelo.predict([[25,3000]])
```

---

## Por quê?

O algoritmo espera receber uma tabela.

Mesmo que exista apenas uma pessoa.

---

# 18. Erro com fit()

## Errado

```python
modelo.fit(df)
```

---

## Correto

```python
modelo.fit(X,y)
```

---

# 19. Erro após reiniciar o Google Colab

## Mensagem

```text
NameError
```

ou

```text
FileNotFoundError
```

---

## Motivo

Ao reiniciar o ambiente, todas as variáveis são apagadas e os arquivos enviados por upload deixam de existir.

---

## Solução

Executar novamente todas as células, na ordem correta, e reenviar o arquivo CSV se ele tiver sido carregado por upload.

---

# 20. Erro ao utilizar random_state

## Errado

```python
random_state="42"
```

---

## Correto

```python
random_state=42
```

O valor deve ser um número inteiro, não um texto.

---

# 21. Erro ao calcular a acurácia

## Errado

```python
accuracy_score(previsoes,y)
```

---

## Correto

```python
accuracy_score(y_teste, previsoes)
```

A ordem correta é:

```text
Resposta correta

↓

Resposta prevista
```

---

# 22. Erro ao dividir treino e teste

## Errado

```python
test_size=80
```

---

## Correto

```python
test_size=0.2
```

ou

```python
test_size=0.3
```

O valor representa uma **proporção**, e não uma porcentagem inteira.

---

# Fluxograma para Diagnóstico de Erros

```text
O código não executou?
        │
        ├──────────────┐
        │              │
Erro vermelho?     Resultado estranho?
        │              │
Leia a primeira     Verifique os dados
linha do erro       e as colunas
        │
Qual é o erro?
        │
├──────── FileNotFound?
│         Faça upload do CSV
│
├──────── Unicode?
│         encoding="latin1"
│
├──────── KeyError?
│         Confira os nomes das colunas
│
├──────── NotFitted?
│         Execute fit()
│
├──────── ValueError?
│         Verifique o formato dos dados
│
└──────── NameError?
          Execute novamente as células anteriores
```

## Dica para os alunos

Sempre leia **a primeira linha da mensagem de erro**, pois ela normalmente informa o tipo do problema (`FileNotFoundError`, `KeyError`, `ValueError`, etc.). Em seguida, leia a última linha destacada da mensagem, que costuma indicar exatamente em qual comando o erro ocorreu. Aprender a interpretar essas mensagens é uma habilidade essencial para qualquer profissional de Ciência de Dados e Machine Learning.
