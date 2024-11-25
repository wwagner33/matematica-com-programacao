# **2. Estatística Descritiva**

## **2.1. Medidas de Tendência Central**

### **Média (\( \bar{x} \))**

A média aritmética é a soma de todos os valores dividida pelo número de observações. Representa o valor central dos dados.

### **Mediana**

Valor que divide o conjunto de dados ordenados em duas partes iguais. É menos sensível a valores extremos (outliers) do que a média.

### **Moda**

Valor que ocorre com maior frequência no conjunto de dados. Útil para dados categóricos e para identificar valores mais comuns.

## **2.2. Medidas de Dispersão**

### **Variância (\( \sigma^2 \))**

Mede a dispersão dos dados em relação à média. Calculada como a média dos quadrados das diferenças entre cada valor e a média.

### **Desvio Padrão (\( \sigma \))**

Raiz quadrada da variância. Indica o quão dispersos os dados estão em torno da média.

### **Amplitude**

Diferença entre o valor máximo e o valor mínimo do conjunto de dados.

## **2.3. Visualização de Dados**

Visualizações gráficas são essenciais na análise exploratória para compreender a distribuição e identificar padrões nos dados.

### **Histogramas**

Gráficos que mostram a distribuição de frequências dos dados em intervalos (bins).

### **Boxplots**

Também conhecidos como gráficos de caixa, representam a mediana, quartis e possíveis outliers dos dados.

### **Gráficos Interativos com Plotly**

Plotly é uma biblioteca JavaScript para criação de gráficos interativos que permitem uma exploração mais dinâmica dos dados.

## **2.4. Implementações em JavaScript**

**Exemplo Prático 1: Calculando Medidas Descritivas**

```javascript
// Conjunto de dados
const dados = [12, 15, 14, 10, 8, 12, 14, 16, 15, 14];

// Média
const media = dados.reduce((a, b) => a + b, 0) / dados.length;
console.log(`Média: ${media}`);

// Mediana
const dadosOrdenados = dados.slice().sort((a, b) => a - b);
const meio = Math.floor(dadosOrdenados.length / 2);
const mediana = dadosOrdenados.length % 2 !== 0
  ? dadosOrdenados[meio]
  : (dadosOrdenados[meio - 1] + dadosOrdenados[meio]) / 2;
console.log(`Mediana: ${mediana}`);

// Moda
const frequencia = {};
dados.forEach(valor => {
  frequencia[valor] = (frequencia[valor] || 0) + 1;
});
const maxFrequencia = Math.max(...Object.values(frequencia));
const moda = Object.keys(frequencia).filter(
  valor => frequencia[valor] === maxFrequencia
);
console.log(`Moda: ${moda}`);

// Variância
const variancia =
  dados.reduce((a, b) => a + Math.pow(b - media, 2), 0) / dados.length;
console.log(`Variância: ${variancia}`);

// Desvio Padrão
const desvioPadrao = Math.sqrt(variancia);
console.log(`Desvio Padrão: ${desvioPadrao}`);

// Amplitude
const amplitude = Math.max(...dados) - Math.min(...dados);
console.log(`Amplitude: ${amplitude}`);
```

### Exemplo Prático 2: Visualização com Histogramas e Boxplots Interativos

Para gráficos interativos em JavaScript, podemos usar o Plotly.js.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Visualização de Dados</title>
  <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
</head>
<body>

<h2>Histograma dos Dados</h2>
<div id="histograma"></div>

<h2>Boxplot dos Dados</h2>
<div id="boxplot"></div>

<script>
  const dados = [12, 15, 14, 10, 8, 12, 14, 16, 15, 14];

  // Histograma
  const traceHist = {
    x: dados,
    type: 'histogram',
    nbinsx: 5
  };
  Plotly.newPlot('histograma', [traceHist]);

  // Boxplot
  const traceBox = {
    y: dados,
    type: 'box'
  };
  Plotly.newPlot('boxplot', [traceBox]);
</script>

</body>
</html>
```

### 2.5. Exercícios
Calcule as medidas descritivas para o conjunto de dados: [23, 20, 27, 25, 22, 24, 26, 28, 21, 23].

Gere um histograma e um boxplot interativos para um conjunto de dados aleatórios seguindo uma distribuição normal com média 50 e desvio padrão 5.

```javascript
// Dica:
function gerarDadosNormais(n, media, desvioPadrao) {
  const dados = [];
  for (let i = 0; i < n; i++) {
    let u = 0, v = 0;
    while (u === 0) u = Math.random(); // Converte [0,1) para (0,1)
    while (v === 0) v = Math.random();
    let num = Math.sqrt(-2.0 * Math.log(u)) * Math.cos(2.0 * Math.PI * v);
    dados.push(num * desvioPadrao + media);
  }
  return dados;
}

const dados = gerarDadosNormais(100, 50, 5);
```

[Voltar ao Índice Principal](indice.md)