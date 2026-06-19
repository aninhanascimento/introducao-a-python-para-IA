# Aula 01 — Introdução ao Machine Learning
**Duração: 4h | Modalidade: Expositiva + Prática (Google Colab)**

---

## Bloco 1 — O que é Machine Learning 

**Definição:** ML é a área da computação em que o sistema aprende padrões a partir de dados, em vez de seguir regras explicitamente programadas.

**ML vs. programação tradicional**

| Programação tradicional | Machine Learning |
|---|---|
| Regras + Dados → Resultado | Dados + Resultado → Regras |
| Programador escreve a lógica | Algoritmo descobre a lógica |

**Analogia central:** Ensinar uma criança a reconhecer cachorros.
- *Abordagem tradicional:* você lista regras ("tem 4 patas, late, tem rabo"). Mas e um cachorro de 3 patas? E um lobo, que também late?
- *Abordagem ML:* você mostra centenas de fotos de cachorros (e de "não-cachorros") e deixa a criança (o modelo) descobrir sozinha os padrões que distinguem um cachorro.

**Outro exemplo prático:** Filtro de spam.
- Tradicional: programador escreve regra fixa "se contém a palavra 'grátis', é spam" — fácil de burlar.
- ML: o sistema aprende, a partir de milhares de e-mails já classificados, quais combinações de padrões indicam spam — e se adapta a novos truques.

**Discussão em sala:** Dê exemplos do cotidiano onde "regras fixas" falhariam e ML seria mais adequado.

---

## Bloco 2 — Tipos de Aprendizado 

### 1. Aprendizado Supervisionado 
O modelo aprende com exemplos rotulados (entrada + resposta correta).

**Analogia:** Um aluno estudando com um gabarito ao lado — vê a pergunta, tenta responder, confere com a resposta certa e ajusta seu raciocínio.

- **Regressão:** prever um valor numérico (ex: preço de uma casa).
- **Classificação:** prever uma categoria (ex: e-mail é spam ou não).

### 2. Aprendizado Não Supervisionado 
O modelo recebe dados **sem rótulos** e precisa encontrar padrões ou agrupamentos por conta própria.

**Analogia:** Organizar uma caixa de botões misturados sem instruções — você naturalmente os agrupa por cor, tamanho ou formato, mesmo sem alguém dizer como.

- **Clustering:** agrupar elementos semelhantes (ex: segmentação de clientes).
- **Redução de dimensionalidade:** simplificar dados complexos mantendo o essencial.

### 3. Aprendizado por Reforço 
O modelo aprende por tentativa e erro, recebendo recompensas ou punições conforme suas ações.

**Analogia:** Treinar um cachorro com petiscos — ele não recebe um manual, mas aprende por repetição quais ações geram recompensa.

---

## Bloco 3 — Ciclo de Vida de um Projeto de ML 

```
1. Definição do problema
2. Coleta de dados
3. Preparação/limpeza dos dados
4. Divisão treino/teste
5. Treinamento do modelo
6. Avaliação do modelo
7. Ajustes (voltar a 3, 5 ou 6, se necessário)
8. Implantação (deploy) e monitoramento
```

**Analogia:** É como o ciclo de aprovação de um prato novo em um restaurante — definir o prato (problema), comprar ingredientes (dados), preparar (limpeza), testar em um grupo pequeno (treino/teste), servir (deploy) e ajustar a receita conforme o feedback.

> As etapas 2 e 3 consomem ~70-80% do tempo real de um projeto de ML.

---

## Bloco 4 — Casos de Uso Reais 

| Aplicação | Tipo de aprendizado | Exemplo |
|---|---|---|
| Recomendação de produtos | Supervisionado/Não supervisionado | Netflix, Spotify |
| Detecção de fraude | Supervisionado | Cartões de crédito |
| Visão computacional | Supervisionado | Diagnóstico por imagem |
| Segmentação de clientes | Não supervisionado | Marketing |
| Carros autônomos | Reforço | Navegação |

---

## Bloco 5 — Prática no Google Colab 

### Passo 1 — Configuração do ambiente 

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

print("Ambiente pronto!")
```

**Explicando linha por linha:**
- `import pandas as pd` → importa a biblioteca **pandas**, usada para trabalhar com tabelas de dados (chamadas de *DataFrames*). O `as pd` é um "apelido" — em vez de escrever `pandas.algumacoisa()` toda vez, escrevemos `pd.algumacoisa()`. É uma convenção que todo mundo usa, então os alunos vão encontrar esse padrão em qualquer material de ML.
- `import matplotlib.pyplot as plt` → importa o módulo de gráficos do **matplotlib**, apelidado de `plt`. É a biblioteca base de visualização em Python.
- `import seaborn as sns` → importa o **seaborn**, uma biblioteca construída em cima do matplotlib que facilita gráficos estatísticos mais bonitos com menos código. Apelido `sns` é convenção (vem do nome de uma personagem da série *The West Wing*, curiosidade besteira que pode descontrair a aula).
- `print("Ambiente pronto!")` → apenas confirma visualmente que as células rodaram sem erro. Não tem função técnica, é só feedback para o aluno.

> Não precisamos instalar nada (`!pip install`) porque essas três bibliotecas já vêm pré-instaladas no Google Colab.

---

### Passo 2 — Carregar e explorar o dataset

```python
from sklearn.datasets import load_iris

iris = load_iris(as_frame=True)
df = iris.frame

