---
title: "Série de Fourier: Descrição, Exemplo, Aplicação e Código"
date: 2025-05-10
draft: false
params:
  math: true
---


## O que é uma série de Fourier?

A Série de Fourier pode ser explicada através da música. Existem 7 notas, sendo elas: Dó, Ré, Mi, Fá, Sol, Lá e Si. Nessa ordem específica, é representada a escala de Dó maior. No intervalo entre elas geralmente há 1 tom; somente entre Mi/Fá e Si/Dó há um semitom separando-as. Isso acontece porque, diferente das demais notas, Mi e Si não possuem sua forma sustenido ou bemol.

Saindo da escala de Dó mostrada anteriormente, todas as notas têm sua própria escala maior, que é formada por um padrão de intervalos, sendo ele:
(tom - tom - semitom - tom - tom - tom - semitom).
Isso demonstra que a melodia, mesmo que em diferentes tonalidades, pode ser reproduzida se o padrão de intervalos se repetir.

Essa ideia de repetição, variações harmônicas e construção de melodias a partir de uma nota base se conecta diretamente com o conceito de Série de Fourier. Na música, quando se toca uma nota em um instrumento como o violão ou piano, na verdade não se ouve apenas aquela nota (frequência fundamental), mas também uma série de outras frequências mais altas que soam juntas com ela — esses são os harmônicos. Eles são múltiplos inteiros da frequência fundamental.

De maneira semelhante, a Série de Fourier afirma que qualquer função periódica pode ser decomposta em uma soma de funções senoidais (seno e cosseno) com diferentes frequências, amplitudes e fases. A frequência mais baixa é chamada de frequência fundamental, e as demais são seus múltiplos inteiros (os harmônicos), assim como ocorre com os sons musicais.

A forma geral da Série de Fourier para uma função periódica \( f(t) \) com período \(T\) é dada por:


\begin{align*}f(t) = a_0 + \sum_{n=1}^{\infty} \left[a_n \cos\left(\frac{2\pi n t}{T}\right) + b_n \sin\left(\frac{2\pi n t}{T}\right)\right]\end{align*}


Onde: \(a_0\) representa a média da função no intervalo (parte constante, semelhante a um “tom base”);
\(a_n\) e \(b_n\) são os coeficientes que determinam a amplitude dos cossenos e senos;
\(n\) representa o número do harmônico (o "grau" da nota);
\(\frac{2πn}{T}\) é a frequência angular dos harmônicos.

Assim como em uma composição musical complexa, onde uma nota fundamental é enriquecida com harmônicos para formar um timbre único, uma função complexa pode ser "tocada" como uma composição de senos e cossenos com diferentes frequências e amplitudes.

Portanto, da mesma forma que é possível compor melodias diferentes mantendo o padrão de intervalos (como nas escalas maiores), é possível representar diferentes funções periódicas através de combinações específicas de ondas senoidais — sendo a Série de Fourier o método matemático que descreve exatamente como fazer isso.


-Mostrar como ela é usada para modelar sinais periódicos (áudio, engenharia elétrica, etc.).


### Transmissão de Sinais (telecomunicações):

Na transmissão de sinais, como rádio, TV e internet, os sinais são modulados em diferentes frequências. A decomposição de um sinal em suas frequências (análise espectral via Fourier) permite:

- Compressão de dados;

- Detecção e correção de erros;

- Filtragem e separação de canais.

Por exemplo, um sinal digital (com pulsos) pode ser modelado e transmitido como a soma de senos e cossenos. Isso é essencial para modulações como AM, FM, e OFDM (usado em Wi-Fi e 4G).

### Áudio e som:

No áudio, todo som periódico pode ser decomposto em uma combinação de ondas senoidais. Por exemplo, a forma de onda de uma nota musical tocada em um instrumento pode parecer complexa, mas matematicamente, ela é a soma de várias senoides com diferentes frequências e amplitudes.

A representação matemática é:

\begin{align*}f(t) = a_0 + \sum_{n=1}^{\infty} \left[ a_n \cos\left( \frac{2\pi n t}{T} \right) + b_n \sin\left( \frac{2\pi n t}{T} \right) \right]\end{align*}

Aqui:

- \(f(t)\): sinal sonoro (onda sonora);
- \(T\): período da onda sonora (inverso da frequência fundamental);
- \(a_n\),\(b_n\): coeficientes que controlam a “cor” do som (ou timbre);
- Os termos de seno e cosseno modelam os harmônicos.

