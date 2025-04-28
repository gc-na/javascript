<!--
Meta Description: # CanvasGradient em JavaScript: Criando Gradientes para Gráficos em Canvas ## Sinopse O `CanvasGradient` é uma interface do HTML5 que permite a criaçã...
Meta Keywords: gradiente, canvas, ctx, const, addcolorstop
-->

# CanvasGradient em JavaScript: Criando Gradientes para Gráficos em Canvas

## Sinopse
O `CanvasGradient` é uma interface do HTML5 que permite a criação de gradientes em elementos `<canvas>` usando JavaScript. Ele é essencial para adicionar efeitos visuais sofisticados a gráficos e imagens renderizadas em canvas.

## Documentação
O `CanvasGradient` é utilizado para definir a cor de preenchimento ou a cor da borda de um caminho no contexto de um canvas. Existem dois tipos principais de gradientes:

1. **Gradiente Linear**: Um gradiente que se estende em uma linha reta entre dois ou mais pontos.
2. **Gradiente Radial**: Um gradiente que se irradia a partir de um ponto central para fora, em círculos concêntricos.

### Como Criar um Gradiente
Para criar um gradiente em um canvas, você deve seguir os seguintes passos:

1. Obtenha o contexto 2D do canvas.
2. Crie um objeto `CanvasGradient` usando os métodos `createLinearGradient()` ou `createRadialGradient()`.
3. Adicione cores ao gradiente usando o método `addColorStop()`.
4. Aplique o gradiente ao contexto do canvas.

### Sintaxe
```javascript
const ctx = canvas.getContext('2d'); // Obtém o contexto 2D
const gradient = ctx.createLinearGradient(x0, y0, x1, y1); // Para gradiente linear
// ou
const radialGradient = ctx.createRadialGradient(x0, y0, r0, x1, y1, r1); // Para gradiente radial

gradient.addColorStop(0, 'cor1'); // Adiciona a primeira cor
gradient.addColorStop(1, 'cor2'); // Adiciona a segunda cor

ctx.fillStyle = gradient; // Define o gradiente como estilo de preenchimento
ctx.fillRect(0, 0, width, height); // Desenha um retângulo preenchido com o gradiente
```

## Exemplos

### Exemplo 1: Gradiente Linear
```javascript
const canvas = document.getElementById('meuCanvas');
const ctx = canvas.getContext('2d');

const gradient = ctx.createLinearGradient(0, 0, 200, 0);
gradient.addColorStop(0, 'red');
gradient.addColorStop(1, 'blue');

ctx.fillStyle = gradient;
ctx.fillRect(10, 10, 180, 100);
```

### Exemplo 2: Gradiente Radial
```javascript
const canvas = document.getElementById('meuCanvas');
const ctx = canvas.getContext('2d');

const radialGradient = ctx.createRadialGradient(100, 75, 50, 100, 75, 100);
radialGradient.addColorStop(0, 'yellow');
radialGradient.addColorStop(1, 'green');

ctx.fillStyle = radialGradient;
ctx.fillRect(10, 10, 180, 100);
```

## Explicação
Ao trabalhar com `CanvasGradient`, é importante lembrar que:

- As coordenadas dos gradientes são relativas ao canvas. Um erro comum é não dimensionar corretamente as coordenadas, o que pode resultar em gradientes não visíveis ou inesperados.
- O método `addColorStop()` aceita valores entre `0.0` e `1.0`, onde `0.0` representa o início do gradiente e `1.0` representa o final. Usar valores fora desse intervalo pode levar a resultados indesejados.
- Gradientes podem afetar o desempenho, especialmente em animações, então utilize-os com sabedoria em aplicações que exigem alto desempenho.

## Resumo em Uma Linha
O `CanvasGradient` em JavaScript permite a criação de gradientes visuais em elementos canvas, melhorando a estética de gráficos e imagens renderizadas.