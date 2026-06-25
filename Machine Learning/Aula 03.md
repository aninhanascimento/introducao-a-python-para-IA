
Até agora vimos:

* ✅ O que é Machine Learning.
* ✅ O que é um Dataset.
* ✅ Utilizar Pandas.
* ✅ Utilizar NumPy.
* ✅ Criar um modelo simples com `DecisionTreeClassifier`.
* ✅ Utilizar `fit()` e `predict()`.

Agora chegou o momento de responder uma pergunta muito importante:

> **Como saber se o modelo realmente aprendeu ou apenas decorou os exemplos?**

Essa será a motivação da aula.

---

# Aula 03 – Treinando e Avaliando Modelos de Machine Learning

**Carga horária:** 4 horas

## Objetivos da Aula

Ao final desta aula você será capaz de:

* Entender por que dividir os dados em treino e teste.
* Conhecer o conceito de generalização.
* Utilizar `train_test_split()`.
* Criar um modelo de Machine Learning utilizando dados de treino.
* Avaliar o modelo utilizando dados de teste.
* Entender os conceitos de Overfitting e Underfitting.
* Calcular a acurácia do modelo.

---

# Relembrando

Na aula passada fizemos:

```text
Dataset
      ↓
DataFrame
      ↓
Features (X)
      ↓
Target (y)
      ↓
fit()
      ↓
predict()
```

Funcionou!

Mas existe um problema...

---

# O problema

Imagine que um professor queira saber se um aluno realmente aprendeu matemática.

Ele faz isso:

Durante um mês:

```
2 + 2 = ?
```

O aluno responde:

```
4
```

Depois de repetir cem vezes...

Na prova...

O professor pergunta novamente:

```
2 + 2 = ?
```

O aluno responde:

```
4
```

O professor conclui:

> "O aluno aprendeu."

Será?

Não necessariamente.

Talvez ele apenas decorou aquela conta.

---

## Em Machine Learning acontece exatamente a mesma coisa.

Se utilizarmos os mesmos dados para ensinar e para avaliar o modelo...

Ele poderá simplesmente decorar.

Isso NÃO significa que ele sabe resolver novos problemas.

---

# Analogia

Imagine ensinar uma criança as respostas da prova.

Na prova você faz exatamente as mesmas perguntas.

Ela tira nota 10.

Mas será que ela aprendeu?

Provavelmente não.

---

# Generalização

O verdadeiro objetivo da IA é conseguir responder perguntas que ela nunca viu.

Isso chama-se:

## Generalização

Ou seja:

```
Aprender padrões
```

e não

```
Decorar respostas.
```

---

# Como resolver?

Dividimos os dados.

```
Dados completos
        │
        ├─────────────┐
        │             │
Treinamento       Teste
```

---

## Dados de Treinamento

Servem para ensinar.

---

## Dados de Teste

Servem para verificar se realmente aprendeu.

---

# Conhecendo o train_test_split

Vamos importar uma nova função.

```python
from sklearn.model_selection import train_test_split
```

---

## Explicando linha por linha

### from

Importar algo específico.

---

### sklearn

Biblioteca Scikit-Learn.

---

### model_selection

Módulo responsável pela preparação dos modelos.

---

### train_test_split

Função que divide automaticamente o dataset.

---

# Criando nosso Dataset

```python
import pandas as pd

dados = {
    "idade": [18,20,22,25,27,30,35,40,45,50],
    "salario": [1500,1800,2200,3000,3500,4000,5000,6000,7000,8000],
    "comprou": [0,0,0,1,1,1,1,1,1,1]
}

df = pd.DataFrame(dados)

display(df)
```

---

# Separando Features e Target

```python
X = df[["idade","salario"]]

y = df["comprou"]
```

---

# Dividindo os Dados

```python
from sklearn.model_selection import train_test_split

X_treino, X_teste, y_treino, y_teste = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

---

# Entendendo cada parâmetro

## X

São as Features.

---

## y

São as respostas.

---

## test_size

Indica quanto será reservado para teste.

```python
test_size=0.2
```

significa:

```
20% teste

80% treino
```

---

## random_state

Pergunta comum:

> Professor... por que usar 42?

Resposta:

Porque a divisão é aleatória.

Sem definir o `random_state`, a cada execução o computador poderá separar pessoas diferentes para treino e teste.

Ao definir um número fixo, garantimos que a divisão será sempre a mesma.

O número **42** virou uma convenção entre programadores (uma referência bem-humorada ao livro *O Guia do Mochileiro das Galáxias*), mas poderia ser **7**, **10**, **100** ou qualquer outro inteiro.

O importante é manter o mesmo valor para reproduzir os resultados.

---

# Criando o Modelo

```python
from sklearn.tree import DecisionTreeClassifier

