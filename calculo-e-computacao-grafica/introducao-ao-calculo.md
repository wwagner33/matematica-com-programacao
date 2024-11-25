# **Cálculo Diferencial e Integral Aplicado à Computação Gráfica**

## **Índice**

1. **Introdução e Relevância**

   - 1.1. Por que Cálculo e Álgebra Linear são Essenciais na Computação Gráfica?
   - 1.2. Objetivos do Material

2. **Fundamentos de Álgebra Linear**

   - 2.1. Vetores e Operações Básicas
   - 2.2. Matrizes e Transformações
   - 2.3. Transformações Compostas
   - 2.4. Exemplos de Problemas Resolvidos
   - 2.5. Exercícios Práticos com Programação

3. **Funções e Gráficos**

   - 3.1. Representação de Funções na Computação Gráfica
   - 3.2. Interpolação Linear e Curvas de Bézier
   - 3.3. Exemplos de Problemas Resolvidos
   - 3.4. Exercícios Práticos com Programação

4. **Cálculo Diferencial**

   - 4.1. Conceitos Fundamentais de Derivadas
   - 4.2. Tabela de Derivadas Comuns
   - 4.3. Aplicações em Geometria e Computação Gráfica
   - 4.4. Gradiente e Cálculo Vetorial
   - 4.5. Exemplos de Problemas Resolvidos
   - 4.6. Exercícios Práticos com Programação

5. **Cálculo Integral**

   - 5.1. Conceitos Fundamentais de Integrais
   - 5.2. Tabela de Integrais Comuns
   - 5.3. Aplicações em Geometria e Computação Gráfica
   - 5.4. Gradiente e Divergente em Integrais
   - 5.5. Exemplos de Problemas Resolvidos
   - 5.6. Exercícios Práticos com Programação

6. **Programação de Computadores para Computação Gráfica**
   - 6.1. Estruturas e Lógica com JavaScript
   - 6.2. Bibliotecas e Ferramentas Úteis
   - 6.3. Exemplos de Problemas Resolvidos
   - 6.4. Exercícios Práticos com Programação

## **1. Introdução e Relevância**

### **1.1. Por que Cálculo e Álgebra Linear são Essenciais na Computação Gráfica?**

A computação gráfica é a área da computação que se preocupa com a geração, manipulação e representação de imagens e modelos visuais. Para criar gráficos realistas e simulações precisas, é fundamental entender os conceitos matemáticos subjacentes, principalmente o cálculo e a álgebra linear.

- **Transformações Geométricas**: Movimentos como translação, rotação e escala de objetos gráficos são realizados usando matrizes e vetores.
- **Modelagem de Superfícies e Curvas**: Funções matemáticas definem formas complexas e permitem a criação de modelos 3D detalhados.
- **Animação e Movimento**: O cálculo diferencial permite descrever e controlar o movimento de objetos ao longo do tempo.
- **Iluminação e Sombreamento**: O cálculo vetorial é usado para determinar como a luz interage com superfícies, afetando cor e brilho.
- **Simulações Físicas**: Integrais são usadas para calcular trajetórias e prever o comportamento de objetos sob forças variadas.

### **1.2. Objetivos do Material**

- **Compreender os Fundamentos Matemáticos**: Fornecer uma base sólida em cálculo e álgebra linear aplicados à computação gráfica.
- **Aplicar Conceitos Matemáticos em Programação**: Integrar teoria e prática através de exemplos e exercícios em JavaScript.
- **Desenvolver Habilidades de Resolução de Problemas**: Incentivar o aprendizado ativo por meio de problemas resolvidos e exercícios práticos.
- **Preparar para Aplicações Avançadas**: Estabelecer fundamentos para estudos avançados em gráficos 3D, simulações físicas e outras áreas relacionadas.

## **2. Fundamentos de Álgebra Linear**

### **2.1. Vetores e Operações Básicas**

**Definição de Vetor**

Um vetor é uma entidade que possui magnitude (tamanho) e direção. Em um espaço 2D ou 3D, vetores são usados para representar pontos, deslocamentos, velocidades e forças.

**Operações com Vetores**

- **Adição**:
  $$
  \vec{u} + \vec{v} = (u_x + v_x, u_y + v_y, u_z + v_z)
  $$
- **Subtração**:
  $$
  \vec{u} - \vec{v} = (u_x - v_x, u_y - v_y, u_z - v_z)
  $$
