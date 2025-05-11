---
title: "Série de Taylor: Descrição, Exemplo, Aplicação e Código"
date: 2025-05-08
draft: false
description: "Entenda de forma intuitiva como a Série de Taylor funciona, com exemplo usando logaritmo neperiano, aplicações práticas em sensores e código Python para simulação."
params:
  math: true
---

## O que é a Série de Taylor?

Imagine que você tem uma função, como \( ln(x) \) ou \( sin(x) \), e quer aproximá-la com uma fórmula mais simples. Uma das alternativas é usar a Série de Taylor. Ela é descrita pela somatória abaixo:


\begin{align*}f\left( x \right) & = \sum\limits_{n = 0}^\infty {\frac{{{f^{\left( n \right)}}\left( a \right)}}{{n!}}{{\left( {x - a} \right)}^n}} \end{align*}


Ela é uma função que possui uma soma infinita de termos baseada em um número \(x \). Cada termo terá um expoente maior que o anterior e quanto mais termos, mais preciso será o resultado.

\begin{align*}f\left( a \right) + f'\left( a \right)\left( {x - a} \right) + \frac{{f''\left( a \right)}}{{2!}}{\left( {x - a} \right)^2} + \frac{{f'''\left( a \right)}}{{3!}}{\left( {x - a} \right)^3} + \cdots \end{align*}

## Como se usa?
Digamos que queremos aproximar a equação \( ln(x) \). Primeiramente, temos que saber quanta precisão é necessária, ou seja, quantos termos iremos usar. Neste caso, usaremos cinco termos para maior precisão. Um termo se refere a uma derivada, logo o segundo termo se refere a segunda derivada e assim segue. Vamos prosseguir:

\begin{align*} \ln(x) = (x - 1) - \frac{(x - 1)^2}{2} + \frac{(x - 1)^3}{3} - \frac{(x - 1)^4}{4} + \frac{(x - 1)^5}{5} - \dots \end{align*}

Para \(x = 2\), nós substituimos na série:

\begin{align*} ln(2) \approx (2 - 1) - \frac{(2 - 1)^2}{2} + \frac{(2 - 1)^3}{3} - \frac{(2 - 1)^4}{4} + \frac{(2 - 1)^5}{5}\end{align*}

Simplificando:

\begin{align*} ln(2) \approx 1 - \frac{1}{2} + \frac{1}{3} - \frac{1}{4} + \frac{1}{5}\end{align*}

$$ln(2) \approx 1 - 0.5 + 0.3333 - 0.25 + 0.2$$

$$ln(2) \approx 0.7833$$

## Aplicações da série na vida real:
- **Sensores**: Sensores de pressão e temperatura frequentemente fornecem dados que podem ser aproximados por séries de Taylor, especialmente quando os sensores têm uma relação não linear com a variável medida.


- **Física**: Em experimentos de física, especialmente em sistemas dinâmicos ou termodinâmicos, a Série de Taylor pode ser usada para aproximar funções complexas, como \(e^x\) ou \(ln(x)\), de maneira eficiente, sem recorrer a métodos numéricos mais pesados.

- **Microcontroladores**: Em microcontroladores, onde o poder de processamento é limitado, as Séries de Taylor podem ser usadas para simplificar cálculos, como logaritmos, exponenciais e funções trigonométricas. Isso é particularmente útil em algoritmos que precisam ser rápidos e eficientes, como em sistemas embarcados com sensores ou controle de sistemas.

## Código em Python

Abaixo está um código em Python implementando a série de Taylor para \(ln(x)\):

```python
import numpy as np
import matplotlib.pyplot as plt

def taylor_ln(x, termos=10):
    resultado = 0
    for n in range(1, termos+1):
        resultado += ((-1) ** (n+1)) * ((x - 1) ** n) / n # Fórmula da série de Taylor para ln(x)
    return resultado

#valores possíveis de x no intervalo 0.1 < x < 2
valores_x = np.linspace(0.1, 2, 400)
y_taylor = [taylor_ln(x, termos=10) for x in valores_x]
y_exato = np.log(valores_x)  

plt.figure(figsize=(8, 6))
plt.plot(valores_x, y_exato, label="ln(x)", color="black", linestyle="--", linewidth=2)
plt.plot(valores_x, y_taylor, label="ln(x) na Série de Taylor(10 termos)", linestyle="--", linewidth=2)
plt.title("Aproximação de Taylor para ln(x)", fontsize=14)
plt.xlabel("x", fontsize=12)
plt.ylabel("ln(x)", fontsize=12)
plt.legend()
plt.grid(True)

```
![Série de Taylor criada em Python](/images/taylor.png)
