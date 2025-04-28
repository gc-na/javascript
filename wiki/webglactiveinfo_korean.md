<!--
Meta Description: # WebGLActiveInfo: 자바스크립트에서 WebGL의 활용 ## 개요 WebGLActiveInfo는 WebGL에서 셰이더 프로그램의 속성(예: 변수 이름, 유형 및 크기)을 설명하는 객체입니다. 이 객체는 WebGL API를 통해 셰이더의 활성 변수를 조회할 ...
Meta Keywords: info, 셰이더, const, type, size
-->

# WebGLActiveInfo: 자바스크립트에서 WebGL의 활용

## 개요
WebGLActiveInfo는 WebGL에서 셰이더 프로그램의 속성(예: 변수 이름, 유형 및 크기)을 설명하는 객체입니다. 이 객체는 WebGL API를 통해 셰이더의 활성 변수를 조회할 때 사용되며, 그래픽스 프로그래밍에서 중요한 역할을 합니다.

## 문서화
### 목적
WebGLActiveInfo는 WebGL 셰이더 프로그램에서 사용되는 활성 변수에 대한 정보를 제공합니다. 이 정보를 통해 개발자는 셰이더의 변수를 효율적으로 관리하고, 원하는 그래픽 효과를 구현할 수 있습니다.

### 사용법
WebGLActiveInfo 객체는 `getActiveAttrib` 및 `getActiveUniform` 메서드를 통해 생성됩니다. 이 메서드는 각각 활성 속성과 활성 유니폼 변수의 정보를 반환합니다.

### 세부사항
- **속성**:
  - `name`: 활성 변수의 이름을 나타내는 문자열입니다.
  - `type`: 변수의 데이터 유형을 나타내는 숫자입니다. 이 값은 WebGLRenderingContext의 상수 중 하나입니다.
  - `size`: 변수의 크기를 나타내며, 배열의 경우 배열의 길이를 의미합니다.

### 생성 예시
WebGLActiveInfo 객체를 사용하여 셰이더 프로그램의 활성 변수를 조회하는 기본적인 방법은 다음과 같습니다.

```javascript
// WebGL 컨텍스트 생성
const canvas = document.createElement('canvas');
const gl = canvas.getContext('webgl');

// 셰이더 프로그램 생성 및 링크 (가정)
const program = gl.createProgram();
// ... 셰이더 추가 및 링크 코드 ...

// 활성 속성 정보 가져오기
const numAttributes = gl.getProgramParameter(program, gl.ACTIVE_ATTRIBUTES);
for (let i = 0; i < numAttributes; i++) {
    const info = gl.getActiveAttrib(program, i);
    console.log(`Name: ${info.name}, Type: ${info.type}, Size: ${info.size}`);
}

// 활성 유니폼 정보 가져오기
const numUniforms = gl.getProgramParameter(program, gl.ACTIVE_UNIFORMS);
for (let i = 0; i < numUniforms; i++) {
    const info = gl.getActiveUniform(program, i);
    console.log(`Name: ${info.name}, Type: ${info.type}, Size: ${info.size}`);
}
```

## 설명
WebGLActiveInfo를 사용할 때의 흔한 실수는 배열 변수를 처리하는 방법입니다. `size` 속성은 배열의 크기를 나타내므로, 배열 변수를 사용할 경우 이 값을 고려해야 합니다. 또한, `type` 속성은 숫자로 반환되므로, 각 데이터 유형을 해석하기 위해 WebGLRenderingContext의 상수를 참조해야 합니다.

다른 일반적인 주의사항은, 프로그램이 링크되지 않았거나 활성 속성이 없는 경우 `getActiveAttrib` 또는 `getActiveUniform` 호출 시 null을 반환할 수 있다는 점입니다. 이를 방지하기 위해 셰이더 프로그램이 올바르게 링크되었는지 확인하는 것이 중요합니다.

## 한 줄 요약
WebGLActiveInfo는 WebGL 셰이더 프로그램의 활성 변수에 대한 정보를 제공하는 객체로, 그래픽스 프로그래밍에서 필수적인 요소입니다.