- **Multiplicação por Escalar**:
  $$
  k\vec{v} = (k v_x, k v_y, k v_z)
  $$
- **Produto Escalar**:
  $$
  \vec{u} \cdot \vec{v} = u_x v_x + u_y v_y + u_z v_z
  $$
- **Produto Vetorial** (em 3D):
  $$
  \vec{u} \times \vec{v} = (u_y v_z - u_z v_y, u_z v_x - u_x v_z, u_x v_y - u_y v_x)
  $$

**Exemplo em JavaScript**

```javascript
// Definição de um vetor em 3D
class Vector3D {
  constructor(x, y, z) {
    this.x = x;
    this.y = y;
    this.z = z;
  }

  // Adição de vetores
  add(v) {
    return new Vector3D(this.x + v.x, this.y + v.y, this.z + v.z);
  }

  // Subtração de vetores
  subtract(v) {
    return new Vector3D(this.x - v.x, this.y - v.y, this.z - v.z);
  }

  // Multiplicação por escalar
  multiply(scalar) {
    return new Vector3D(this.x * scalar, this.y * scalar, this.z * scalar);
  }

  // Produto escalar
  dot(v) {
    return this.x * v.x + this.y * v.y + this.z * v.z;
  }

  // Produto vetorial
  cross(v) {
    return new Vector3D(
      this.y * v.z - this.z * v.y,
      this.z * v.x - this.x * v.z,
      this.x * v.y - this.y * v.x
    );
  }

  // Comprimento do vetor (magnitude)
  magnitude() {
    return Math.sqrt(this.x ** 2 + this.y ** 2 + this.z ** 2);
  }

  // Normalização do vetor
  normalize() {
    let mag = this.magnitude();
    return new Vector3D(this.x / mag, this.y / mag, this.z / mag);
  }
}

// Exemplo de uso
let u = new Vector3D(1, 2, 3);
let v = new Vector3D(4, 5, 6);
let sum = u.add(v);
console.log("Soma:", sum);
```

### **2.2. Matrizes e Transformações**

**Matrizes em Transformações Geométricas**

Matrizes são estruturas matemáticas que representam transformações lineares. Em computação gráfica, usamos matrizes para transformar coordenadas de objetos.

**Matriz de Rotação em 2D**

Para rotacionar um ponto \( P(x, y) \) em torno da origem por um ângulo \( \theta \):

$$
R(\theta) = \begin{bmatrix}
\cos \theta & -\sin \theta \\
\sin \theta & \cos \theta \\
\end{bmatrix}
$$

**Matriz de Translação em Coordenadas Homogêneas**

Para representar translações, usamos coordenadas homogêneas:

$$
T(tx, ty) = \begin{bmatrix}
1 & 0 & tx \\
0 & 1 & ty \\
0 & 0 & 1 \\
\end{bmatrix}
$$

**Exemplo em JavaScript**

```javascript
// Multiplicação de matrizes 3x3
function multiplyMatrices(a, b) {
  let result = [];
  for (let i = 0; i < 3; i++) {
    result[i] = [];
    for (let j = 0; j < 3; j++) {
      result[i][j] = a[i][0] * b[0][j] + a[i][1] * b[1][j] + a[i][2] * b[2][j];
    }
  }
  return result;
}

// Ponto em coordenadas homogêneas
let point = [1, 1, 1];

// Matriz de translação
let tx = 2,
  ty = 3;
let translationMatrix = [
  [1, 0, tx],
  [0, 1, ty],
  [0, 0, 1],
];

// Matriz de rotação
let theta = Math.PI / 4;
let rotationMatrix = [
  [Math.cos(theta), -Math.sin(theta), 0],
  [Math.sin(theta), Math.cos(theta), 0],
  [0, 0, 1],
];

// Transformação composta
let transformMatrix = multiplyMatrices(translationMatrix, rotationMatrix);

// Aplicando a transformação ao ponto
function applyTransformation(matrix, point) {
  let result = [];
  for (let i = 0; i < 3; i++) {
    result[i] =
      matrix[i][0] * point[0] +
      matrix[i][1] * point[1] +
      matrix[i][2] * point[2];
  }
  return result;
}

let transformedPoint = applyTransformation(transformMatrix, point);
console.log("Ponto transformado:", transformedPoint);
```

### **2.3. Transformações Compostas**

Transformações podem ser combinadas multiplicando suas matrizes correspondentes. A ordem das multiplicações é crucial, pois as transformações não são necessariamente comutativas.

