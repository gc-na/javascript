<!--
Meta Description: # XRAnchor：在 JavaScript 中的擴增實境錨點 ## 簡介 XRAnchor 是一個在 WebXR API 中使用的物件，旨在幫助開發者在擴增實境（AR）環境中創建、管理和操作錨點。這些錨點可以被用於將虛擬物件固定在現實世界中的特定位置，從而提供更具沉浸感的用戶體驗。 ## 文件說...
Meta Keywords: xranchor, session, createanchor, const, javascript
-->

# XRAnchor：在 JavaScript 中的擴增實境錨點 

## 簡介
XRAnchor 是一個在 WebXR API 中使用的物件，旨在幫助開發者在擴增實境（AR）環境中創建、管理和操作錨點。這些錨點可以被用於將虛擬物件固定在現實世界中的特定位置，從而提供更具沉浸感的用戶體驗。

## 文件說明
XRAnchor 物件的主要目的是為了在擴增實境應用中提供穩定的參考點。這些錨點可以對應於真實世界的物理位置，並且可以在用戶的移動過程中保持其位置不變。XRAnchor 能夠與其他 XR 物件結合使用，幫助開發者創建更複雜的 AR 體驗。

### 使用方法
要使用 XRAnchor，開發者需要先創建 XRSession，然後使用 `createAnchor` 方法來生成一個新的錨點。以下是基本的使用步驟：

1. 初始化 XRSession。
2. 使用 `hitTest` 方法來檢測真實世界中的位置。
3. 使用 `createAnchor` 方法來創建一個新的 XRAnchor。

### 詳細說明
- **屬性**：
  - `position`：錨點在三維空間中的位置。
  - `orientation`：錨點的方向，通常用四元數表示。
  
- **方法**：
  - `createAnchor(pose)`：根據指定的姿勢創建一個新的 XRAnchor。
  - `remove()`：從場景中移除錨點。

## 範例
以下是使用 XRAnchor 的基本範例：

```javascript
async function initXR() {
    const session = await navigator.xr.requestSession('immersive-ar');
    const xrReferenceSpace = await session.requestReferenceSpace('local');

    session.addEventListener('select', onSelect);

    function onSelect(event) {
        const hitTestSource = session.requestHitTestSource({ space: xrReferenceSpace });
        
        // 假設我們已經獲得了一個有效的 hitTest 結果
        const anchor = session.createAnchor(hitTestResultPose);
        // 在這裡可以使用 anchor 來附加虛擬物件
    }
}
```

## 說明
使用 XRAnchor 時，開發者應注意以下幾點：
- 錨點的穩定性取決於環境的光線和使用者的移動速度。若環境變化劇烈，可能會影響錨點的準確性。
- 確保正確處理 session 和 reference space，以免出現錯誤。
- 在移除錨點後，應釋放相關資源以避免記憶體洩漏。

## 一句話總結
XRAnchor 是一個重要的 WebXR API 組件，幫助開發者在擴增實境環境中創建穩定的虛擬錨點。