Um violino e uma flauta tocando a mesma nota (mesma frequência fundamental) terão diferentes coeficientes \(a_n\) e \(b_n\), e por isso soam diferentes.


Engenharia elétrica:
Na engenharia elétrica, especialmente em sistemas de corrente alternada (CA), a Série de Fourier é usada para analisar sinais não senoidais — como sinais quadrados, triangulares ou dentados — que aparecem em circuitos com comutadores ou eletrônica de potência (por exemplo, em inversores ou fontes chaveadas).

Um exemplo clássico: a forma de onda quadrada com período T pode ser modelada pela Série de Fourier como:

\begin{align*}f(t) = \frac{4}{\pi} \sum_{n=1,3,5,\ldots}^{\infty} \frac{1}{n} \sin\left( \frac{2\pi n t}{T} \right)\end{align*}

Observe que:

- Apenas harmônicos ímpares estão presentes (1º, 3º, 5º...);

- A amplitude de cada harmônico decresce com \(\frac{1}{n}\).

Esse tipo de análise permite projetar filtros que removem harmônicos indesejados, ou prever como um sistema vai responder a diferentes componentes de frequência.



Queremos representar a função:

\(f(x) = x,\text{para } x \in [-\pi, \pi]\) como uma série de senos e cossenos.

- \(T = 2𝜋\)

calculando os coeficientes:



\(a_0 = \frac{1}{\pi} \int_{-\pi}^{\pi} x \, dx = 0\) (porque a função é ímpar: a área negativa anula a positiva)


\(a_n = \frac{1}{\pi} \int_{-\pi}^{\pi} x \cos(nx) \, dx = 0\) ( por simetria: \(xcos(nx)\) é uma função ímpar, então a integral em \([−π,π]\) também dá zero )



\(b_n = \frac{1}{\pi} \int_{-\pi}^{\pi} x \sin(nx) \, dx\)

Essa é uma função par, então podemos usar simetria:

\(b_n = \frac{2}{\pi} \int_{0}^{\pi} x \sin(nx) \, dx\)

Integração por partes (ou tabela de integrais):


$$b_n = \frac{2}{\pi} \left[ -\frac{x \cos(nx)}{n} \Big|_0^\pi + \frac{1}{n} \int_0^\pi \cos(nx) \, dx \right]$$

$$b_n = \frac{2}{\pi} \left( -\frac{\pi \cos(n\pi)}{n} + \frac{1}{n^2} \sin(n\pi) \right)$$

Como \(sin(nπ)=0\) e \(cos(nπ)=(−1)^n\), temos:


$$b_n = \frac{2}{\pi} \cdot \left( -\frac{\pi (-1)^n}{n} \right) = \frac{2 (-1)^{n+1}}{n}$$

Série final:

$$f(x) = x = \sum_{n=1}^{\infty} \frac{2 (-1)^{n+1}}{n} \sin(nx)$$


Observações:
A série contém somente termos de seno, pois \(f(x)=x\) é uma função ímpar.

A série é uma soma infinita de senos com coeficientes alternados (positivo/negativo).

Essa série converge para \(f(x)=x\) no intervalo \((−π,π)\), e fora desse intervalo, ela se repete com período \(2π\) (continuação periódica).

## Código em Python

Vamos plotar o gráfico de \(f(x)=x\) em Python para visualizar a aproximação de forma mais fácil

```python
import numpy as np
import matplotlib.pyplot as plt

def f(x): # f(x) = x
    return x

def b_n(n): # Coeficientes b_n
    return (2 / np.pi) * (-1)**(n+1) / n

def fourier(x, termos):
    resultado = np.zeros_like(x)
    for n in range(1, termos+1):
        resultado += b_n(n) * np.sin(n * x)
    return resultado

# Gerando os pontos x
x = np.linspace(-np.pi, np.pi, 400)

y_exact = f(x)
y_approx = fourier(x, 10) # aproximando com 10 termos

# Plotando o gráfico
plt.figure(figsize=(10, 6))
plt.plot(x, y_exact, label="f(x) = x", color='blue', linestyle='-', linewidth=2)
plt.plot(x, y_approx, label=f"Aproximação (N = {N})", color='red', linestyle='--', linewidth=2)
plt.xlabel("x")
plt.ylabel("f(x)")
plt.title("Aproximação de f(x) = x com a Série de Fourier")
plt.legend()
plt.grid(True)
plt.show()
```

![](/images/fourier.png)