**Exemplo de Transformação Composta**

Aplicar escala, seguida de rotação e depois translação:

$$
M_{\text{total}} = T \cdot R \cdot S
$$

Onde:

- \( S \) é a matriz de escala.
- \( R \) é a matriz de rotação.
- \( T \) é a matriz de translação.

### **2.4. Exemplos de Problemas Resolvidos**

**Exemplo 1: Rotacionar e Transladar um Triângulo**

**Problema:** Dado um triângulo com vértices em \( P_0(0, 0) \), \( P_1(1, 0) \), \( P_2(0, 1) \), aplique uma rotação de \( 45^\circ \) seguida de uma translação de \( (2, 3) \).

**Solução em JavaScript:**

```javascript
// Definição dos pontos
let P0 = [0, 0, 1];
let P1 = [1, 0, 1];
let P2 = [0, 1, 1];

// Matriz de rotação
let theta = Math.PI / 4;
let rotationMatrix = [
  [Math.cos(theta), -Math.sin(theta), 0],
  [Math.sin(theta), Math.cos(theta), 0],
  [0, 0, 1],
];

// Matriz de translação
let tx = 2,
  ty = 3;
let translationMatrix = [
  [1, 0, tx],
  [0, 1, ty],
  [0, 0, 1],
];

// Transformação composta
let transformMatrix = multiplyMatrices(translationMatrix, rotationMatrix);

// Aplicando a transformação aos pontos
let newP0 = applyTransformation(transformMatrix, P0);
let newP1 = applyTransformation(transformMatrix, P1);
let newP2 = applyTransformation(transformMatrix, P2);

console.log("Novos vértices do triângulo:");
console.log("P0:", newP0);
console.log("P1:", newP1);
console.log("P2:", newP2);
```

**Exemplo 2: Animação de um Objeto em Movimento Circular**

**Problema:** Crie uma animação onde um objeto se move ao longo de uma circunferência de raio \( r = 100 \) pixels.

**Solução com p5.js:**

```javascript
let angle = 0;
function setup() {
  createCanvas(400, 400);
}
function draw() {
  background(220);
  translate(width / 2, height / 2);
  let x = 100 * cos(angle);
  let y = 100 * sin(angle);
  fill(0);
  ellipse(x, y, 20, 20);
  angle += 0.02;
}
```

### **2.5. Exercícios Práticos com Programação**

**Exercício 1: Implementar uma Classe Matrix2D**

**Problema:** Crie uma classe `Matrix2D` que suporte operações básicas como multiplicação de matrizes, aplicação a vetores e cálculo da matriz inversa.

**Resposta:**

```javascript
class Matrix2D {
  constructor(a, b, c, d, tx, ty) {
    this.a = a; // [a  c  tx]
    this.b = b; // [b  d  ty]
    this.c = c; // [0  0   1]
    this.d = d;
    this.tx = tx;
    this.ty = ty;
  }

  // Multiplicação de matrizes
  multiply(matrix) {
    let a = this.a * matrix.a + this.c * matrix.b;
    let b = this.b * matrix.a + this.d * matrix.b;
    let c = this.a * matrix.c + this.c * matrix.d;
    let d = this.b * matrix.c + this.d * matrix.d;
    let tx = this.a * matrix.tx + this.c * matrix.ty + this.tx;
    let ty = this.b * matrix.tx + this.d * matrix.ty + this.ty;
    return new Matrix2D(a, b, c, d, tx, ty);
  }

  // Aplicar transformação a um ponto
  applyToPoint(x, y) {
    let xNew = this.a * x + this.c * y + this.tx;
    let yNew = this.b * x + this.d * y + this.ty;
    return { x: xNew, y: yNew };
  }

  // Outros métodos podem ser adicionados conforme necessário
}
```

**Exercício 2: Simular Transformações de Escala e Rotação**

**Problema:** Use a classe `Matrix2D` para aplicar uma escala de \( 2 \times \) e uma rotação de \( 30^\circ \) a um conjunto de pontos que formam um quadrado.

**Resposta:**

