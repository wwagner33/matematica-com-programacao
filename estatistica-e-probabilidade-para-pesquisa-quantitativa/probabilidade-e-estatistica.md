# **Introdução à Estatística e Probabilidade Aplicadas à Pesquisa Quantitativa e Análise Exploratória de Dados**

## **Índice**

1. **Introdução**

   - 1.1. O que é Estatística e Probabilidade?
   - 1.2. Importância na Pesquisa Quantitativa e Análise Exploratória de Dados

2. **Estatística Descritiva**

   - 2.1. Medidas de Tendência Central
     - Média
     - Mediana
     - Moda
   - 2.2. Medidas de Dispersão
     - Variância
     - Desvio Padrão
     - Amplitude
   - 2.3. Visualização de Dados
     - Histogramas
     - Boxplots
     - Gráficos Interativos com Plotly
   - 2.4. Implementações em Python
     - Exemplos Práticos
   - 2.5. Exercícios

3. **Probabilidade**

   - 3.1. Conceitos Básicos
     - Experimento Aleatório
     - Espaço Amostral
     - Evento
   - 3.2. Axiomas de Kolmogorov
     - Definições
     - Propriedades
   - 3.3. Probabilidade Condicional e Independência
     - Teorema da Multiplicação
     - Independência de Eventos
   - 3.4. Teorema de Bayes
     - Formulação
     - Aplicações em Previsões Médicas (Exemplo do Teste de HIV)
     - Outros Exemplos Práticos
   - 3.5. Implementações em Python
     - Exemplos Práticos com Plotly
   - 3.6. Exercícios

4. **Distribuições Probabilísticas**

   - 4.1. Variáveis Aleatórias Discretas
     - Distribuição Binomial
     - Distribuição de Poisson
   - 4.2. Variáveis Aleatórias Contínuas
     - Distribuição Normal
     - Distribuição Exponencial
   - 4.3. Função Densidade de Probabilidade (PDF) e Função Distribuição Cumulativa (CDF)
   - 4.4. Implementações em Python
     - Exemplos Práticos com Plotly
   - 4.5. Exercícios

5. **Inferência Estatística**

   - 5.1. Estimativa
     - Pontual
     - Intervalar
   - 5.2. Testes de Hipótese
     - Hipóteses Nula e Alternativa
     - Erros Tipo I e II
     - Nível de Significância e Poder do Teste
   - 5.3. Testes Paramétricos e Não Paramétricos
     - Teste t de Student
     - Teste Qui-Quadrado
   - 5.4. Implementações em Python
     - Exemplos Práticos
   - 5.5. Exercícios

6. **Conclusão**

7. **Respostas dos Exercícios**

## **1. Introdução**

### **1.1. O que é Estatística e Probabilidade?**

- **Estatística** é a ciência que se dedica à coleta, organização, análise, interpretação e apresentação de dados. É fundamental na pesquisa quantitativa para entender padrões e tendências em conjuntos de dados.
- **Probabilidade** é um ramo da matemática que estuda eventos aleatórios e quantifica a chance de ocorrência desses eventos. É essencial para fazer inferências sobre populações a partir de amostras.

### **1.2. Importância na Pesquisa Quantitativa e Análise Exploratória de Dados**

- **Análise Exploratória de Dados (AED)**: A estatística descritiva e a visualização de dados são fundamentais para a AED, permitindo que pesquisadores identifiquem padrões, outliers e relacionamentos iniciais nos dados.
- **Pesquisa Quantitativa**: Estatística e probabilidade fornecem as ferramentas necessárias para testar hipóteses, estimar parâmetros populacionais e tomar decisões baseadas em dados.

## **2. Estatística Descritiva**

### **2.1. Medidas de Tendência Central**

#### **Média (\( \bar{x} \))**

A média aritmética é a soma de todos os valores dividida pelo número de observações. Representa o valor central dos dados.

#### **Mediana**

Valor que divide o conjunto de dados ordenados em duas partes iguais. É menos sensível a valores extremos (outliers) do que a média.

#### **Moda**

Valor que ocorre com maior frequência no conjunto de dados. Útil para dados categóricos e para identificar valores mais comuns.

### **2.2. Medidas de Dispersão**

#### **Variância (\( \sigma^2 \))**

