<!--
Meta Description: # XRAnchorSet：JavaScript擴增實境中的錨點集 ## 簡介 XRAnchorSet 是一個在擴增實境（AR）應用中使用的 JavaScript API，用於管理和操作一組錨點。錨點是虛擬物體在現實世界中定位的基礎，XRAnchorSet 提供了對這些錨點的增刪改查功能，讓開發者能...
Meta Keywords: xranchorset, anchorset, anchor, const, pose
-->

# XRAnchorSet：JavaScript擴增實境中的錨點集

## 簡介
XRAnchorSet 是一個在擴增實境（AR）應用中使用的 JavaScript API，用於管理和操作一組錨點。錨點是虛擬物體在現實世界中定位的基礎，XRAnchorSet 提供了對這些錨點的增刪改查功能，讓開發者能夠更靈活地控制擴增實境體驗。

## 文檔
### 目的
XRAnchorSet 的主要目的是為了讓開發者能夠方便地管理多個錨點，這在擴增實境應用中是非常重要的，因為錨點的準確性直接影響到虛擬物體的顯示效果。

### 使用方法
要使用 XRAnchorSet，開發者需先獲取 XRSession 物件，然後利用此物件來創建或獲取現有的 XRAnchorSet。此 API 提供了多種方法來操作錨點，包括添加、刪除和查詢錨點。

#### 基本用法：
```javascript
// 獲取 XRSession
navigator.xr.requestSession('immersive-ar').then((session) => {
    // 創建 XRAnchorSet
    const anchorSet = session.requestAnchorSet();

    // 添加錨點
    const anchor = anchorSet.addAnchor(pose);

    // 刪除錨點
    anchorSet.removeAnchor(anchor);
});
```

### 詳細說明
- **XRAnchorSet** 物件包含了一組錨點，這些錨點可以通過 `addAnchor()` 方法來添加，或通過 `removeAnchor()` 方法來刪除。
- 錨點的姿勢（pose）需要提供準確的位置和方向，以確保虛擬物體能夠正確顯示。
- 開發者應根據實際需求來管理錨點的生命週期，避免在不必要的情況下保留過多的錨點，這樣可以提升應用的性能。

## 範例
### 基本使用範例
```javascript
navigator.xr.requestSession('immersive-ar').then((session) => {
    const anchorSet = session.requestAnchorSet();

    // 假設已經獲得一個有效的 pose 物件
    const pose = { position: { x: 0, y: 0, z: 0 }, orientation: { x: 0, y: 0, z: 0, w: 1 } };
    
    const anchor = anchorSet.addAnchor(pose);
    console.log('錨點已添加:', anchor);

    // 刪除錨點
    anchorSet.removeAnchor(anchor);
    console.log('錨點已刪除:', anchor);
});
```

## 說明
- **常見陷阱**：使用錨點時，開發者必須確保提供的姿勢信息是準確的，否則虛擬物體可能顯示在錯誤的位置。
- **性能考量**：避免在大量場景中同時保持多個錨點，這會影響性能，特別是在移動設備上。
- **支援性**：並非所有瀏覽器或設備都支援 XR API，開發者應檢查其相容性。

## 一句總結
XRAnchorSet 是一個強大的工具，幫助開發者在 JavaScript 擴增實境應用中有效管理錨點。