```javascript
// Definição dos pontos do quadrado
let squarePoints = [
  { x: -1, y: -1 },
  { x: 1, y: -1 },
  { x: 1, y: 1 },
  { x: -1, y: 1 },
];

// Matriz de escala
let scaleMatrix = new Matrix2D(2, 0, 0, 2, 0, 0);

// Matriz de rotação
let theta = (30 * Math.PI) / 180;
let rotationMatrix = new Matrix2D(
  Math.cos(theta),
  Math.sin(theta),
  -Math.sin(theta),
  Math.cos(theta),
  0,
  0
);

// Transformação composta
let transformMatrix = rotationMatrix.multiply(scaleMatrix);

// Aplicar transformação aos pontos
let transformedPoints = squarePoints.map((point) =>
  transformMatrix.applyToPoint(point.x, point.y)
);

console.log("Pontos transformados:", transformedPoints);
```

## **3. Funções e Gráficos**

### **3.1. Representação de Funções na Computação Gráfica**

**Funções Paramétricas**

Funções paramétricas são usadas para descrever curvas e trajetórias, onde as coordenadas \( x \) e \( y \) dependem de um parâmetro comum \( t \).

**Exemplo: Círculo**

$$
\begin{cases}
x(t) = r \cos(t) \\
y(t) = r \sin(t)
\end{cases}, \quad t \in [0, 2\pi]
$$

**Exemplo em JavaScript com p5.js**

```javascript
function setup() {
  createCanvas(400, 400);
}
function draw() {
  background(220);
  translate(width / 2, height / 2);
  beginShape();
  for (let t = 0; t <= TWO_PI; t += 0.01) {
    let x = 100 * cos(t);
    let y = 100 * sin(t);
    vertex(x, y);
  }
  endShape(CLOSE);
}
```

### **3.2. Interpolação Linear e Curvas de Bézier**

**Interpolação Linear**

Interpolação linear é usada para calcular pontos intermediários entre dois pontos:

$$
P(t) = (1 - t) P_0 + t P_1, \quad t \in [0, 1]
$$

**Curvas de Bézier**

Curvas de Bézier são usadas para modelar curvas suaves com um conjunto de pontos de controle.

- **Curva de Bézier Quadrática**:

$$
B(t) = (1 - t)^2 P_0 + 2(1 - t) t P_1 + t^2 P_2
$$

- **Curva de Bézier Cúbica**:

$$
B(t) = (1 - t)^3 P_0 + 3(1 - t)^2 t P_1 + 3(1 - t) t^2 P_2 + t^3 P_3
$$

**Exemplo em JavaScript: Desenhando uma Curva de Bézier Cúbica**

```javascript
function setup() {
  createCanvas(400, 400);
}
function draw() {
  background(220);
  noFill();

  let P0 = createVector(50, 300);
  let P1 = createVector(150, 50);
  let P2 = createVector(250, 350);
  let P3 = createVector(350, 100);

  // Desenha a curva de Bézier
  stroke(0);
  beginShape();
  for (let t = 0; t <= 1; t += 0.01) {
    let x =
      Math.pow(1 - t, 3) * P0.x +
      3 * Math.pow(1 - t, 2) * t * P1.x +
      3 * (1 - t) * Math.pow(t, 2) * P2.x +
      Math.pow(t, 3) * P3.x;
    let y =
      Math.pow(1 - t, 3) * P0.y +
      3 * Math.pow(1 - t, 2) * t * P1.y +
      3 * (1 - t) * Math.pow(t, 2) * P2.y +
      Math.pow(t, 3) * P3.y;
    vertex(x, y);
  }
  endShape();

  // Desenha os pontos de controle
  stroke(255, 0, 0);
  strokeWeight(8);
  point(P0.x, P0.y);
  point(P1.x, P1.y);
  point(P2.x, P2.y);
  point(P3.x, P3.y);
}
```

### **3.3. Exemplos de Problemas Resolvidos**

**Exemplo 1: Desenhar uma Espiral Logarítmica**

A espiral logarítmica pode ser definida por:

$$
\begin{cases}
x(t) = e^{a t} \cos(t) \\
y(t) = e^{a t} \sin(t)
\end{cases}
$$

**Solução em JavaScript:**

```javascript
function setup() {
  createCanvas(400, 400);
}
function draw() {
  background(220);
  translate(width / 2, height / 2);
  beginShape();
  for (let t = 0; t <= 6 * PI; t += 0.01) {
    let a = 0.05;
    let r = exp(a * t);
    let x = r * cos(t);
    let y = r * sin(t);
    vertex(x, y);
  }
  endShape();
}
```

**Exemplo 2: Animação de um Objeto ao Longo de uma Curva de Bézier**

**Problema:** Mover um objeto ao longo de uma curva de Bézier quadrática.

**Solução:**

