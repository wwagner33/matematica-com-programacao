# **3. Probabilidade**

## **3.1. Conceitos Básicos**

### **Experimento Aleatório**

Processo que resulta em um resultado imprevisível, mas possível de ser descrito.

### **Espaço Amostral (\( S \))**

Conjunto de todos os resultados possíveis de um experimento aleatório.

### **Evento**

Subconjunto do espaço amostral.

## **3.2. Axiomas de Kolmogorov**

1. **Não Negatividade**: Para qualquer evento \( A \), \( P(A) \geq 0 \).
2. **Normalização**: \( P(S) = 1 \), onde \( S \) é o espaço amostral.
3. **Aditividade**: Se \( A \) e \( B \) são eventos mutuamente exclusivos, então \( P(A \cup B) = P(A) + P(B) \).

**Propriedades Derivadas**

- \( P(\emptyset) = 0 \)
- \( P(A^c) = 1 - P(A) \), onde \( A^c \) é o complemento de \( A \).

## **3.3. Probabilidade Condicional e Independência**

### **Probabilidade Condicional**

Probabilidade de um evento \( A \) dado que outro evento \( B \) ocorreu:

$$
P(A|B) = \frac{P(A \cap B)}{P(B)}, \quad P(B) > 0
$$

### **Teorema da Multiplicação**

$$
P(A \cap B) = P(A|B) \cdot P(B)
$$

### **Independência de Eventos**

Eventos \( A \) e \( B \) são independentes se:

$$
P(A \cap B) = P(A) \cdot P(B)
$$

## **3.4. Teorema de Bayes**

O Teorema de Bayes permite atualizar a probabilidade de um evento com base em novas evidências.

$$
P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}
$$

### **Aplicações em Previsões Médicas (Exemplo do Teste de HIV)**

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

### **Outros Exemplos Práticos**

**Exemplo: Diagnóstico de Doenças Raras**

Em doenças raras, mesmo testes altamente sensíveis e específicos podem resultar em um alto número de falsos positivos, demonstrando a importância do Teorema de Bayes na interpretação de resultados médicos.

## **3.5. Implementações em JavaScript**

**Exemplo Prático 1: Teorema de Bayes aplicado ao Teste de HIV**

```javascript
// Dados do problema
const P_HIV = 0.001; // Prevalência da doença
const P_Pos_HIV = 0.99; // Sensibilidade
const P_Pos_NaoHIV = 0.01; // 1 - Especificidade

// Probabilidade total de teste positivo
const P_Pos = P_Pos_HIV * P_HIV + P_Pos_NaoHIV * (1 - P_HIV);

// Aplicando Teorema de Bayes
const P_HIV_Pos = (P_Pos_HIV * P_HIV) / P_Pos;

console.log(
  `Probabilidade de ter HIV dado que o teste é positivo: ${P_HIV_Pos.toFixed(
    4
  )}`
);
```

### Exemplo Prático 2: Visualização Interativa com Plotly

Podemos visualizar como a prevalência da doença afeta a probabilidade pós-teste.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Teorema de Bayes - Visualização</title>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
  </head>
  <body>
    <h2>Probabilidade Pós-Teste vs Prevalência</h2>
    <div id="grafico"></div>

    <script>
      const prevalencia = [];
      const P_HIV_Pos = [];
      const P_Pos_HIV = 0.99;
      const P_Pos_NaoHIV = 0.01;

      for (let i = 0.0001; i <= 0.01; i += 0.0001) {
        prevalencia.push(i * 100); // Em porcentagem
        const P_HIV = i;
        const P_Pos = P_Pos_HIV * P_HIV + P_Pos_NaoHIV * (1 - P_HIV);
        const probPosTeste = (P_Pos_HIV * P_HIV) / P_Pos;
        P_HIV_Pos.push(probPosTeste * 100); // Em porcentagem
      }

      const trace = {
        x: prevalencia,
        y: P_HIV_Pos,
        mode: "lines",
        name: "P(HIV|Positivo)",
      };

      const layout = {
        title: "Probabilidade Pós-Teste vs Prevalência",
        xaxis: { title: "Prevalência (%)" },
        yaxis: { title: "P(HIV|Positivo) (%)" },
      };

      Plotly.newPlot("grafico", [trace], layout);
    </script>
  </body>
</html>
```

### 3.6. Exercícios

1. Simule o lançamento de dois dados 10.000 vezes e calcule a probabilidade experimental da soma ser igual a 7. Utilize gráficos interativos para visualizar a distribuição das somas.
2. Utilize o Teorema de Bayes para resolver o seguinte problema:
3. Uma fábrica produz 60% de seus produtos na máquina A e 40% na máquina B. A taxa de defeitos na máquina A é de 2%, e na máquina B é de 5%. Se um produto é selecionado aleatoriamente e é defeituoso, qual a probabilidade de ter sido produzido na máquina B?

[Voltar ao Índice Principal](indice.md)
