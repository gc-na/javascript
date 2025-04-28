<!--
Meta Description: # FeaturePolicy：JavaScript 中的功能策略详解 ## 概述 FeaturePolicy 是一种用于控制网页中功能访问权限的机制，允许开发者指定哪些特性（如摄像头、麦克风等）可以被页面或其嵌入的内容使用。这一特性有助于提升页面的安全性和用户隐私。 ## 文档 ### 目的 Fe...
Meta Keywords: iframe, featurepolicy, http, self, camera
-->

# FeaturePolicy：JavaScript 中的功能策略详解

## 概述
FeaturePolicy 是一种用于控制网页中功能访问权限的机制，允许开发者指定哪些特性（如摄像头、麦克风等）可以被页面或其嵌入的内容使用。这一特性有助于提升页面的安全性和用户隐私。

## 文档
### 目的
FeaturePolicy 旨在提供一种灵活的方式，允许网页开发者通过声明特定的功能使用权限，来限制嵌入内容（如 iframe）或页面本身对某些功能的访问。

### 使用
FeaturePolicy 通过 HTTP 头或 `<iframe>` 标签的 `allow` 属性进行配置。以下是两种常见的用法：

1. **通过 HTTP 头部设置**：
   服务器可以通过设置 `Feature-Policy` HTTP 头部来控制整个页面的功能访问。

   ```http
   Feature-Policy: camera 'none'; microphone 'self'
   ```

2. **通过 `<iframe>` 标签设置**：
   在 `<iframe>` 标签中使用 `allow` 属性来控制嵌入内容的功能访问。

   ```html
   <iframe src="example.html" allow="camera 'self'; microphone 'none'"></iframe>
   ```

### 细节
- **支持的功能**：FeaturePolicy 支持多种功能，包括但不限于以下几项：
  - `camera`
  - `microphone`
  - `geolocation`
  - `payment`
  
- **值的说明**：
  - `'none'`：完全禁止访问该功能。
  - `'self'`：仅允许同源的内容访问该功能。
  - 其他源的 URI：可以指定特定的源来允许访问。

## 示例
### 基本用法示例
1. **通过 HTTP 头部禁止摄像头访问**：

   ```http
   Feature-Policy: camera 'none'
   ```

2. **在 iframe 中允许同源访问麦克风**：

   ```html
   <iframe src="child.html" allow="microphone 'self'"></iframe>
   ```

3. **组合使用多个功能**：

   ```http
   Feature-Policy: camera 'none'; microphone 'self'; geolocation 'self'
   ```

## 说明
- **常见陷阱**：
  - 确保在服务器上正确配置 HTTP 头部，否则可能无法生效。
  - 注意不同浏览器对 FeaturePolicy 的支持程度，某些功能在特定浏览器中可能无法使用。

- **注意事项**：
  - 需要在文档的 `<head>` 部分或服务器配置中设置 FeaturePolicy，以确保在页面加载时生效。
  - 在使用 `<iframe>` 时，确保嵌入内容的源符合声明的策略。

## 一句总结
FeaturePolicy 是一种用于控制网页功能访问权限的机制，有助于提升安全性和用户隐私。