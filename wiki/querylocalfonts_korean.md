<!--
Meta Description: # queryLocalFonts: 자바스크립트에서 로컬 폰트 조회하기 ## 개요 `queryLocalFonts`는 웹 애플리케이션에서 사용자의 로컬 시스템에 설치된 폰트를 조회하는 자바스크립트 메서드입니다. 이 기능은 브라우저 내에서 사용자가 어떤 폰트를 갖고 있는지 ...
Meta Keywords: querylocalfonts, error, 폰트를, fonts, console
-->

# queryLocalFonts: 자바스크립트에서 로컬 폰트 조회하기

## 개요
`queryLocalFonts`는 웹 애플리케이션에서 사용자의 로컬 시스템에 설치된 폰트를 조회하는 자바스크립트 메서드입니다. 이 기능은 브라우저 내에서 사용자가 어떤 폰트를 갖고 있는지 파악할 수 있게 해주며, 이를 통해 폰트 관리 및 디자인에 유용하게 활용될 수 있습니다.

## 문서화

### 목적
`queryLocalFonts` 메서드는 사용자가 로컬 시스템에 설치된 모든 폰트의 목록을 반환합니다. 이를 통해 웹 개발자는 사용자의 환경에 적합한 폰트를 선택하거나, 특정 폰트가 사용 가능한지 확인할 수 있습니다.

### 사용법
`queryLocalFonts`는 비동기적으로 작동하며, Promise를 반환합니다. 이 메서드는 다음과 같이 호출할 수 있습니다.

```javascript
queryLocalFonts().then(fonts => {
    console.log(fonts);
}).catch(error => {
    console.error('폰트를 조회하는 중 오류 발생:', error);
});
```

### 세부 정보
- **반환 값**: `queryLocalFonts`는 사용자의 로컬 폰트 목록을 포함하는 배열을 반환합니다. 각 폰트 객체는 폰트의 이름 및 스타일 정보를 포함합니다.
- **브라우저 지원**: 이 메서드는 최신 웹 브라우저에서만 지원되므로, 사용하기 전에 호환성을 확인해야 합니다.

## 예제

### 기본 사용 예제
```javascript
async function displayLocalFonts() {
    try {
        const fonts = await queryLocalFonts();
        fonts.forEach(font => {
            console.log(`폰트 이름: ${font.family}, 스타일: ${font.style}`);
        });
    } catch (error) {
        console.error('폰트를 조회하는 중 오류 발생:', error);
    }
}

displayLocalFonts();
```

### 특정 폰트 확인
```javascript
async function checkFontAvailability(fontName) {
    try {
        const fonts = await queryLocalFonts();
        const isAvailable = fonts.some(font => font.family === fontName);
        console.log(`${fontName}는 ${isAvailable ? '사용 가능합니다' : '사용 불가능합니다'}.`);
    } catch (error) {
        console.error('폰트를 조회하는 중 오류 발생:', error);
    }
}

checkFontAvailability('Arial');
```

## 설명
`queryLocalFonts`를 사용할 때 주의할 점은 다음과 같습니다:
- **비동기 처리**: 이 메서드는 비동기적으로 작동하므로, Promise를 사용하여 결과를 처리해야 합니다. 이를 간과할 경우, 결과를 예상치 못한 시점에서 사용할 수 있습니다.
- **브라우저 호환성**: 모든 브라우저가 이 기능을 지원하지 않으므로, 특정 브라우저에서 동작하지 않을 수 있습니다. 항상 브라우저의 최신 버전을 사용하고, 폴리필이 필요할 수 있는지 검토해야 합니다.

## 한 줄 요약
`queryLocalFonts`는 사용자의 로컬 시스템에서 설치된 폰트 목록을 비동기적으로 조회하는 자바스크립트 메서드입니다.