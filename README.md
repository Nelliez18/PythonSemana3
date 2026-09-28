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
# 1. Conversor
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

