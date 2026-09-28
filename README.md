Exercício guiado 1: Saudação
```python
def saudar(nome):
    return "Ola, " + nome + "!"
print(saudar("Ana"))
# Ola, Ana!
msg = saudar("Edilson")
print(msg.upper())
```
Exercício guiado 2: Valor padrão
```python
def media(a, b, casas=2): 
    m = (a + b) / 2 
    return round(m, casas) 
print(media(8, 6)) 
# 7.0 
print(media(8, 5, 1)) 
# 6.5
```
Exercício guiado 3: *args
```python
def total(*precos, desc=0):
    s = sum(precos)
    return s * (1 - desc / 100)
print(total(10, 25.5, 7))
# 42.5
print(total(10, 25.5, 7, desc=10))
# 38.25
```
Exercício guiado 4: Objeto mutável
```python
def reg(nota, boletim=None):
    """Nao altera a lista original."""
    if boletim is None:
        boletim = []
    novo = boletim[:]   # copia
    novo.append(nota)
    return novo notas = [7]
print(reg(9, notas))  # [7, 9]
print(notas)          # [7]
```
Exercício guiado 5: Módulo importado
```python
# script_desafio.py
from calculadora import somar, \
                        multiplicar
def orc(qtd, preco, frete=0):
    """Total do pedido."""
    s = multiplicar(qtd, preco)
    return somar(s, frete)
print(orc(3, 49.9, 15))  # 164.7
```
Prática Independente

Conversor: crie celsius_para_fahrenheit(c) e devolva o valor com return.
```python
def celsius_para_fahrenheit(c):
    return (c * 9/5) + 32
```
Validador: retorne True se a senha tiver 8 ou mais caracteres.
```python
def validar_senha(senha):
    return len(senha) >= 8
```
Caixa: função com *precos que retorna total, item mais caro e média.
```python
def caixa(*precos):
    if not precos:
        return 0, 0, 0
    total = sum(precos)
    mais_caro = max(precos)
    media = total / len(precos)
    return total, mais_caro, media
```
Ficha do aluno: função com **dados que imprime umainformação por linha.
```python
def ficha_aluno(**dados):
    for chave, valor in dados.items():
        # Substitui o underline por espaço e capitaliza para uma exibição mais limpa
        print(f"{chave.replace('_', ' ').title()}: {valor}")
```
Módulo utilidades.py: três funções e um script que o importa.
```python
def formatar_moeda(valor):
    return f"R$ {valor:,.2f}"

def saudar(nome):
    return f"Olá, {nome}! Seja bem-vindo(a)."

def calcular_desconto(preco, percentual):
    return preco * (1 - percentual / 100)
```
```python
import utilidades

# Testando as funções do módulo importado
print(utilidades.saudar("Carlos"))
print(utilidades.formatar_moeda(1500.50))
print(f"Preço com desconto: {utilidades.calcular_desconto(100, 15)}")

```
Lista segura: adicione um item sem alterar a lista original (use cópia).
```python
def adicionar_item_seguro(lista_original, novo_item):
    # Cria uma cópia rasa da lista para não modificar a original
    nova_lista = lista_original.copy()
    nova_lista.append(novo_item)
    return nova_lista

# Exemplo de uso:
# compras = ['arroz', 'feijão']
# nova_compras = adicionar_item_seguro(compras, 'azeite')
#print(compras)      # Mantém: ['arroz', 'feijão']
#print(nova_compras) # Retorna: ['arroz', 'feijão', 'azeite']

```
Desafios bônus

Módulo estatistica.py: media, mediana e moda, com alias est
```python
"""Módulo para cálculos estatísticos básicos."""

from collections import Counter

def calcular_media(valores):
    """Calcula a média aritmética de uma lista de números.
    
    Argumentos:
        valores (list): Lista com números (int ou float).
    Retorna:
        float: O valor da média.
    """
    if not valores:
        return 0
    return sum(valores) / len(valores)

def calcular_mediana(valores):
    """Calcula a mediana de uma lista de números.
    
    Argumentos:
        valores (list): Lista com números (int ou float).
    Retorna:
        float: O valor da mediana.
    """
    if not valores:
        return 0
    ordenados = sorted(valores)
    n = len(ordenados)
    meio = n // 2
    
    if n % 2 == 1:
        return ordenados[meio]
    return (ordenados[meio - 1] + ordenados[meio]) / 2

def calcular_moda(valores):
    """Calcula a(s) moda(s) de uma lista de números.
    
    Argumentos:
        valores (list): Lista com números.
    Retorna:
        list: Lista com o(s) valor(es) mais frequente(s).
    """
    if not valores:
        return []
    contador = Counter(valores)
    maior_frequencia = max(contador.values())
    return [item for item, freq in contador.items() if freq == maior_frequencia]
```
```python
import estatistica as est

dados = [1, 2, 2, 3, 4, 7, 9]

print(f"Média: {est.calcular_media(dados)}")       # 4.0
print(f"Mediana: {est.calcular_mediana(dados)}")   # 3
print(f"Moda: {est.calcular_moda(dados)}")         # [2]
```
Função recursiva fatorial(n): compare com Portugol com repetição
```python
def fatorial_recursivo(n):
    """Calcula o fatorial de um número inteiro de forma recursiva.
    
    Argumentos:
        n (int): Número inteiro não-negativo.
    Retorna:
        int: O resultado do fatorial.
    """
    if n <= 1:
        return 1
    return n * fatorial_recursivo(n - 1)

# COMPARATIVO: PORTUGOL COM REPETIÇÃO (Iterativo)
# 
# programa {
#     funcao inicio() {
#         inteiro n, fatorial = 1, i
#         escreva("Digite um número: ")
#         leia(n)
#         
#         // Abordagem com repetição (enquanto ou para)
#         para(i = n; i > 1; i--) {
#             fatorial = fatorial * i
#         }
#         
#         escreva("O fatorial é: ", fatorial)
#     }
# }

# Teste da função Python
print(f"Fatorial de 5 (Recursivo): {fatorial_recursivo(5)}")  # 120

```
Função relatorio(titulo, *linhas, **config) que formata texto
```python
def relatorio(titulo, *linhas, **config):
    """Gera um relatório textual formatado dinamicamente.
    
    Argumentos:
        titulo (str): O título principal do relatório.
        *linhas (str): Múltiplas strings representando as linhas de conteúdo.
        **config (opcionais):
            caractere_borda (str): Caractere para desenhar as divisórias (padrão '*').
            maiusculo (bool): Transforma o título em caixa alta se True (padrão False).
    """
    # Define valores padrão usando os kwargs passados ou defaults seguros
    borda = config.get("caractere_borda", "*")
    caixa_alta = config.get("maiusculo", False)
    
    texto_titulo = titulo.upper() if caixa_alta else titulo
    largura = max(len(texto_titulo), max((len(l) for l in linhas), default=0)) + 4
    
    # Montagem do layout do relatório
    print(borda * largura)
    print(f"{borda} {texto_titulo.center(largura - 4)} {borda}")
    print(borda * largura)
    
    for linha in linhas:
        print(f"{borda} {linha.ljust(largura - 4)} {borda}")
        
    print(borda * largura)

# Teste da função
relatorio(
    "Vendas Mensais", 
    "Produto A: R$ 500", 
    "Produto B: R$ 1.200", 
    caractere_borda="-", 
    maiusculo=True
)
```