```javascript
let t = 0;
function setup() {
  createCanvas(400, 400);
}
function draw() {
  background(220);
  let P0 = createVector(50, 350);
  let P1 = createVector(200, 50);
  let P2 = createVector(350, 350);

  // Calcula a posição do objeto na curva
  let x = (1 - t) * (1 - t) * P0.x + 2 * (1 - t) * t * P1.x + t * t * P2.x;
  let y = (1 - t) * (1 - t) * P0.y + 2 * (1 - t) * t * P1.y + t * t * P2.y;

  // Desenha a curva
  noFill();
  stroke(0);
  beginShape();
  for (let s = 0; s <= 1; s += 0.01) {
    let xCurve =
      (1 - s) * (1 - s) * P0.x + 2 * (1 - s) * s * P1.x + s * s * P2.x;
    let yCurve =
      (1 - s) * (1 - s) * P0.y + 2 * (1 - s) * s * P1.y + s * s * P2.y;
    vertex(xCurve, yCurve);
  }
  endShape();

  // Desenha o objeto
  fill(255, 0, 0);
  ellipse(x, y, 20, 20);

  t += 0.005;
  if (t > 1) t = 0;
}
```

### **3.4. Exercícios Práticos com Programação**

**Exercício 1: Desenhar uma Rosácea**

**Problema:** Use funções paramétricas para desenhar uma rosácea definida por:

$$
\begin{cases}
x(t) = r \cos(k t) \cos(t) \\
y(t) = r \cos(k t) \sin(t)
\end{cases}
$$

Onde \( k \) é um inteiro positivo.

**Resposta:**

```javascript
function setup() {
  createCanvas(400, 400);
}
function draw() {
  background(220);
  translate(width / 2, height / 2);
  beginShape();
  let r = 150;
  let k = 5;
  for (let t = 0; t <= TWO_PI; t += 0.01) {
    let x = r * cos(k * t) * cos(t);
    let y = r * cos(k * t) * sin(t);
    vertex(x, y);
  }
  endShape(CLOSE);
}
```

**Exercício 2: Implementar Interpolação Linear para Animação**

**Problema:** Crie uma animação onde um objeto se move de \( P_0(50, 50) \) para \( P_1(350, 350) \) usando interpolação linear.

**Resposta:**

```javascript
let t = 0;
function setup() {
  createCanvas(400, 400);
}
function draw() {
  background(220);
  let P0 = createVector(50, 50);
  let P1 = createVector(350, 350);

  let x = (1 - t) * P0.x + t * P1.x;
  let y = (1 - t) * P0.y + t * P1.y;

  fill(0);
  ellipse(x, y, 20, 20);

  t += 0.01;
  if (t > 1) t = 0;
}
```

## **4. Cálculo Diferencial**

### **4.1. Conceitos Fundamentais de Derivadas**

A derivada de uma função mede a taxa de variação dessa função em relação a uma variável. Em computação gráfica, derivadas são usadas para calcular inclinações, velocidades e acelerações.

**Definição Formal da Derivada**

$$
f'(x) = \lim_{h \to 0} \frac{f(x + h) - f(x)}{h}
$$

### **4.2. Tabela de Derivadas Comuns**