Mede a dispersão dos dados em relação à média. Calculada como a média dos quadrados das diferenças entre cada valor e a média.

#### **Desvio Padrão (\( \sigma \))**

Raiz quadrada da variância. Indica o quão dispersos os dados estão em torno da média.

#### **Amplitude**

Diferença entre o valor máximo e o valor mínimo do conjunto de dados.

### **2.3. Visualização de Dados**

Visualizações gráficas são essenciais na análise exploratória para compreender a distribuição e identificar padrões nos dados.

#### **Histogramas**

Gráficos que mostram a distribuição de frequências dos dados em intervalos (bins).

#### **Boxplots**

Também conhecidos como gráficos de caixa, representam a mediana, quartis e possíveis outliers dos dados.

#### **Gráficos Interativos com Plotly**

Plotly é uma biblioteca Python para criação de gráficos interativos que permitem uma exploração mais dinâmica dos dados.

### **2.4. Implementações em Python**

**Exemplo Prático 1: Calculando Medidas Descritivas**

```python
import numpy as np
import pandas as pd

# Conjunto de dados
dados = [12, 15, 14, 10, 8, 12, 14, 16, 15, 14]

# Converter para um objeto Series do Pandas
serie = pd.Series(dados)

# Média
media = serie.mean()
print(f"Média: {media}")

# Mediana
mediana = serie.median()
print(f"Mediana: {mediana}")

# Moda
moda = serie.mode()
print(f"Moda: {moda.values}")

# Variância
variancia = serie.var()
print(f"Variância: {variancia}")

# Desvio Padrão
desvio_padrao = serie.std()
print(f"Desvio Padrão: {desvio_padrao}")

# Amplitude
amplitude = serie.max() - serie.min()
print(f"Amplitude: {amplitude}")
```

**Exemplo Prático 2: Visualização com Histogramas e Boxplots Interativos**

```python
import plotly.express as px

# Histograma Interativo
fig_hist = px.histogram(serie, nbins=5, title='Histograma dos Dados')
fig_hist.show()

# Boxplot Interativo
fig_box = px.box(serie, title='Boxplot dos Dados')
fig_box.show()
```

### **2.5. Exercícios**

1. **Calcule as medidas descritivas** para o conjunto de dados: [23, 20, 27, 25, 22, 24, 26, 28, 21, 23].

2. **Gere um histograma e um boxplot interativos** para um conjunto de dados aleatórios seguindo uma distribuição normal com média 50 e desvio padrão 5.

   ```python
   # Dica:
   import numpy as np
   dados = np.random.normal(50, 5, 100)
   ```

## **3. Probabilidade**

### **3.1. Conceitos Básicos**

#### **Experimento Aleatório**

Processo que resulta em um resultado imprevisível, mas possível de ser descrito.

#### **Espaço Amostral (\( S \))**

Conjunto de todos os resultados possíveis de um experimento aleatório.

#### **Evento**

Subconjunto do espaço amostral.

### **3.2. Axiomas de Kolmogorov**

1. **Não Negatividade**: Para qualquer evento \( A \), \( P(A) \geq 0 \).
2. **Normalização**: \( P(S) = 1 \), onde \( S \) é o espaço amostral.
3. **Aditividade**: Se \( A \) e \( B \) são eventos mutuamente exclusivos, então \( P(A \cup B) = P(A) + P(B) \).

**Propriedades Derivadas**

- \( P(\emptyset) = 0 \)
- \( P(A^c) = 1 - P(A) \), onde \( A^c \) é o complemento de \( A \).

### **3.3. Probabilidade Condicional e Independência**

#### **Probabilidade Condicional**

Probabilidade de um evento \( A \) dado que outro evento \( B \) ocorreu:

$$
P(A|B) = \frac{P(A \cap B)}{P(B)}, \quad P(B) > 0
$$

#### **Teorema da Multiplicação**

$$
P(A \cap B) = P(A|B) \cdot P(B)
$$

#### **Independência de Eventos**

Eventos \( A \) e \( B \) são independentes se:

$$
P(A \cap B) = P(A) \cdot P(B)
$$

### **3.4. Teorema de Bayes**

O Teorema de Bayes permite atualizar a probabilidade de um evento com base em novas evidências.

$$
P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}
$$

#### **Aplicações em Previsões Médicas**

**Exemplo do Teste de HIV**

