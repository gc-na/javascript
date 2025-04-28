<!--
Meta Description: # WebGLProgram: JavaScript에서의 WebGL 프로그램 객체 ## 개요 WebGLProgram은 WebGL에서 셰이더 프로그램을 나타내는 객체로, GPU에서 실행되는 셰이더를 연결하고 관리하는 역할을 합니다. 이 객체는 vertex 셰이더와 fragm...
Meta Keywords: 셰이더, const, 프로그램, 셰이더를, webgl
-->

# WebGLProgram: JavaScript에서의 WebGL 프로그램 객체

## 개요
WebGLProgram은 WebGL에서 셰이더 프로그램을 나타내는 객체로, GPU에서 실행되는 셰이더를 연결하고 관리하는 역할을 합니다. 이 객체는 vertex 셰이더와 fragment 셰이더를 결합하여 그래픽스를 렌더링하는 데 필요한 모든 정보를 포함하고 있습니다.

## 문서화
### 목적
WebGLProgram은 JavaScript에서 WebGL을 사용할 때, 그래픽스를 효과적으로 렌더링하기 위한 셰이더의 집합을 정의합니다. 이 객체는 `WebGLRenderingContext`의 `createProgram` 메서드를 통해 생성되며, 프로그램이 활성화되면 GPU에서 그래픽 작업을 수행하는 데 사용됩니다.

### 사용법
WebGLProgram을 사용하려면 다음 단계가 필요합니다:

1. **WebGL 컨텍스트 생성**: HTML5 `<canvas>` 요소에서 WebGL 컨텍스트를 가져옵니다.
2. **셰이더 생성**: vertex 셰이더와 fragment 셰이더를 각각 정의하고 컴파일합니다.
3. **프로그램 생성**: `createProgram` 메서드를 호출하여 WebGLProgram 객체를 생성합니다.
4. **셰이더 추가**: `attachShader` 메서드를 사용하여 생성한 셰이더를 프로그램에 추가합니다.
5. **프로그램 링크**: `linkProgram` 메서드를 호출하여 프로그램을 링크합니다.
6. **프로그램 사용**: `useProgram` 메서드로 프로그램을 활성화합니다.

### 세부사항
- **프로그램의 속성**: WebGLProgram 객체는 셰이더 코드, 변수, 그리고 GLSL (OpenGL Shading Language)과의 연결 정보를 포함합니다.
- **셰이더의 상태**: 프로그램의 상태는 링크된 후에만 유효합니다. 따라서 셰이더를 변경한 후에는 항상 프로그램을 다시 링크해야 합니다.
- **에러 처리**: 프로그램 링크 과정에서 에러가 발생할 수 있으므로, `getProgramInfoLog` 메서드를 통해 에러 메시지를 확인하는 것이 중요합니다.

## 예제
다음은 WebGLProgram을 사용하는 기본적인 예제입니다:

```javascript
// WebGL 컨텍스트 생성
const canvas = document.getElementById('canvas');
const gl = canvas.getContext('webgl');

// Vertex 셰이더 코드
const vertexShaderSource = `
  attribute vec4 position;
  void main() {
    gl_Position = position;
  }
`;

// Fragment 셰이더 코드
const fragmentShaderSource = `
  void main() {
    gl_FragColor = vec4(1.0, 0.0, 0.0, 1.0); // Red color
  }
`;

// 셰이더 컴파일 함수
function compileShader(gl, source, type) {
  const shader = gl.createShader(type);
  gl.shaderSource(shader, source);
  gl.compileShader(shader);
  return shader;
}

// 셰이더 생성 및 프로그램 링크
const vertexShader = compileShader(gl, vertexShaderSource, gl.VERTEX_SHADER);
const fragmentShader = compileShader(gl, fragmentShaderSource, gl.FRAGMENT_SHADER);
const program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

// 프로그램 사용
gl.useProgram(program);
```

## 설명
- **셰이더 코드의 작성**: 셰이더 코드는 GLSL로 작성되며, JavaScript 내에서 문자열로 정의됩니다.
- **링크 후 수정 불가**: 프로그램이 한 번 링크된 후, 셰이더를 수정하면 다시 링크해야 합니다.
- **성능**: 프로그램의 성능은 셰이더 코드의 복잡성에 따라 달라질 수 있습니다. 최적화를 고려하여 간결한 코드를 작성하는 것이 좋습니다.

## 한 줄 요약
WebGLProgram은 WebGL에서 셰이더 프로그램을 생성하고 관리하는 객체로, GPU에서 그래픽스를 렌더링하는 데 필수적입니다.