df.head()
```

**Explicando linha por linha:**
- `from sklearn.datasets import load_iris` → o scikit-learn (`sklearn`) traz alguns datasets clássicos já embutidos, prontos para uso didático. Aqui importamos a função `load_iris`, que carrega o famoso dataset **Iris** (150 flores, 3 espécies, 4 medidas por flor).
- `iris = load_iris(as_frame=True)` → executa a função e guarda o resultado na variável `iris`. O parâmetro `as_frame=True` diz "me devolva os dados já organizados como uma tabela pandas (DataFrame)", em vez do formato bruto (array NumPy), que é mais difícil de visualizar para iniciantes.
- `df = iris.frame` → o objeto `iris` carregado guarda várias informações (dados, descrição, nomes das colunas...). `.frame` é especificamente a tabela de dados pronta. Guardamos essa tabela na variável `df` (abreviação comum de *DataFrame*).
- `df.head()` → método do pandas que mostra **as primeiras 5 linhas** da tabela. É o primeiro comando que qualquer pessoa roda ao abrir um dataset novo — serve para "dar uma espiada" na estrutura dos dados sem imprimir a tabela inteira.

```python
df.info()
df.describe()
```

**Explicando linha por linha:**
- `df.info()` → mostra um resumo técnico da tabela: quantas linhas e colunas existem, o tipo de dado de cada coluna (número inteiro, decimal, texto...) e se há valores faltantes. É o comando para entender "do que essa tabela é feita".
- `df.describe()` → gera estatísticas resumidas de cada coluna numérica: média, desvio padrão, valor mínimo, valor máximo e os quartis (25%, 50%, 75%). Serve para ter uma primeira noção da distribuição dos dados, sem precisar olhar linha por linha.

**Discussão guiada:** O que são as colunas? O que representa a coluna `target`? Quantas espécies existem?

---

### Passo 3 — Visualização exploratória 

```python
df['target'].value_counts()
```

**Explicando:**
- `df['target']` → seleciona apenas a coluna chamada `target` da tabela (a coluna que indica a espécie da flor, codificada como 0, 1 ou 2).
- `.value_counts()` → método que conta quantas vezes cada valor aparece nessa coluna. Aqui, vai mostrar quantas flores existem de cada espécie — útil para verificar se o dataset está **balanceado** (quantidade parecida entre as classes) ou **desbalanceado**.

```python
sns.scatterplot(data=df, x='petal length (cm)', y='petal width (cm)', hue='target', palette='deep')
plt.title('Distribuição das espécies por características da pétala')
plt.show()
```

**Explicando linha por linha:**
- `sns.scatterplot(...)` → cria um **gráfico de dispersão** (cada ponto = uma flor), usando o seaborn.
  - `data=df` → diz qual tabela usar como fonte dos dados.
  - `x='petal length (cm)'` → define o eixo horizontal (comprimento da pétala).
  - `y='petal width (cm)'` → define o eixo vertical (largura da pétala).
  - `hue='target'` → colore os pontos de acordo com a espécie (essa é a parte mais importante: permite ver visualmente se as espécies se separam naturalmente no gráfico).
  - `palette='deep'` → define o conjunto de cores usado (é só uma escolha estética/paleta pronta do seaborn).
- `plt.title('...')` → adiciona um título ao gráfico, usando o matplotlib (o seaborn é construído sobre ele, então comandos do `plt` continuam funcionando).
- `plt.show()` → renderiza o gráfico na tela. Sem esse comando, em alguns ambientes o gráfico pode não aparecer.

**Pergunta para os alunos:** Observando o gráfico, vocês conseguem imaginar uma "régua" (linha) que separe as espécies? *(Gancho para a Aula 4 — Regressão Linear, e Aula 5 — Classificação)*

---

### Passo 4 — Fechamento da prática 
Ainda não treinamos nenhum modelo — só **exploramos** os dados (etapas 2-3 do ciclo de vida visto no Bloco 4).

---

## Bloco 7 — Encerramento 
- Quais são os 3 tipos de aprendizado e o ciclo de vida?
- Apresentar a lista de exercícios (tarefa para casa).
- Prévia da Aula 2: matemática essencial (vetores, distâncias, médias).

---

## Lista de Exercícios — Aula 01

**Parte A — Conceitual**
1. Explique, com suas palavras, a diferença entre programação tradicional e Machine Learning.
2. Dê um exemplo do seu cotidiano que poderia ser resolvido com ML. Justifique por que regras fixas não seriam suficientes.
3. Classifique cada cenário como supervisionado, não supervisionado ou por reforço, justificando:
   a) Prever se um aluno vai ou não ser aprovado, com base no histórico de notas de alunos anteriores.
   b) Agrupar clientes de um e-commerce em perfis de compra, sem informação prévia sobre esses perfis.
   c) Um robô aprendendo a andar, recebendo "pontos" quando avança e "penalidades" quando cai.
4. Por que a etapa de preparação de dados costuma consumir mais tempo que o treinamento do modelo?
5. Cite dois riscos éticos possíveis no uso de ML em decisões que afetam pessoas.

**Parte B — Prática (Google Colab)**
6. Usando o dataset Iris, calcule a média e o desvio padrão de cada característica para cada espécie separadamente. *(Dica: `df.groupby('target').describe()`)*
7. Crie um gráfico de dispersão usando `sepal length` e `sepal width` em vez de pétala. As espécies ficam tão bem separadas? Comente.
8. Carregue outro dataset do scikit-learn (`load_wine()` ou `load_breast_cancer()`), repita `head()`, `info()`, `describe()` e escreva 3 observações.

**Parte C — Reflexão**
9. Escolha um app do dia a dia e identifique duas funcionalidades que provavelmente usam ML. Que tipo de aprendizado cada uma usa?

---

