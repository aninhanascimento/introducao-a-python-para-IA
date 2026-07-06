# Aula: Funções em Python



# 1. O que são funções?

Uma **função** é um bloco de código criado para executar uma tarefa específica.

Em vez de repetir o mesmo código várias vezes, criamos uma função e chamamos essa função sempre que precisarmos.

## Analogia

Imagine uma máquina de café.

Você aperta um botão e ela executa várias etapas internamente:

- esquenta a água;
- passa o café;
- coloca na xícara;
- entrega a bebida pronta.

Você não precisa repetir manualmente todo o processo. Basta chamar a função da máquina: **fazer café**.

Em programação, uma função funciona de forma parecida.

---

# 2. Por que usar funções?

Usamos funções para:

- evitar repetição de código;
- organizar melhor o programa;
- facilitar a leitura;
- reaproveitar comandos;
- dividir um problema grande em partes menores;
- facilitar manutenção e correção de erros.

## Exemplo sem função

```python
print("Olá, Maria! Seja bem-vinda ao sistema.")
print("Olá, João! Seja bem-vindo ao sistema.")
print("Olá, Ana! Seja bem-vinda ao sistema.")
```

Nesse exemplo, repetimos a mesma ideia várias vezes.

## Exemplo com função

```python
# Criando uma função chamada saudacao

def saudacao(nome):
    print(f"Olá, {nome}! Seja bem-vindo(a) ao sistema.")

# Chamando a função para diferentes pessoas
saudacao("Maria")
saudacao("João")
saudacao("Ana")
```

Agora o código ficou mais organizado e fácil de reaproveitar.

---

# 3. Como criar uma função em Python

Em Python, usamos a palavra-chave `def` para criar uma função.

## Estrutura básica

```python
def nome_da_funcao():
    # bloco de código da função
    print("Esta é uma função")
```

## Exemplo

```python
# Definindo uma função simples

def mensagem():
    print("Aprender Python é como montar blocos: um encaixe por vez!")

# Chamando a função
mensagem()
```

### Explicação

```python
def mensagem():
```

Cria uma função chamada `mensagem`.

```python
print("Aprender Python é como montar blocos: um encaixe por vez!")
```

É o comando que será executado quando a função for chamada.

```python
mensagem()
```

Chama a função, ou seja, manda o Python executar o código que está dentro dela.

---

# 4. Função sem parâmetro

Uma função sem parâmetro executa sempre a mesma tarefa.

```python
# Função sem parâmetro

def mostrar_menu():
    print("===== MENU =====")
    print("1 - Cadastrar")
    print("2 - Listar")
    print("3 - Sair")

# Chamando a função
mostrar_menu()
```

## Quando usar?

Use quando a função não precisa receber informações externas para funcionar.

---

# 5. Função com parâmetro

Parâmetros são informações que a função recebe para trabalhar.

## Analogia

Pense em uma receita de bolo.

A função seria: **fazer bolo**.

Os parâmetros seriam:

- sabor;
- tamanho;
- cobertura.

Dependendo dos ingredientes enviados, o resultado muda.

## Exemplo

```python
# Função com parâmetro

def apresentar_aluno(nome):
    print(f"O aluno {nome} está presente.")

# Chamando a função com valores diferentes
apresentar_aluno("Carlos")
apresentar_aluno("Beatriz")
apresentar_aluno("Fernanda")
```

### Explicação

A função recebe o valor dentro dos parênteses e usa esse valor no código.

```python
apresentar_aluno("Carlos")
```

Aqui, o valor `"Carlos"` é enviado para o parâmetro `nome`.

---

# 6. Função com mais de um parâmetro

Uma função pode receber vários parâmetros.

```python
# Função com dois parâmetros

def calcular_soma(numero1, numero2):
    soma = numero1 + numero2
    print(f"A soma é: {soma}")

# Chamando a função
calcular_soma(10, 5)
calcular_soma(20, 30)
```

## Exemplo com dados de aluno

```python
# Função que exibe informações de um aluno

def mostrar_aluno(nome, idade, curso):
    print("----- Dados do Aluno -----")
    print(f"Nome: {nome}")
    print(f"Idade: {idade}")
    print(f"Curso: {curso}")

# Chamando a função
mostrar_aluno("Maria", 19, "Python")
mostrar_aluno("João", 20, "Java")
```

---

# 7. Função com retorno

Algumas funções não apenas mostram algo na tela. Elas também podem **devolver um resultado**.

Para isso, usamos `return`.

## Analogia

Imagine uma calculadora.

Você informa dois números e uma operação.

A calculadora não apenas fala o que fez: ela entrega um resultado.

Esse resultado é o retorno.

## Exemplo

```python
# Função com retorno

def somar(a, b):
    resultado = a + b
    return resultado

# Guardando o retorno em uma variável
valor = somar(8, 4)

print(f"Resultado: {valor}")
```