Suponha que:

- A prevalência da infecção por HIV em uma determinada população é de 0,1% (\( P(HIV) = 0,001 \)).
- O teste utilizado tem:
  - Sensibilidade (verdadeiro positivo) de 99% (\( P(\text{Positivo}|HIV) = 0,99 \)).
  - Especificidade (verdadeiro negativo) de 99% (\( P(\text{Negativo}|Não\ HIV) = 0,99 \)).

**Pergunta:** Qual é a probabilidade de um indivíduo ter HIV dado que seu teste resultou positivo?

**Solução:**

1. **Probabilidades Conhecidas:**

   - \( P(HIV) = 0,001 \)
   - \( P(\text{Positivo}|HIV) = 0,99 \)
   - \( P(\text{Positivo}|Não\ HIV) = 1 - \text{Especificidade} = 1 - 0,99 = 0,01 \)

2. **Probabilidade Total de Teste Positivo:**

   $$
   P(\text{Positivo}) = P(\text{Positivo}|HIV) \cdot P(HIV) + P(\text{Positivo}|Não\ HIV) \cdot P(Não\ HIV)
   $$

   $$
   P(\text{Positivo}) = (0,99)(0,001) + (0,01)(0,999) = 0,00099 + 0,00999 = 0,01098
   $$

3. **Aplicando o Teorema de Bayes:**

   $$
   P(HIV|\text{Positivo}) = \frac{P(\text{Positivo}|HIV) \cdot P(HIV)}{P(\text{Positivo})}
   $$

   $$
   P(HIV|\text{Positivo}) = \frac{0,99 \times 0,001}{0,01098} \approx 0,090
   $$

**Resposta:** Aproximadamente 9% de chance de ter HIV dado que o teste é positivo.

#### **Outros Exemplos Práticos**

**Exemplo: Diagnóstico de Doenças Raras**

Em doenças raras, mesmo testes altamente sensíveis e específicos podem resultar em um alto número de falsos positivos, demonstrando a importância do Teorema de Bayes na interpretação de resultados médicos.

### **3.5. Implementações em Python**

**Exemplo Prático 1: Teorema de Bayes aplicado ao Teste de HIV**

```python
# Dados do problema
P_HIV = 0.001  # Prevalência da doença
P_Pos_HIV = 0.99  # Sensibilidade
P_Pos_NaoHIV = 0.01  # 1 - Especificidade

# Probabilidade total de teste positivo
P_Pos = (P_Pos_HIV * P_HIV) + (P_Pos_NaoHIV * (1 - P_HIV))

# Aplicando Teorema de Bayes
P_HIV_Pos = (P_Pos_HIV * P_HIV) / P_Pos

print(f"Probabilidade de ter HIV dado que o teste é positivo: {P_HIV_Pos:.4f}")
```

**Exemplo Prático 2: Visualização Interativa com Plotly**

Podemos visualizar como a prevalência da doença afeta a probabilidade pós-teste.

```python
import numpy as np
import plotly.graph_objects as go

# Variando a prevalência de 0% a 1%
prevalencia = np.linspace(0.0001, 0.01, 100)
P_Pos_HIV = 0.99
P_Pos_NaoHIV = 0.01

P_HIV = prevalencia
P_Pos = (P_Pos_HIV * P_HIV) + (P_Pos_NaoHIV * (1 - P_HIV))
P_HIV_Pos = (P_Pos_HIV * P_HIV) / P_Pos

fig = go.Figure()
fig.add_trace(go.Scatter(x=prevalencia*100, y=P_HIV_Pos*100, mode='lines', name='P(HIV|Positivo)'))
fig.update_layout(title='Probabilidade Pós-Teste vs Prevalência',
                  xaxis_title='Prevalência (%)',
                  yaxis_title='P(HIV|Positivo) (%)')
fig.show()
```

### **3.6. Exercícios**

1. **Simule o lançamento de dois dados** 10.000 vezes e calcule a probabilidade experimental da soma ser igual a 7. Utilize gráficos interativos para visualizar a distribuição das somas.

2. **Utilize o Teorema de Bayes** para resolver o seguinte problema:

   - Uma fábrica produz 60% de seus produtos na máquina A e 40% na máquina B.
   - A taxa de defeitos na máquina A é de 2%, e na máquina B é de 5%.
   - Se um produto é selecionado aleatoriamente e é defeituoso, qual a probabilidade de ter sido produzido na máquina B?

