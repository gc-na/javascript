<!--
Meta Description: # WebGLActiveInfo: Entendendo a Classe do WebGL em JavaScript ## Sinopse O `WebGLActiveInfo` é uma interface da API WebGL que fornece informações sobr...
Meta Keywords: que, const, sobre, activeinfo, webgl
-->

# WebGLActiveInfo: Entendendo a Classe do WebGL em JavaScript

## Sinopse
O `WebGLActiveInfo` é uma interface da API WebGL que fornece informações sobre variáveis ativas de shader, como atributos e uniformes, permitindo aos desenvolvedores obter detalhes cruciais sobre as variáveis utilizadas em shaders.

## Documentação
O `WebGLActiveInfo` é utilizado em conjunto com a função `getActiveAttrib` ou `getActiveUniform` do contexto WebGL. Ele permite acessar informações relevantes sobre cada variável ativa em um shader, incluindo o nome, tipo e tamanho da variável. Essa classe é fundamental para entender como os dados são passados para os shaders.

### Propriedades:
- **name**: Uma string que representa o nome da variável ativa.
- **size**: Um inteiro que indica o número de elementos que a variável contém. Para variáveis de tipo vetor, isso representa o número de componentes.
- **type**: Um inteiro que indica o tipo da variável, que pode ser um dos seguintes valores:
  - `gl.FLOAT`
  - `gl.INT`
  - `gl.BOOL`
  - `gl.FLOAT_VEC2`
  - `gl.FLOAT_VEC3`
  - `gl.FLOAT_VEC4`
  - `gl.INT_VEC2`
  - `gl.INT_VEC3`
  - `gl.INT_VEC4`
  - `gl.BOOL_VEC2`
  - `gl.BOOL_VEC3`
  - `gl.BOOL_VEC4`
  - `gl.FLOAT_MAT2`
  - `gl.FLOAT_MAT3`
  - `gl.FLOAT_MAT4`
  - `gl.SAMPLER_2D`
  - `gl.SAMPLER_CUBE`
  
### Uso:
Para utilizar o `WebGLActiveInfo`, você deve primeiro compilar e vincular shaders com o WebGL. Após isso, você pode chamar `getActiveAttrib` ou `getActiveUniform` para obter a informação desejada.

## Exemplos

### Exemplo 1: Obtendo informações sobre atributos ativos
```javascript
// Criação do contexto WebGL
const canvas = document.createElement('canvas');
const gl = canvas.getContext('webgl');

// Compilação e vinculação de shaders
const vertexShaderSource = `...`; // Código do vertex shader
const fragmentShaderSource = `...`; // Código do fragment shader
const program = gl.createProgram();
// Adicione os shaders ao programa e vincule-o...

// Obtendo informações sobre atributos ativos
const numAttributes = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);
for (let i = 0; i < numAttributes; i++) {
    const activeInfo = gl.getActiveAttrib(program, i);
    console.log(`Atributo: ${activeInfo.name}, Tipo: ${activeInfo.type}, Tamanho: ${activeInfo.size}`);
}
```

### Exemplo 2: Obtendo informações sobre uniformes ativos
```javascript
// Obtendo informações sobre uniformes ativos
const numUniforms = gl.getProgramParameter(program, gl.ACTIVE_UNIFORMS);
for (let i = 0; i < numUniforms; i++) {
    const activeInfo = gl.getActiveUniform(program, i);
    console.log(`Uniforme: ${activeInfo.name}, Tipo: ${activeInfo.type}, Tamanho: ${activeInfo.size}`);
}
```

## Explicação
Um erro comum ao trabalhar com `WebGLActiveInfo` é não verificar se o programa foi vinculado corretamente antes de chamar `getActiveAttrib` ou `getActiveUniform`. Além disso, é importante lembrar que as informações obtidas podem variar dependendo das otimizações feitas pelo compilador de shaders, o que pode levar a resultados inesperados.

Outra armadilha é esquecer que o `size` de uma variável pode indicar múltiplos elementos. Por exemplo, um vetor de 4 componentes terá um `size` igual a 4, e você deve tratar isso adequadamente ao passar os dados para o shader.

## Resumo em Uma Linha
`WebGLActiveInfo` é uma interface que fornece detalhes sobre variáveis ativas em shaders no contexto da API WebGL em JavaScript.