### Explicação

```python
return resultado
```

Devolve o valor calculado para quem chamou a função.

---

# 8. Diferença entre print e return

Essa é uma dúvida muito comum.

## `print`

Mostra uma informação na tela.

```python
def mostrar_soma(a, b):
    print(a + b)

mostrar_soma(5, 3)
```

## `return`

Devolve um valor para ser usado depois.

```python
def retornar_soma(a, b):
    return a + b

resultado = retornar_soma(5, 3)
print(resultado)
```

## Comparação

| Comando | O que faz? | Pode ser reutilizado em cálculo? |
|---|---|---|
| `print` | Mostra na tela | Não diretamente |
| `return` | Devolve um valor | Sim |

## Exemplo prático

```python
# Função que retorna a média

def calcular_media(nota1, nota2):
    media = (nota1 + nota2) / 2
    return media

# Usando o retorno da função
media_aluno = calcular_media(8, 6)

if media_aluno >= 7:
    print("Aluno aprovado")
else:
    print("Aluno em recuperação")
```

Se a função usasse apenas `print`, seria mais difícil usar o resultado no `if`.

---

# 9. Parâmetro com valor padrão

Podemos definir valores padrão para parâmetros.

```python
# Função com valor padrão

def boas_vindas(nome="aluno"):
    print(f"Olá, {nome}! Bem-vindo(a) à aula de Python.")

# Chamando sem informar o nome
boas_vindas()

# Chamando informando o nome
boas_vindas("Mariana")
```

### Resultado esperado

```text
Olá, aluno! Bem-vindo(a) à aula de Python.
Olá, Mariana! Bem-vindo(a) à aula de Python.
```

---

# 10. Argumentos nomeados

Podemos chamar uma função informando o nome dos parâmetros.

```python
# Função com três parâmetros

def cadastrar_produto(nome, preco, quantidade):
    print("Produto cadastrado:")
    print(f"Nome: {nome}")
    print(f"Preço: R$ {preco}")
    print(f"Quantidade: {quantidade}")

# Chamando com argumentos nomeados
cadastrar_produto(nome="Mouse", preco=49.90, quantidade=10)
```

Também podemos mudar a ordem se usarmos os nomes:

```python
cadastrar_produto(quantidade=5, nome="Teclado", preco=120.00)
```

---

# 11. Função com lista

Funções também podem receber listas.

```python
# Função que mostra os nomes de uma lista

def listar_alunos(alunos):
    for aluno in alunos:
        print(f"Aluno: {aluno}")

# Lista de alunos
nomes = ["Ana", "Bruno", "Carla", "Diego"]

# Chamando a função
listar_alunos(nomes)
```

---

# 12. Função que calcula média de uma lista

```python
# Função que calcula a média de várias notas

def calcular_media_notas(notas):
    soma = sum(notas)
    quantidade = len(notas)
    media = soma / quantidade
    return media

# Lista de notas
notas_aluno = [8, 7, 9, 6]

# Chamando a função
media = calcular_media_notas(notas_aluno)

print(f"Média final: {media}")
```

### Explicação

```python
sum(notas)
```

Soma todos os valores da lista.

```python
len(notas)
```

Conta quantos elementos existem na lista.

---

# 13. Função com decisão if/else

Podemos usar estruturas condicionais dentro de funções.

```python
# Função que verifica se o aluno foi aprovado

def verificar_aprovacao(media):
    if media >= 7:
        return "Aprovado"
    elif media >= 5:
        return "Recuperação"
    else:
        return "Reprovado"

# Testando a função
situacao = verificar_aprovacao(6.5)
print(f"Situação do aluno: {situacao}")
```

---

# 14. Função com repetição

Podemos usar laços dentro de funções.

```python
# Função que exibe a tabuada de um número

def mostrar_tabuada(numero):
    for i in range(1, 11):
        resultado = numero * i
        print(f"{numero} x {i} = {resultado}")

# Chamando a função
mostrar_tabuada(5)
```

---

# 15. Escopo de variável

Escopo é o local onde uma variável existe e pode ser usada.

## Variável local

Uma variável criada dentro de uma função só existe dentro dela.

```python
def exemplo():
    mensagem = "Estou dentro da função"
    print(mensagem)

exemplo()
```

Se tentarmos acessar `mensagem` fora da função, teremos erro:

```python
print(mensagem)

# Isto gera erro, pois mensagem existe apenas dentro da função

```

## Analogia

Imagine uma sala de aula.

O material que está dentro da sala pertence àquela sala. Se você estiver fora dela, não consegue usar diretamente aquele material.

Assim funciona uma variável local.

---

# 16. Boas práticas ao criar funções

Ao criar funções, procure:

- usar nomes claros;
- criar funções pequenas;
- fazer cada função ter uma responsabilidade principal;
- evitar repetir código;
- usar `return` quando precisar reutilizar o resultado;
- comentar o código quando necessário;
- evitar nomes genéricos como `coisa`, `teste`, `xpto`.

