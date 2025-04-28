<!--
Meta Description: # WebGLProgram: Uma Introdução ao Uso de Programas WebGL em JavaScript ## Sinopse O WebGLProgram é uma interface fundamental na API WebGL que represen...
Meta Keywords: programa, shaders, const, que, webglprogram
-->

# WebGLProgram: Uma Introdução ao Uso de Programas WebGL em JavaScript

## Sinopse
O WebGLProgram é uma interface fundamental na API WebGL que representa um programa de sombreamento que pode ser executado na GPU. Ele é criado a partir de shaders compilados e é essencial para a renderização de gráficos 3D em aplicações web.

## Documentação
O `WebGLProgram` é um objeto que combina um ou mais shaders (vertex shaders e fragment shaders) em um único programa que pode ser utilizado para renderizar gráficos. Quando um programa WebGL é criado, os shaders são compilados e ligados (linked) em um único objeto `WebGLProgram`, que pode ser usado para desenhar objetos 3D na tela.

### Propósito
O propósito principal do WebGLProgram é permitir a execução de código de sombreamento na GPU, permitindo que os desenvolvedores criem gráficos complexos de forma eficiente.

### Uso
Para utilizar um `WebGLProgram`, siga estas etapas:
1. Crie um contexto WebGL a partir de um elemento `<canvas>`.
2. Compile os shaders (vertex e fragment).
3. Crie o programa WebGL e ligue os shaders a ele.
4. Use o programa ao desenhar objetos.

### Detalhes
- Os shaders são escritos em GLSL (OpenGL Shading Language) e devem ser compilados antes que possam ser ligados ao programa.
- Um programa WebGL pode ser utilizado apenas após ser ligado pelo método `gl.linkProgram()`.
- Para usar o programa, você deve ativá-lo com `gl.useProgram()` antes de emitir comandos de desenho.

## Exemplos

### Exemplo Básico de Criação de um WebGLProgram

```javascript
// Obtendo o contexto WebGL do canvas
const canvas = document.getElementById('meuCanvas');
const gl = canvas.getContext('webgl');

// Vertex shader
const vertexShaderSource = `
    attribute vec4 a_position;
    void main(void) {
        gl_Position = a_position;
    }
`;

// Fragment shader
const fragmentShaderSource = `
    void main(void) {
        gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0); // Cor vermelha
    }
`;

// Função para compilar o shader
function compileShader(source, type) {
    const shader = gl.createShader(type);
    gl.shaderSource(shader, source);
    gl.compileShader(shader);
    return shader;
}

// Compilando shaders
const vertexShader = compileShader(vertexShaderSource, gl.VERTEX_SHADER);
const fragmentShader = compileShader(fragmentShaderSource, gl.FRAGMENT_SHADER);

// Criando o programa WebGL e ligando os shaders
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

// Usando o programa
gl.useProgram(program);
```

### Desenhando um Triângulo

```javascript
const vertices = new Float32Array([
    0.0, 1.0,
    -1.0, -1.0,
    1.0, -1.0,
]);

const buffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, buffer);
gl.bufferData(gl.ARRAY_BUFFER, vertices, gl.STATIC_DRAW);

const positionLocation = gl.getAttribLocation(program, 'a_position');
gl.enableVertexAttribArray(positionLocation);
gl.vertexAttribPointer(positionLocation, 2, gl.FLOAT, false, 0, 0);

gl.clearColor(0.0, 0.0, 0.0, 1.0);
gl.clear(gl.COLOR_BUFFER_BIT);
gl.drawArrays(gl.TRIANGLES, 0, 3);
```

## Explicação
Um erro comum ao trabalhar com `WebGLProgram` é não verificar se os shaders foram compilados corretamente antes de vinculá-los ao programa. Sempre verifique os logs de erro após a compilação e o link do programa para garantir que não houve falhas. Além disso, é importante lembrar que a ordem dos comandos é crucial: você deve sempre ligar o programa antes de desenhar.

## Resumo em Uma Linha
WebGLProgram é um objeto que combina shaders e permite a execução de código de sombreamento na GPU, essencial para a renderização de gráficos 3D em JavaScript.