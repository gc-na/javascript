<!--
Meta Description: # CSSTransition: 자바스크립트에서의 CSS 전환 효과 ## 개요 CSSTransition은 React와 같은 라이브러리에서 CSS 전환 효과를 쉽게 관리할 수 있도록 도와주는 컴포넌트입니다. 이 기능을 사용하면 애니메이션과 전환 효과를 간편하게 추가하여 사...
Meta Keywords: css, csstransition, example, import, react
-->

# CSSTransition: 자바스크립트에서의 CSS 전환 효과

## 개요
CSSTransition은 React와 같은 라이브러리에서 CSS 전환 효과를 쉽게 관리할 수 있도록 도와주는 컴포넌트입니다. 이 기능을 사용하면 애니메이션과 전환 효과를 간편하게 추가하여 사용자 경험을 개선할 수 있습니다.

## 문서
### 목적
CSSTransition은 DOM의 상태 변화에 따라 CSS 클래스가 자동으로 적용되도록 하여, 요소가 나타나거나 사라질 때 부드러운 전환 효과를 제공합니다. 이를 통해 개발자는 복잡한 애니메이션 로직을 간소화할 수 있습니다.

### 사용법
CSSTransition은 다음과 같은 주요 속성을 제공합니다:
- `in`: 요소가 나타나는 상태를 제어합니다.
- `timeout`: 전환 효과의 지속 시간을 설정합니다.
- `classNames`: 전환 효과에 사용할 CSS 클래스의 접두사입니다.

다음은 CSSTransition을 사용하는 기본적인 코드 예시입니다.

```javascript
import React from 'react';
import { CSSTransition } from 'react-transition-group';
import './styles.css'; // CSS 파일

const MyComponent = ({ show }) => {
  return (
    <CSSTransition
      in={show}
      timeout={300}
      classNames="fade"
      unmountOnExit
    >
      <div className="my-box">안녕하세요!</div>
    </CSSTransition>
  );
};
```

## 예시
### 기본 사용 예
```javascript
import React, { useState } from 'react';
import { CSSTransition } from 'react-transition-group';
import './styles.css';

const Example = () => {
  const [inProp, setInProp] = useState(false);

  return (
    <>
      <button onClick={() => setInProp(!inProp)}>
        클릭하여 전환
      </button>
      <CSSTransition
        in={inProp}
        timeout={500}
        classNames="example"
      >
        <div className="example-box">안녕하세요!</div>
      </CSSTransition>
    </>
  );
};
```

### CSS 스타일
아래는 CSS 전환 효과에 사용할 스타일입니다.

```css
.example-enter {
  opacity: 0;
}
.example-enter-active {
  opacity: 1;
  transition: opacity 500ms;
}
.example-exit {
  opacity: 1;
}
.example-exit-active {
  opacity: 0;
  transition: opacity 500ms;
}
```

## 설명
CSSTransition을 사용할 때 주의할 점은 다음과 같습니다:
- `timeout` 속성은 전환 효과의 길이에 맞춰 설정해야 합니다. 이 값이 CSS에서 정의한 전환 시간과 일치하지 않으면 애니메이션이 비정상적으로 보일 수 있습니다.
- `unmountOnExit` 속성은 요소가 사라질 때 DOM에서 제거되도록 하여, 메모리 누수를 방지할 수 있습니다.
- CSS 클래스 이름은 `classNames` 속성을 통해 접두사를 지정하고, 세부 전환 상태에 맞게 추가 CSS 클래스를 정의해야 합니다.

## 한 줄 요약
CSSTransition은 자바스크립트에서 CSS 전환 효과를 간편하게 관리할 수 있도록 해주는 유용한 컴포넌트입니다.