## Exemplos de nomes ruins
O **pass** é uma palavra reservada do Python que significa literalmente **"não faça nada"**
Nenhum erro acontece, porque o pass informa ao Python que aquele bloco está **vazio intencionalmente.**


```python
def coisa():
    pass

def faz():
    pass
```

## Exemplos de nomes melhores

```python
def calcular_media():
    pass

def cadastrar_aluno():
    pass

def verificar_idade():
    pass
```

---

# 17. Exemplo completo: sistema simples de alunos

```python
# Função para calcular a média do aluno

def calcular_media(nota1, nota2):
    media = (nota1 + nota2) / 2
    return media

# Função para verificar a situação do aluno

def verificar_situacao(media):
    if media >= 7:
        return "Aprovado"
    elif media >= 5:
        return "Recuperação"
    else:
        return "Reprovado"

# Função para mostrar o relatório final

def mostrar_relatorio(nome, nota1, nota2):
    media = calcular_media(nota1, nota2)
    situacao = verificar_situacao(media)

    print("===== RELATÓRIO DO ALUNO =====")
    print(f"Nome: {nome}")
    print(f"Nota 1: {nota1}")
    print(f"Nota 2: {nota2}")
    print(f"Média: {media}")
    print(f"Situação: {situacao}")

# Chamando a função principal
mostrar_relatorio("Maria", 8, 6)
```

## O que esse exemplo mostra?

Esse exemplo separa o problema em três partes:

1. calcular a média;
2. verificar a situação;
3. mostrar o relatório.

Isso deixa o código mais organizado, mais limpo e mais fácil de alterar depois.

---

# 18. Atividade guiada

Crie um programa em Python com funções para:

1. cadastrar o nome de um cliente;
2. receber dois valores de compra;
3. calcular a média;
4. verificar se o cliente tem desconto, (se valor acima de R$150,00, ele tem desconto de 10%);
5. exibir o cupom final com nome cliente, exibir os dois valores, total da compra, desconto, e valor final.

Use como base o exemplo anterior, mas tente escrever com seus próprios nomes de funções.

---

# 19. Lista de exercícios

## Exercício 1

Crie uma função chamada `mostrar_mensagem` que exiba a frase:

```text
Estou aprendendo funções em Python!
```

---

## Exercício 2

Crie uma função chamada `saudar_usuario` que receba um nome como parâmetro e mostre uma mensagem de boas-vindas.

Exemplo:

```text
Olá, Ana! Seja bem-vinda.
```

---

## Exercício 3

Crie uma função chamada `somar` que receba dois números e retorne a soma deles.

---

## Exercício 4

Crie uma função chamada `calcular_dobro` que receba um número e retorne o dobro desse número.

---

## Exercício 5

Crie uma função chamada `verificar_maioridade` que receba uma idade e retorne:

- `Maior de idade`, se a idade for maior ou igual a 18;
- `Menor de idade`, se for menor que 18.

---

## Exercício 6

Crie uma função chamada `calcular_media` que receba três notas e retorne a média.

---

## Exercício 7

Crie uma função chamada `verificar_aprovacao` que receba uma média e retorne:

- `Aprovado`, se a média for maior ou igual a 7;
- `Recuperação`, se a média for maior ou igual a 5 e menor que 7;
- `Reprovado`, se a média for menor que 5.

---

## Exercício 8

Crie uma função chamada `mostrar_tabuada` que receba um número e mostre a tabuada de 1 a 10.

---

## Exercício 9

Crie uma função chamada `calcular_area_retangulo` que receba a base e a altura de um retângulo e retorne a área.

Fórmula:

```text
área = base * altura
```

---

## Exercício 10

Crie uma função chamada `listar_produtos` que receba uma lista de produtos e mostre cada produto na tela.

---

## Exercício 11

Crie uma função chamada `calcular_total_compra` que receba uma lista de preços e retorne o valor total da compra.

---

## Exercício 12

Crie uma função chamada `contar_pares` que receba uma lista de números e retorne quantos números pares existem na lista.

---

## Exercício 13

Crie uma função chamada `converter_para_maiusculo` que receba uma palavra e retorne essa palavra em letras maiúsculas.

---

## Exercício 14

Crie uma função chamada `calcular_desconto` que receba o preço de um produto e o percentual de desconto. A função deve retornar o preço final.

Exemplo:

```text
Preço: 100
Desconto: 10%
Preço final: 90
```

---

#  Conclusão

Funções são fundamentais para escrever programas mais organizados, reutilizáveis e fáceis de manter.

Quando você cria uma função, está ensinando o computador a executar uma tarefa com nome próprio.

É como montar uma equipe dentro do seu código: cada função tem uma responsabilidade, e juntas elas resolvem problemas maiores.