modelo = DecisionTreeClassifier()
```

---

# Treinando

Agora atenção!

Antes utilizávamos:

```python
modelo.fit(X,y)
```

Agora fazemos:

```python
modelo.fit(X_treino,y_treino)
```

Estamos ensinando apenas com os dados de treinamento.

---

# Fazendo Previsões

```python
previsoes = modelo.predict(X_teste)
```

---

# O que existe dentro de previsões?

```python
print(previsoes)
```

Exemplo:

```
[1 0]
```

---

# Comparando

Resposta prevista:

```
[1 0]
```

Resposta correta:

```python
print(y_teste.values)
```

Exemplo:

```
[1 1]
```

Observe que uma previsão foi correta.

Outra não.

---

# Como medir isso?

Utilizamos uma métrica.

---

# Acurácia

Importando:

```python
from sklearn.metrics import accuracy_score
```

---

Calculando:

```python
acuracia = accuracy_score(
    y_teste,
    previsoes
)

print(acuracia)
```

Resultado:

```
0.90
```

---

# O que significa?

A acurácia varia entre:

```
0
```

e

```
1
```

ou

```
0%

até

100%
```

---

Exemplos

```
0.55

↓

55%
```

---

```
0.90

↓

90%
```

---

# Mas cuidado!

Imagine uma escola com:

```
100 alunos
```

95 foram aprovados.

5 reprovaram.

Uma IA responde:

```
Todo mundo passou.
```

Ela acertará:

```
95%
```

Mesmo sem identificar nenhum reprovado.

Por isso, futuramente estudaremos outras métricas além da acurácia.

---

# Overfitting

Imagine um aluno que decorou exatamente os exercícios do livro.

Na prova aparece um exercício diferente.

Ele não consegue resolver.

Isso é Overfitting.

```
Decorou
↓

Não aprendeu
```

---

# Underfitting

Agora imagine outro aluno.

Ele estudou apenas cinco minutos.

Não consegue responder nem os exercícios do livro.

Isso é Underfitting.

```
Nem decorou
↓

Nem aprendeu
```

---

# Objetivo

Queremos um modelo que:

```
Aprenda padrões

↓

Generalize

↓

Resolva situações novas.
```

---

# Código Completo

```python
import pandas as pd

from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

dados = {
    "idade":[18,20,22,25,27,30,35,40,45,50],
    "salario":[1500,1800,2200,3000,3500,4000,5000,6000,7000,8000],
    "comprou":[0,0,0,1,1,1,1,1,1,1]
}

df = pd.DataFrame(dados)

X = df[["idade","salario"]]
y = df["comprou"]

X_treino, X_teste, y_treino, y_teste = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

modelo = DecisionTreeClassifier()

modelo.fit(X_treino, y_treino)

previsoes = modelo.predict(X_teste)

print("Previsões:")
print(previsoes)

print("\nRespostas corretas:")
print(y_teste.values)

acuracia = accuracy_score(y_teste, previsoes)

print(f"\nAcurácia: {acuracia:.2%}")
```

---

# Exercício Prático

Utilize o mesmo código da aula e altere:

* `test_size` para `0.3`.
* `random_state` para `10`.

Compare:

* A divisão dos dados mudou?
* A acurácia mudou?
* O modelo fez as mesmas previsões?

Explique por que isso aconteceu.

---

# Desafio da Aula

Crie um novo conjunto de dados com as colunas:

| Horas de Estudo | Faltas | Aprovado |
| --------------- | ------ | -------- |
| 2               | 10     | 0        |
| 4               | 5      | 1        |
| 1               | 12     | 0        |
| 6               | 2      | 1        |
| 8               | 0      | 1        |
| 3               | 8      | 0        |
| 5               | 4      | 1        |
| 7               | 1      | 1        |

1. Crie o DataFrame.
2. Separe `X` e `y`.
3. Divida os dados em treino e teste (`80%/20%`).
4. Treine uma Árvore de Decisão.
5. Faça previsões.
6. Calcule a acurácia.
7. Teste o modelo com um novo aluno que estudou **5 horas** e teve **3 faltas**.

---

# Resumo da Aula

Nesta aula aprendemos:

* ✅ Por que dividir os dados em treino e teste.
* ✅ O conceito de generalização.
* ✅ Como usar `train_test_split()`.
* ✅ O significado de `test_size` e `random_state`.
* ✅ Como treinar um modelo apenas com os dados de treino.
* ✅ Como realizar previsões com dados inéditos.
* ✅ Como calcular a acurácia.
* ✅ A diferença entre **Overfitting** e **Underfitting**.

### Próxima Aula

Na Aula 04, entraremos em um dos pilares da Ciência de Dados: **Análise Exploratória de Dados (EDA)**. Os alunos aprenderão a investigar datasets reais utilizando Pandas, identificar padrões, detectar inconsistências e preparar os dados para construir modelos mais confiáveis.
