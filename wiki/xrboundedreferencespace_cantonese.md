<!--
Meta Description: # XRBoundedReferenceSpace：JavaScript 中的擴增現實參考空間 ## 簡介 XRBoundedReferenceSpace 是 WebXR API 中的一個重要組件，主要用於在擴增現實（AR）應用程式中建立一個受限的參考空間。它使開發者能夠在真實環境中設置虛擬物件的位...
Meta Keywords: xrboundedreferencespace, xrsession, requestreferencespace, javascript, then
-->

# XRBoundedReferenceSpace：JavaScript 中的擴增現實參考空間

## 簡介
XRBoundedReferenceSpace 是 WebXR API 中的一個重要組件，主要用於在擴增現實（AR）應用程式中建立一個受限的參考空間。它使開發者能夠在真實環境中設置虛擬物件的位置和運動，從而提升用戶的沉浸感。

## 文檔
### 目的
XRBoundedReferenceSpace 允許開發者在物理環境中劃定一個邊界，並在該邊界內創建虛擬內容。這對於需要精確定位的應用（如室內導航、遊戲等）尤其重要。

### 使用方式
要使用 XRBoundedReferenceSpace，開發者需要首先獲取 XRSession，然後請求一個受限的參考空間。通過以下步驟來實現：

1. 建立一個 XRSession。
2. 使用 `requestReferenceSpace` 方法請求 `XRBoundedReferenceSpace`。
3. 在該參考空間中進行物件的定位和渲染。

### 詳細說明
- **XRSession**：表示一個 XR 會話的實例，可以用來創建和管理 3D 環境。
- **requestReferenceSpace**：此方法會根據會話參數，返回一個特定的參考空間類型，包括 `XRBoundedReferenceSpace`。
- **邊界**：在使用 XRBoundedReferenceSpace 時，開發者需先定義邊界，這通常透過用戶的環境掃描來實現。

## 示例
以下是使用 XRBoundedReferenceSpace 的基本示例：

```javascript
navigator.xr.requestSession('immersive-ar').then(session => {
    session.requestReferenceSpace('bounded').then(referenceSpace => {
        // 使用 referenceSpace 進行虛擬物件的定位
        // ...
    });
});
```

## 解釋
使用 XRBoundedReferenceSpace 時，開發者需注意以下幾點：
- 在某些設備上，可能不支持 `XRBoundedReferenceSpace`，因此需要進行功能檢查。
- 確保用戶在使用應用時有足夠的空間，以避免干擾虛擬物件的正常運作。
- 邊界的設置需要用戶的參與，通常需要用戶進行環境掃描。

## 總結
XRBoundedReferenceSpace 是一個強大的工具，能夠幫助開發者在擴增現實應用中創建更精確和沉浸的虛擬體驗。