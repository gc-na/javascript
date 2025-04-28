<!--
Meta Description: # MediaDeviceInfo：JavaScript 中的媒介設備信息 ## 概述 `MediaDeviceInfo` 是 JavaScript 中用來描述媒介設備（如攝像頭和麥克風）的接口，提供了設備的識別信息和類型，適用於 WebRTC 和其他多媒體應用程序。 ## 文檔 `MediaDev...
Meta Keywords: device, err, mediadeviceinfo, javascript, devices
-->

# MediaDeviceInfo：JavaScript 中的媒介設備信息

## 概述
`MediaDeviceInfo` 是 JavaScript 中用來描述媒介設備（如攝像頭和麥克風）的接口，提供了設備的識別信息和類型，適用於 WebRTC 和其他多媒體應用程序。

## 文檔
`MediaDeviceInfo` 物件包含有關可用媒介設備的信息，通常用於 `navigator.mediaDevices.enumerateDevices()` 方法的返回結果中。這些信息對於開發者來說非常重要，尤其是在需要選擇或切換不同媒介設備的情況下。

### 主要屬性
- **deviceId**: 唯一識別設備的字符串。
- **kind**: 指示設備類型的字符串，可能的值包括 `videoinput`（視頻輸入設備）、`audioinput`（音頻輸入設備）和 `audiooutput`（音頻輸出設備）。
- **label**: 設備的名稱或標籤，可能會因瀏覽器的隱私設置而返回空字符串。
- **groupId**: 同組設備的識別符，通常用於將同一品牌或類型的設備分組。

### 用法
要獲取媒介設備信息，開發者可以使用以下代碼：

```javascript
navigator.mediaDevices.enumerateDevices()
  .then(devices => {
    devices.forEach(device => {
      console.log(`${device.kind}: ${device.label} (ID: ${device.deviceId})`);
    });
  })
  .catch(err => {
    console.error(`${err.name}: ${err.message}`);
  });
```

這段代碼將列出所有可用的媒介設備及其信息。

## 示例
### 基本使用範例
以下範例展示了如何列出所有的音頻輸入設備：

```javascript
navigator.mediaDevices.enumerateDevices()
  .then(devices => {
    devices.forEach(device => {
      if (device.kind === 'audioinput') {
        console.log(`音頻輸入設備: ${device.label} (ID: ${device.deviceId})`);
      }
    });
  })
  .catch(err => {
    console.error(`錯誤: ${err.message}`);
  });
```

### 獲取視頻輸入設備
這段代碼展示了如何獲取視頻輸入設備的名稱：

```javascript
navigator.mediaDevices.enumerateDevices()
  .then(devices => {
    devices.forEach(device => {
      if (device.kind === 'videoinput') {
        console.log(`視頻輸入設備: ${device.label} (ID: ${device.deviceId})`);
      }
    });
  })
  .catch(err => {
    console.error(`錯誤: ${err.message}`);
  });
```

## 解釋
在使用 `MediaDeviceInfo` 時，開發者應注意以下幾點：

- **隱私設置**: 在某些瀏覽器中，如果用戶未授權訪問媒介設備，`label` 可能會返回空字符串。開發者應考慮這一點並適當處理。
- **設備權限**: 確保在調用 `enumerateDevices` 方法之前，已經請求並獲得了媒介設備的使用權限。
- **跨瀏覽器兼容性**: 雖然大多數現代瀏覽器都支持 `MediaDeviceInfo`，但在開發過程中仍需檢查兼容性。

## 一句總結
`MediaDeviceInfo` 是 JavaScript 中用於描述和識別媒介設備的接口，對於多媒體應用開發至關重要。