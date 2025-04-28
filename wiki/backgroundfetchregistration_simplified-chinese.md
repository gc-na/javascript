<!--
Meta Description: # BackgroundFetchRegistration：JavaScript中的后台抓取注册 ## 概述 `BackgroundFetchRegistration` 是一个 JavaScript 接口，用于管理后台抓取请求。它允许开发者在后台异步下载资源，确保即使用户离开页面，下载仍然可以进行。...
Meta Keywords: backgroundfetchregistration, api, backgroundfetch, fetch, error
-->

# BackgroundFetchRegistration：JavaScript中的后台抓取注册

## 概述
`BackgroundFetchRegistration` 是一个 JavaScript 接口，用于管理后台抓取请求。它允许开发者在后台异步下载资源，确保即使用户离开页面，下载仍然可以进行。这对于需要下载大文件或多文件的应用程序尤其有用。

## 文档
### 目的
`BackgroundFetchRegistration` 旨在提供一种方法，使网页能够在后台进行大规模数据抓取，而不影响用户体验。此接口能够在服务工作线程中运行，允许开发者在用户离开网页后仍然能够继续下载。

### 用法
该接口通常在后台抓取 API 中使用。开发者可以通过调用 `navigator.backgroundFetch.fetch()` 方法来发起一个后台抓取请求，并返回一个 `BackgroundFetchRegistration` 对象。

### 详细信息
- **属性**
  - `id`: 抓取请求的唯一标识符。
  - `status`: 抓取请求的当前状态（例如，pending、completed、failed）。
  - `uploadedBytes`: 成功上传的字节数。
  - `uploadedBytes`: 成功下载的字节数。

- **方法**
  - `abort()`: 中止当前的后台抓取请求。
  - `match()`: 查找与请求匹配的缓存资源。

## 示例
以下是 `BackgroundFetchRegistration` 的基本用法示例：

```javascript
navigator.backgroundFetch.fetch('example-fetch', [
  new Request('/large-file-1.zip'),
  new Request('/large-file-2.zip')
]).then(registration => {
  console.log('后台抓取请求已注册:', registration.id);
}).catch(error => {
  console.error('后台抓取请求失败:', error);
});
```

## 说明
- **常见陷阱**
  - 当前并非所有浏览器都支持 `BackgroundFetch` API，因此在使用前请检查兼容性。
  - 请注意，后台抓取请求的生命周期不受页面关闭的影响，但仍需遵循浏览器的限制，如网络连接和电量状态。

- **注意事项**
  - 确保在合适的上下文中使用该 API，例如在服务工作线程中。
  - 为了避免不必要的资源消耗，建议合理配置抓取的资源大小和数量。

## 一句话总结
`BackgroundFetchRegistration` 允许开发者在后台异步抓取资源，提升用户体验和数据下载的效率。