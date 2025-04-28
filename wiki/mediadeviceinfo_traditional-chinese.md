<!--
Meta Description: # MediaDeviceInfo：JavaScript中的媒體設備資訊 ## 概述 `MediaDeviceInfo` 是一個 JavaScript 介面，用於描述媒體設備（如攝像頭和麥克風）的詳細信息。它允許開發者獲取可用媒體設備的列表及其屬性，從而在網頁應用中實現多媒體功能。 ## 文檔 ##...
Meta Keywords: mediadeviceinfo, device, javascript, navigator, mediadevices
-->

# MediaDeviceInfo：JavaScript中的媒體設備資訊

## 概述
`MediaDeviceInfo` 是一個 JavaScript 介面，用於描述媒體設備（如攝像頭和麥克風）的詳細信息。它允許開發者獲取可用媒體設備的列表及其屬性，從而在網頁應用中實現多媒體功能。

## 文檔
### 目的
`MediaDeviceInfo` 介面主要用於獲取和管理用戶的媒體設備。這些設備通常是通過使用 `getUserMedia` API 獲得，並在應用中進行音視頻通訊。

### 使用方法
要獲取媒體設備信息，通常使用 `navigator.mediaDevices.enumerateDevices()` 方法，這會返回一個 `Promise`，其解析為 `MediaDeviceInfo` 物件的數組。每個 `MediaDeviceInfo` 物件包含以下屬性：

- `deviceId`: 設備的唯一標識符。
- `kind`: 設備的類型（如 `audioinput`, `audiooutput`, `videoinput`）。
- `label`: 設備的標籤，通常顯示設備的名稱（需要用戶授權）。
- `groupId`: 設備的組ID，指示設備是否屬於同一組。

### 詳細信息
使用 `MediaDeviceInfo` 的一般流程如下：

1. 調用 `navigator.mediaDevices.enumerateDevices()` 獲取設備列表。
2. 使用返回的 `MediaDeviceInfo` 數組來顯示或管理設備。

## 範例
以下是基本使用範例：

```javascript
navigator.mediaDevices.enumerateDevices()
    .then(function(devices) {
        devices.forEach(function(device) {
            console.log(device.kind + ": " + device.label + " id = " + device.deviceId);
        });
    })
    .catch(function(err) {
        console.error(err.name + ": " + err.message);
    });
```

在這個範例中，我們列出了所有可用的媒體設備及其類型和ID。

## 解釋
### 常見陷阱與注意事項
- **用戶授權**：在某些情況下，`label` 屬性可能會返回空值，這通常是因為用戶尚未授予訪問媒體設備的權限。
- **設備類型**：在使用 `kind` 屬性時，需要注意不同類型設備的使用情境（例如，音頻輸入與視頻輸入）。
- **設備ID穩定性**：`deviceId` 在不同的會話中可能會變化，特別是在用戶更改設備或重新啟動瀏覽器之後。

## 一句總結
`MediaDeviceInfo` 是一個強大的 JavaScript 介面，用於獲取和管理媒體設備的詳細信息，對於多媒體應用開發至關重要。