## **4. Distribuições Probabilísticas**

### **4.1. Variáveis Aleatórias Discretas**

#### **Distribuição Binomial**

Modela o número de sucessos em \( n \) ensaios de Bernoulli independentes.

- **Função de Probabilidade:**

  $$
  P(X = k) = \binom{n}{k} p^k (1 - p)^{n - k}
  $$

- **Média:** \( \mu = n p \)
- **Variância:** \( \sigma^2 = n p (1 - p) \)

**Exemplo em Python com Plotly:**

```python
from scipy.stats import binom
import plotly.express as px

n = 10  # Número de ensaios
p = 0.5  # Probabilidade de sucesso

# Valores possíveis de k
k = np.arange(0, n+1)
probabilidades = binom.pmf(k, n, p)

# Gráfico interativo
fig = px.bar(x=k, y=probabilidades, labels={'x':'Número de Sucessos', 'y':'Probabilidade'},
             title='Distribuição Binomial (n=10, p=0.5)')
fig.show()
```

#### **Distribuição de Poisson**

Modela o número de eventos que ocorrem em um intervalo fixo.

- **Função de Probabilidade:**

  $$
  P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}
  $$

- **Média e Variância:** \( \mu = \sigma^2 = \lambda \)

### **4.2. Variáveis Aleatórias Contínuas**

#### **Distribuição Normal (Gaussiana)**

Distribuição simétrica em torno da média.

- **Função Densidade de Probabilidade:**

  $$
  f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{ -\frac{1}{2} \left( \frac{x - \mu}{\sigma} \right)^2 }
  $$

**Exemplo em Python com Plotly:**

```python
from scipy.stats import norm
import numpy as np
import plotly.graph_objects as go

mu = 0  # Média
sigma = 1  # Desvio padrão

# Gerando dados
x = np.linspace(mu - 4*sigma, mu + 4*sigma, 1000)
y = norm.pdf(x, mu, sigma)

# Gráfico interativo
fig = go.Figure()
fig.add_trace(go.Scatter(x=x, y=y, mode='lines', name='f(x)'))
fig.update_layout(title='Distribuição Normal',
                  xaxis_title='x',
                  yaxis_title='f(x)')
fig.show()
```

### **4.3. Função Densidade de Probabilidade (PDF) e Função Distribuição Cumulativa (CDF)**

- **PDF**: Descreve a probabilidade de uma variável aleatória contínua assumir um valor específico.
- **CDF**: Probabilidade acumulada até um certo valor \( x \).

### **4.4. Implementações em Python**

**Exemplo Prático: Analisando a Distribuição Normal**

```python
# CDF
prob = norm.cdf(x, mu, sigma)

# Gráfico da CDF
fig = go.Figure()
fig.add_trace(go.Scatter(x=x, y=prob, mode='lines', name='F(x)'))
fig.update_layout(title='Função Distribuição Cumulativa (CDF)',
                  xaxis_title='x',
                  yaxis_title='F(x)')
fig.show()
```

### **4.5. Exercícios**

1. **Simule uma distribuição binomial** com \( n = 20 \) e \( p = 0,3 \). Plote o gráfico de probabilidades usando Plotly.

2. **Utilize a distribuição exponencial** para modelar o tempo entre falhas de um equipamento com taxa média de falhas \( \lambda = 0,5 \) por hora. Calcule a probabilidade de que o equipamento funcione por pelo menos 3 horas sem falhar. Visualize a função de sobrevivência.

## **5. Inferência Estatística**

### **5.1. Estimativa**

#### **Estimativa Pontual**

Estima um parâmetro populacional usando um único valor baseado na amostra.

#### **Estimativa Intervalar**

Fornece um intervalo que, com certa confiança, contém o parâmetro populacional.

### **5.2. Testes de Hipótese**

#### **Hipóteses Nula (\( H_0 \)) e Alternativa (\( H_1 \))**

- **\( H_0 \)**: Afirmação inicial que se assume verdadeira.
- **\( H_1 \)**: Afirmação que representa uma nova teoria ou efeito.

#### **Erros Tipo I e II**