| Função \( f(x) \) | Derivada \( f'(x) \) |
|--||
| \( c \) (constante) | \( 0 \) |
| \( x^n \) | \( n x^{n-1} \) |
| \( e^{ax} \) | \( a e^{ax} \) |
| \( \ln(x) \) | \( \frac{1}{x} \) |
| \( \sin(ax) \) | \( a \cos(ax) \) |
| \( \cos(ax) \) | \( -a \sin(ax) \) |
| \( \tan(ax) \) | \( a \sec^2(ax) \) |
| \( \arcsin(x) \) | \( \frac{1}{\sqrt{1 - x^2}} \) |
| \( \arccos(x) \) | \( -\frac{1}{\sqrt{1 - x^2}} \) |
| \( \arctan(x) \) | \( \frac{1}{1 + x^2} \) |

### **4.3. Aplicações em Geometria e Computação Gráfica**

**Cálculo de Tangentes e Normais**

- **Reta Tangente**: Representa a direção instantânea da curva em um ponto.
- **Reta Normal**: Perpendicular à tangente, usada para cálculos de iluminação.

**Exemplo:**

Para a curva \( y = x^2 \), a inclinação da tangente em \( x = x_0 \) é:

$$
f'(x_0) = 2x_0
$$

A equação da reta tangente é:

$$
y - f(x_0) = f'(x_0)(x - x_0)
$$

### **4.4. Gradiente e Cálculo Vetorial**

**Gradiente**

O gradiente de uma função escalar \( f(x, y, z) \) é o vetor que aponta na direção de maior aumento de \( f \):

$$
\nabla f = \left( \frac{\partial f}{\partial x}, \frac{\partial f}{\partial y}, \frac{\partial f}{\partial z} \right)
$$

**Aplicação em Computação Gráfica**

- **Cálculo de Normais**: O gradiente é usado para determinar as normais em superfícies implícitas, essencial para iluminação e sombreamento.

### **4.5. Exemplos de Problemas Resolvidos**

**Exemplo 1: Cálculo da Reta Tangente**

**Problema:** Encontre a equação da reta tangente à curva \( y = \ln(x) \) no ponto \( x = 1 \).

**Solução:**

1. Calcule \( f'(x) \):

$$
f'(x) = \frac{1}{x}
$$

2. Avalie em \( x = 1 \):

$$
f'(1) = 1
$$

3. A equação da reta tangente é:

$$
y - f(1) = f'(1)(x - 1) \\
y - 0 = 1 \cdot (x - 1) \\
y = x - 1
$$

**Exemplo 2: Cálculo do Gradiente**

**Problema:** Calcule o gradiente da função \( f(x, y) = x^2 + y^2 \) e avalie no ponto \( (3, 4) \).

**Solução:**

1. Calcule as derivadas parciais:

$$
\frac{\partial f}{\partial x} = 2x \\
\frac{\partial f}{\partial y} = 2y
$$

2. Avalie em \( (3, 4) \):

$$
\nabla f(3, 4) = (6, 8)
$$

### **4.6. Exercícios Práticos com Programação**

**Exercício 1: Visualizar a Derivada de uma Função**

**Problema:** Escreva um programa em JavaScript que plota a função \( f(x) = \sin(x) \) e sua derivada \( f'(x) = \cos(x) \) no mesmo gráfico.

**Resposta:**

```javascript
function setup() {
  createCanvas(400, 400);
}
function draw() {
  background(220);
  translate(0, height / 2);
  scale(1, -1);

  // Desenha f(x) = sin(x)
  stroke(0, 0, 255);
  noFill();
  beginShape();
  for (let x = 0; x < width; x++) {
    let xVal = map(x, 0, width, 0, TWO_PI * 2);
    let yVal = 100 * sin(xVal);
    vertex(x, yVal);
  }
  endShape();

  // Desenha f'(x) = cos(x)
  stroke(255, 0, 0);
  noFill();
  beginShape();
  for (let x = 0; x < width; x++) {
    let xVal = map(x, 0, width, 0, TWO_PI * 2);
    let yVal = 100 * cos(xVal);
    vertex(x, yVal);
  }
  endShape();
}
```

**Exercício 2: Animação com Velocidade e Aceleração Variáveis**

**Problema:** Crie uma animação onde um objeto se move ao longo do eixo \( x \) com posição \( s(t) = t^3 \). Calcule e exiba a velocidade e aceleração em tempo real.

**Resposta:**

```javascript
let t = 0;
function setup() {
  createCanvas(400, 200);
}
function draw() {
  background(220);
  let s = t * t * t;
  let v = 3 * t * t;
  let a = 6 * t;

  fill(0);
  ellipse(s % width, height / 2, 20, 20);

  fill(0);
  noStroke();
  text("Velocidade: " + v.toFixed(2), 10, 20);
  text("Aceleração: " + a.toFixed(2), 10, 40);

  t += 0.05;
}
```

## **5. Cálculo Integral**

### **5.1. Conceitos Fundamentais de Integrais**

A integral de uma função representa a área sob a curva dessa função em um intervalo específico. Em computação gráfica, integrais são usadas para calcular áreas, volumes e efeitos acumulados.

### **5.2. Tabela de Integrais Comuns**

| Função \( f(x) \) | Integral \( \int f(x) \, dx \) |
|--||
| \( c \) (constante) | \( c x + C \) |
| \( x^n \) | \( \frac{x^{n+1}}{n+1} + C \) (se \( n \neq -1 \)) |
| \( \frac{1}{x} \) | \( \ln|x| + C \) |
| \( e^{ax} \) | \( \frac{1}{a} e^{ax} + C \) |
| \( \sin(ax) \) | \( -\frac{1}{a} \cos(ax) + C \) |
| \( \cos(ax) \) | \( \frac{1}{a} \sin(ax) + C \) |
| \( \sec^2(ax) \) | \( \frac{1}{a} \tan(ax) + C \) |
| \( \frac{1}{\sqrt{1 - x^2}} \) | \( \arcsin(x) + C \) |
| \( \frac{1}{1 + x^2} \) | \( \arctan(x) + C \) |
| \( \sinh(ax) \) | \( \frac{1}{a} \cosh(ax) + C \) |
| \( \cosh(ax) \) | \( \frac{1}{a} \sinh(ax) + C \) |

### **5.3. Aplicações em Geometria e Computação Gráfica**

**Cálculo de Áreas e Volumes**

- **Área entre Curvas**: Usada para determinar a área de formas complexas.
- **Volumes de Sólidos**: Importante na modelagem 3D e renderização.

**Exemplo: Volume por Revolução**

Para encontrar o volume gerado pela rotação da curva \( y = f(x) \) em torno do eixo \( x \):

$$
V = \pi \int_{a}^{b} [f(x)]^2 dx
$$

### **5.4. Gradiente e Divergente em Integrais**

**Integrais de Linha e Superfície**

- **Integral de Linha**: Integra uma função ao longo de uma curva.
- **Integral de Superfície**: Integra uma função sobre uma superfície.

**Teorema de Green, Gauss e Stokes**: Relacionam integrais de diferentes dimensões, úteis em simulações físicas.

### **5.5. Exemplos de Problemas Resolvidos**

**Exemplo 1: Cálculo do Volume de um Cilindro**

**Problema:** Calcule o volume de um cilindro de raio \( r \) e altura \( h \).

**Solução:**

$$
V = \pi r^2 h
$$

**Exemplo 2: Comprimento de uma Curva**

**Problema:** Encontre o comprimento da curva \( y = \ln(\cosh(x)) \) de \( x = 0 \) a \( x = a \).

**Solução:**

1. Calcule \( \frac{dy}{dx} \):

$$
\frac{dy}{dx} = \tanh(x)
$$

2. Comprimento \( L \):

$$
L = \int_{0}^{a} \sqrt{1 + \tanh^2(x)} dx = \int_{0}^{a} \text{sech}(x)^{-1} dx
$$

3. Avalie a integral conforme necessário.

### **5.6. Exercícios Práticos com Programação**

**Exercício 1: Cálculo Numérico de Integrais**

**Problema:** Escreva uma função em JavaScript que utiliza o Método de Simpson para calcular \( \int\_{0}^{1} e^{-x^2} dx \).

**Resposta:**

```javascript
function simpsonRule(f, a, b, n) {
  if (n % 2 !== 0) n++; // n deve ser par
  let h = (b - a) / n;
  let sum = f(a) + f(b);
  for (let i = 1; i < n; i++) {
    let x = a + i * h;
    sum += (i % 2 === 0 ? 2 : 4) * f(x);
  }
  return (h / 3) * sum;
}

function f(x) {
  return Math.exp(-x * x);
}

let integral = simpsonRule(f, 0, 1, 100);
console.log("Valor aproximado da integral:", integral);
```

**Exercício 2: Animação Baseada em Integração**

**Problema:** Simule o movimento de um objeto sob aceleração variável \( a(t) = \sin(t) \), calculando sua velocidade e posição usando integração numérica.

**Resposta:**

```javascript
let t = 0;
let dt = 0.1;
let v = 0;
let s = 0;

function setup() {
  createCanvas(400, 200);
}
function draw() {
  background(220);

  let a = sin(t);
  v += a * dt; // Integração da aceleração para obter velocidade
  s += v * dt; // Integração da velocidade para obter posição

  fill(0);
  ellipse(s % width, height / 2, 20, 20);

  t += dt;
}
```

## **6. Programação de Computadores para Computação Gráfica**

### **6.1. Estruturas e Lógica com JavaScript**

**Objetos e Classes**

Organizar código em classes e objetos torna o desenvolvimento mais modular e reutilizável.

**Exemplo: Classe para Curvas de Bézier**

```javascript
class BezierCurve {
  constructor(points) {
    this.points = points; // Array de pontos de controle
  }

  getPoint(t) {
    // Implementação para curvas de grau arbitrário
    let n = this.points.length - 1;
    let point = createVector(0, 0);
    for (let i = 0; i <= n; i++) {
      let binomial = factorial(n) / (factorial(i) * factorial(n - i));
      let coefficient = binomial * Math.pow(1 - t, n - i) * Math.pow(t, i);
      point.x += coefficient * this.points[i].x;
      point.y += coefficient * this.points[i].y;
    }
    return point;
  }
}

function factorial(n) {
  return n ? n * factorial(n - 1) : 1;
}
```

### **6.2. Bibliotecas e Ferramentas Úteis**

- **math.js**: Biblioteca para operações matemáticas avançadas.
- **p5.js**: Biblioteca para gráficos 2D interativos.
- **three.js**: Biblioteca para renderização 3D.
- **Plotly.js**: Biblioteca para gráficos interativos.

### **6.3. Exemplos de Problemas Resolvidos**

**Exemplo 1: Simulação de Partículas**

**Problema:** Crie uma simulação simples onde partículas são afetadas por um campo de força central.

**Solução:**

```javascript
let particles = [];

function setup() {
  createCanvas(400, 400);
  // Cria partículas aleatórias
  for (let i = 0; i < 100; i++) {
    particles.push({
      position: createVector(random(width), random(height)),
      velocity: createVector(0, 0),
    });
  }
}

function draw() {
  background(220);
  let center = createVector(width / 2, height / 2);
  particles.forEach((p) => {
    let direction = p5.Vector.sub(center, p.position);
    let distance = direction.mag();
    direction.normalize();
    let force = direction.mult(1 / (distance * 0.1)); // Força inversamente proporcional à distância
    p.velocity.add(force);
    p.position.add(p.velocity);
    ellipse(p.position.x, p.position.y, 2, 2);
  });
}
```

### **6.4. Exercícios Práticos com Programação**

**Exercício 1: Implementar um Sistema de Partículas com Gravidade**

**Problema:** Estenda o exemplo anterior para incluir gravidade e colisão com as bordas da tela.

**Resposta:**

```javascript
let particles = [];

function setup() {
  createCanvas(400, 400);
  for (let i = 0; i < 50; i++) {
    particles.push({
      position: createVector(random(width), random(height)),
      velocity: createVector(random(-1, 1), random(-1, 1)),
      mass: random(1, 5),
    });
  }
}

function draw() {
  background(220);
  particles.forEach((p) => {
    // Gravidade
    p.velocity.y += 0.1 * p.mass;

    // Atualiza posição
    p.position.add(p.velocity);

    // Colisão com as bordas
    if (p.position.x < 0 || p.position.x > width) {
      p.velocity.x *= -1;
    }
    if (p.position.y > height) {
      p.position.y = height;
      p.velocity.y *= -0.9; // Perda de energia
    }

    ellipse(p.position.x, p.position.y, p.mass * 2, p.mass * 2);
  });
}
```

**Exercício 2: Renderização de Superfícies 3D com three.js**

**Problema:** Use a biblioteca three.js para renderizar uma superfície definida pela função \( z = \sin(x) \cos(y) \).

**Resposta:**

```javascript
// Este código deve ser executado em um ambiente que suporte three.js
// Configuração básica
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  1000
);

const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// Criação da superfície
const geometry = new THREE.PlaneGeometry(10, 10, 100, 100);
const material = new THREE.MeshPhongMaterial({
  color: 0x00ff00,
  wireframe: true,
});

const plane = new THREE.Mesh(geometry, material);

// Modifica os vértices para seguir a função z = sin(x) * cos(y)
geometry.vertices.forEach((vertex) => {
  vertex.z = Math.sin(vertex.x) * Math.cos(vertex.y);
});

scene.add(plane);

// Adiciona luz
const light = new THREE.DirectionalLight(0xffffff, 1);
light.position.set(0, 0, 10);
scene.add(light);

camera.position.z = 15;

function animate() {
  requestAnimationFrame(animate);
  plane.rotation.z += 0.01;
  renderer.render(scene, camera);
}
animate();
```

## **Conclusão**

Este material integra conceitos fundamentais de cálculo diferencial e integral com aplicações práticas em computação gráfica, usando programação em JavaScript. Ao explorar exemplos e exercícios, você desenvolveu habilidades que são essenciais para criar gráficos e animações avançadas.

## **Referências**

- Stewart, J. **Cálculo**. Cengage Learning.
- Press, W. H., et al. **Numerical Recipes**. Cambridge University Press.
- Eberly, D. **3D Game Engine Design**. CRC Press.
- Documentação das bibliotecas **p5.js**, **three.js**, **math.js**.
