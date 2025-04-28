<!--
Meta Description: # GPUMapMode: JavaScript에서 GPU 메모리 맵 모드 이해하기 ## 개요 GPUMapMode는 JavaScript에서 WebGPU API를 사용할 때 GPU 메모리를 다루는 방법을 정의하는 열거형입니다. 이 모드는 GPU 메모리에 접근할 때의 동작 방...
Meta Keywords: gpu, const, gpumapmode, 데이터, buffer
-->

# GPUMapMode: JavaScript에서 GPU 메모리 맵 모드 이해하기

## 개요
GPUMapMode는 JavaScript에서 WebGPU API를 사용할 때 GPU 메모리를 다루는 방법을 정의하는 열거형입니다. 이 모드는 GPU 메모리에 접근할 때의 동작 방식을 설정하여, 성능과 효율성을 극대화합니다.

## 문서화
GPUMapMode는 WebGPU API의 일부로, GPU 메모리의 맵핑 방식을 정의합니다. 주로 `GPUBuffer`의 데이터를 CPU와 GPU 간에 전송할 때 사용됩니다. 이 열거형은 다음과 같은 모드를 제공합니다:

- **GPUMapMode.READ**: GPU 메모리에서 데이터를 읽을 수 있는 모드입니다. 이 모드는 CPU가 GPU 메모리에서 데이터를 읽을 수 있도록 허용합니다.
  
- **GPUMapMode.WRITE**: GPU 메모리에 데이터를 쓸 수 있는 모드입니다. 이 설정은 CPU가 GPU 메모리에 데이터를 기록할 수 있게 합니다.

- **GPUMapMode.READ_WRITE**: 읽기 및 쓰기 모두 허용하는 모드입니다. 이 모드는 CPU가 GPU 메모리에서 데이터를 읽고 쓸 수 있는 가장 유연한 옵션입니다.

### 사용법
GPUMapMode는 `GPUBuffer.mapAsync()` 메서드와 함께 사용됩니다. 이 메서드는 데이터 전송을 비동기적으로 처리하여, CPU와 GPU 간의 효율적인 데이터 교환을 가능하게 합니다.

```javascript
// WebGPU 컨텍스트 생성
const adapter = await navigator.gpu.requestAdapter();
const device = await adapter.requestDevice();

// GPUBuffer 생성
const buffer = device.createBuffer({
    size: 1024,
    usage: GPUBufferUsage.COPY_DST | GPUBufferUsage.MAP_READ | GPUBufferUsage.MAP_WRITE,
});

// 데이터 매핑
await buffer.mapAsync(GPUMapMode.READ_WRITE);
const mappedBuffer = buffer.getMappedRange();
```

## 예제
아래는 GPUMapMode를 사용하는 간단한 예제입니다.

```javascript
async function example() {
    // GPU 장치 요청
    const adapter = await navigator.gpu.requestAdapter();
    const device = await adapter.requestDevice();

    // GPUBuffer 생성
    const buffer = device.createBuffer({
        size: 4,
        usage: GPUBufferUsage.MAP_READ | GPUBufferUsage.MAP_WRITE,
    });

    // 데이터 매핑
    await buffer.mapAsync(GPUMapMode.READ_WRITE);
    const array = new Float32Array(buffer.getMappedRange());
    
    // 데이터 수정
    array[0] = 1.0;
    array[1] = 2.0;

    // GPUBuffer 언맵
    buffer.unmap();
}
example();
```

## 설명
GPUMapMode 사용 시 주의해야 할 점은 데이터 매핑 후 GPUBuffer를 언맵하기 전까지는 해당 메모리에 접근할 수 없다는 것입니다. 또한, GPU 메모리의 크기와 사용 용도를 정확히 정의하는 것이 중요하며, 잘못된 설정은 성능 저하를 초래할 수 있습니다. 데이터 전송이 완료되기 전에 GPUBuffer를 언맵하면 오류가 발생할 수 있습니다.

## 한 줄 요약
GPUMapMode는 JavaScript의 WebGPU API에서 GPU 메모리에 대한 읽기 및 쓰기 접근 방식을 정의하는 열거형입니다.