- **Erro Tipo I (\( \alpha \))**: Rejeitar \( H_0 \) quando é verdadeira.
- **Erro Tipo II (\( \beta \))**: Não rejeitar \( H_0 \) quando é falsa.

### **5.3. Testes Paramétricos e Não Paramétricos**

#### **Teste t de Student**

Usado para comparar médias quando a variância populacional é desconhecida.

**Exemplo em Python:**

```python
from scipy import stats

# Dados de uma amostra
amostra = [14, 15, 16, 14, 15, 16, 14]

# Teste t para média populacional igual a 15
t_stat, p_value = stats.ttest_1samp(amostra, 15)
print(f"Estatística t: {t_stat:.4f}")
print(f"Valor-p: {p_value:.4f}")
```

### **5.4. Implementações em Python**

**Exemplo Prático: Intervalo de Confiança Interativo**

```python
import plotly.graph_objects as go

# Dados
dados = [12, 15, 14, 16, 15, 14, 13, 15, 14, 16]
media = np.mean(dados)
s = np.std(dados, ddof=1)
n = len(dados)
alpha = 0.05
t_critico = stats.t.ppf(1 - alpha/2, df=n-1)
margem_erro = t_critico * (s / np.sqrt(n))
lim_inferior = media - margem_erro
lim_superior = media + margem_erro

# Gráfico interativo
fig = go.Figure()
fig.add_trace(go.Scatter(x=dados, y=[0]*len(dados), mode='markers', name='Dados'))
fig.add_shape(type="line", x0=lim_inferior, y0=-0.1, x1=lim_inferior, y1=0.1, line=dict(color="Red"))
fig.add_shape(type="line", x0=lim_superior, y0=-0.1, x1=lim_superior, y1=0.1, line=dict(color="Red"))
fig.update_layout(title='Intervalo de Confiança para a Média',
                  xaxis_title='Valores',
                  yaxis_visible=False)
fig.show()
```

### **5.5. Exercícios**

1. **Realize um teste t de Student** para verificar se a média de um conjunto de dados é significativamente diferente de um valor hipotético. Utilize um nível de significância de 5%.

2. **Construa um intervalo de confiança** de 99% para a média de uma amostra com os dados: [22, 24, 20, 23, 25, 24, 26, 27, 23, 22].

## **6. Conclusão**

Neste material, abordamos os fundamentos da estatística e probabilidade aplicados à pesquisa quantitativa e análise exploratória de dados. Utilizamos implementações práticas em Python, incluindo gráficos interativos com Plotly, para ilustrar os conceitos e facilitar a compreensão. A inclusão de exemplos relevantes, como o Teorema de Bayes aplicado a testes médicos, reforça a importância desses conceitos na interpretação de resultados e na tomada de decisões baseadas em dados.

## **7. Respostas dos Exercícios**

### **Exercícios da Seção 2**

**Exercício 1:**

Calculando as medidas descritivas para o conjunto de dados: [23, 20, 27, 25, 22, 24, 26, 28, 21, 23].

```python
dados = [23, 20, 27, 25, 22, 24, 26, 28, 21, 23]
serie = pd.Series(dados)

# Média
media = serie.mean()
print(f"Média: {media}")  # Média: 23.9

# Mediana
mediana = serie.median()
print(f"Mediana: {mediana}")  # Mediana: 23.5

# Moda
moda = serie.mode()
print(f"Moda: {moda.values}")  # Moda: [23]

# Variância
variancia = serie.var()
print(f"Variância: {variancia}")  # Variância: 6.766666666666667

# Desvio Padrão
desvio_padrao = serie.std()
print(f"Desvio Padrão: {desvio_padrao}")  # Desvio Padrão: 2.6

# Amplitude
amplitude = serie.max() - serie.min()
print(f"Amplitude: {amplitude}")  # Amplitude: 8
```

**Exercício 2:**

Gerando histograma e boxplot interativos:

```python
import numpy as np
import plotly.express as px

dados = np.random.normal(50, 5, 100)

# Histograma
fig_hist = px.histogram(dados, nbins=10, title='Histograma de Dados Normais')
fig_hist.show()

# Boxplot
fig_box = px.box(dados, title='Boxplot de Dados Normais')
fig_box.show()
```

### **Exercícios da Seção 3**

**Exercício 1:**

Simulando o lançamento de dois dados:

