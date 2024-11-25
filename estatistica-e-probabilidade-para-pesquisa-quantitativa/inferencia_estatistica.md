# **5. Inferência Estatística**

## **5.1. Estimativa**

### **Estimativa Pontual**

Estima um parâmetro populacional usando um único valor baseado na amostra.

### **Estimativa Intervalar**

Fornece um intervalo que, com certa confiança, contém o parâmetro populacional.

- **Intervalo de Confiança para a Média (variância desconhecida):**

  $$
  \bar{x} \pm t_{\alpha/2, \, n-1} \times \frac{s}{\sqrt{n}}
  $$

  Onde:
  - \( \bar{x} \) é a média amostral.
  - \( t_{\alpha/2, \, n-1} \) é o valor crítico da distribuição t de Student com \( n-1 \) graus de liberdade.
  - \( s \) é o desvio padrão amostral.
  - \( n \) é o tamanho da amostra.

## **5.2. Testes de Hipótese**

### **Hipóteses Nula (\( H_0 \)) e Alternativa (\( H_1 \))**

- **\( H_0 \)**: Afirmação inicial que se assume verdadeira (hipótese nula).
- **\( H_1 \)**: Afirmação que representa uma nova teoria ou efeito (hipótese alternativa).

Exemplo:

- \( H_0: \mu = \mu_0 \) (a média populacional é igual a um valor específico).
- \( H_1: \mu \neq \mu_0 \) (a média populacional é diferente desse valor).

### **Erros Tipo I e II**

- **Erro Tipo I (\( \alpha \))**: Rejeitar \( H_0 \) quando ela é verdadeira.
- **Erro Tipo II (\( \beta \))**: Não rejeitar \( H_0 \) quando ela é falsa.

### **Nível de Significância e Poder do Teste**

- **Nível de Significância (\( \alpha \))**: Probabilidade máxima permitida de cometer um erro Tipo I.
- **Poder do Teste**: Probabilidade de corretamente rejeitar \( H_0 \) quando ela é falsa (igual a \( 1 - \beta \)).

## **5.3. Testes Paramétricos e Não Paramétricos**

### **Teste t de Student**

Usado para comparar médias quando a variância populacional é desconhecida e o tamanho da amostra é pequeno.

**Estatística t:**

$$
t = \frac{\bar{x} - \mu_0}{s / \sqrt{n}}
$$

Onde:
- \( \bar{x} \) é a média amostral.
- \( \mu_0 \) é a média hipotética sob \( H_0 \).
- \( s \) é o desvio padrão amostral.
- \( n \) é o tamanho da amostra.

**Exemplo em JavaScript:**

Para realizar o teste t em JavaScript, podemos usar bibliotecas estatísticas como a **jStat**.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Teste t de Student</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jstat/1.9.4/jstat.min.js"></script>
</head>
<body>

<script>
  // Dados de uma amostra
  const amostra = [14, 15, 16, 14, 15, 16, 14];
  const mediaHipotetica = 15;

  const n = amostra.length;
  const mediaAmostral = jStat.mean(amostra);
  const desvioPadrao = jStat.stdev(amostra, true);

  // Estatística t
  const tEstatistica = (mediaAmostral - mediaHipotetica) / (desvioPadrao / Math.sqrt(n));

  // Valor-p
  const grausDeLiberdade = n - 1;
  const pValor = 2 * (1 - jStat.studentt.cdf(Math.abs(tEstatistica), grausDeLiberdade));

  console.log(`Estatística t: ${tEstatistica.toFixed(4)}`);
  console.log(`Valor-p: ${pValor.toFixed(4)}`);
</script>

</body>
</html>
```
### Teste Qui-Quadrado
Usado para testar a independência entre duas variáveis categóricas ou para verificar a adequação de uma distribuição.

## 5.4. Implementações em JavaScript

**Exemplo Prático: Intervalo de Confiança Interativo**

Vamos construir um intervalo de confiança para a média e visualizar os resultados usando Plotly.js.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Intervalo de Confiança</title>
  <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jstat/1.9.4/jstat.min.js"></script>
</head>
<body>

<h2>Intervalo de Confiança para a Média</h2>
<div id="grafico-ic"></div>

<script>
  const dados = [12, 15, 14, 16, 15, 14, 13, 15, 14, 16];
  const media = jStat.mean(dados);
  const desvioPadrao = jStat.stdev(dados, true);
  const n = dados.length;
  const alpha = 0.05; // Nível de significância de 5%
  const tCritico = jStat.studentt.inv(1 - alpha / 2, n - 1);
  const margemErro = tCritico * (desvioPadrao / Math.sqrt(n));
  const limInferior = media - margemErro;
  const limSuperior = media + margemErro;

  // Exibindo o intervalo de confiança
  console.log(`Intervalo de confiança: [${limInferior.toFixed(2)}, ${limSuperior.toFixed(2)}]`);

  // Gráfico interativo
  const traceDados = {
    x: dados,
    y: Array(dados.length).fill(0),
    mode: 'markers',
    marker: { size: 8 },
    name: 'Dados'
  };

  const layout = {
    xaxis: { title: 'Valores' },
    yaxis: { visible: false },
    shapes: [
      {
        type: 'line',
        x0: limInferior,
        y0: -0.1,
        x1: limInferior,
        y1: 0.1,
        line: { color: 'red', width: 2, dash: 'dashdot' },
        name: 'Limite Inferior'
      },
      {
        type: 'line',
        x0: limSuperior,
        y0: -0.1,
        x1: limSuperior,
        y1: 0.1,
        line: { color: 'red', width: 2, dash: 'dashdot' },
        name: 'Limite Superior'
      }
    ],
    title: 'Intervalo de Confiança para a Média'
  };

  Plotly.newPlot('grafico-ic', [traceDados], layout);
</script>

</body>
</html>
```
###Explicação do Código:

**Calculando a Média e o Desvio Padrão Amostral:**

Usamos jStat.mean(dados) para calcular a média amostral.
Usamos jStat.stdev(dados, true) para calcular o desvio padrão amostral.
Determinando o Valor Crítico t:

Usamos jStat.studentt.inv para encontrar o valor crítico da distribuição t com n - 1 graus de liberdade.
Calculando a Margem de Erro e os Limites do Intervalo de Confiança:

A margem de erro é calculada multiplicando o valor crítico t pelo erro padrão da média.
Visualizando com Plotly:

Plotamos os dados e adicionamos linhas verticais nos limites inferior e superior do intervalo de confiança.

## 5.5. Exercícios
Realize um teste t de Student para verificar se a média de um conjunto de dados é significativamente diferente de um valor hipotético. Utilize um nível de significância de 5%. Use os dados: [18, 20, 22, 19, 21, 20, 23, 19, 18, 22] e média hipotética de 20.

Construa um intervalo de confiança de 99% para a média de uma amostra com os dados: [22, 24, 20, 23, 25, 24, 26, 27, 23, 22]. Calcule a margem de erro e os limites do intervalo.