```python
import numpy as np
import plotly.express as px

# Simulação
lancamentos1 = np.random.randint(1, 7, 10000)
lancamentos2 = np.random.randint(1, 7, 10000)
somas = lancamentos1 + lancamentos2

# Probabilidade experimental de soma igual a 7
prob_soma_7 = np.sum(somas == 7) / 10000
print(f"Probabilidade experimental de soma igual a 7: {prob_soma_7}")

# Distribuição das somas
fig = px.histogram(somas, nbins=11, title='Distribuição das Som

as dos Dados')
fig.show()
```

**Exercício 2:**

Aplicando o Teorema de Bayes:

```python
# Probabilidades dadas
P_A = 0.6  # Produção da máquina A
P_B = 0.4  # Produção da máquina B
P_D_A = 0.02  # Defeito na máquina A
P_D_B = 0.05  # Defeito na máquina B

# Probabilidade total de defeito
P_D = (P_D_A * P_A) + (P_D_B * P_B)

# Probabilidade de ter sido produzido na máquina B dado que é defeituoso
P_B_D = (P_D_B * P_B) / P_D
print(f"Probabilidade de ter sido produzido na máquina B dado que é defeituoso: {P_B_D:.4f}")
```

### **Exercícios da Seção 4**

**Exercício 1:**

Simulando distribuição binomial:

```python
from scipy.stats import binom
import numpy as np
import plotly.express as px

n = 20
p = 0.3
k = np.arange(0, n+1)
probabilidades = binom.pmf(k, n, p)

fig = px.bar(x=k, y=probabilidades, labels={'x':'Número de Sucessos', 'y':'Probabilidade'},
             title='Distribuição Binomial (n=20, p=0.3)')
fig.show()
```

**Exercício 2:**

Calculando a probabilidade na distribuição exponencial:

```python
from scipy.stats import expon

lambda_param = 0.5  # Taxa média de falhas por hora
tempo = 3  # Horas

# Função de sobrevivência (probabilidade de não falhar até o tempo t)
prob_funcionamento = expon.sf(tempo, scale=1/lambda_param)
print(f"Probabilidade de funcionar por pelo menos 3 horas: {prob_funcionamento:.4f}")

# Visualização
import numpy as np
import plotly.graph_objects as go

t = np.linspace(0, 10, 1000)
survival = expon.sf(t, scale=1/lambda_param)

fig = go.Figure()
fig.add_trace(go.Scatter(x=t, y=survival, mode='lines', name='Função de Sobrevivência'))
fig.update_layout(title='Função de Sobrevivência do Equipamento',
                  xaxis_title='Tempo (horas)',
                  yaxis_title='Probabilidade de Funcionamento')
fig.show()
```

### **Exercícios da Seção 5**

**Exercício 1:**

Realizando teste t de Student:

```python
from scipy import stats
import numpy as np

dados = [18, 20, 22, 19, 21, 20, 23, 19, 18, 22]
media_hipotetica = 20
t_stat, p_value = stats.ttest_1samp(dados, media_hipotetica)
print(f"Estatística t: {t_stat:.4f}")
print(f"Valor-p: {p_value:.4f}")

# Decisão
alpha = 0.05
if p_value < alpha:
    print("Rejeita-se a hipótese nula.")
else:
    print("Não se rejeita a hipótese nula.")
```

**Exercício 2:**

Construindo intervalo de confiança:

```python
dados = [22, 24, 20, 23, 25, 24, 26, 27, 23, 22]
media = np.mean(dados)
s = np.std(dados, ddof=1)
n = len(dados)
alpha = 0.01  # 99% de confiança
t_critico = stats.t.ppf(1 - alpha/2, df=n-1)
margem_erro = t_critico * (s / np.sqrt(n))
lim_inferior = media - margem_erro
lim_superior = media + margem_erro

print(f"Intervalo de confiança de 99%: [{lim_inferior:.2f}, {lim_superior:.2f}]")
```

## **Referências**

- Montgomery, D. C., & Runger, G. C. **Estatística Aplicada e Probabilidade para Engenheiros**.
- Ross, S. M. **Introdução à Probabilidade e Estatística para Engenheiros e Cientistas**.
- Documentação do **NumPy**, **Pandas**, **Matplotlib**, **Plotly** e **SciPy**.
