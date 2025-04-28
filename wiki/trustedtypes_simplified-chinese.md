<!--
Meta Description: # Trusted Types: JavaScript 中的安全类型 ## 概述 Trusted Types 是一种安全性增强机制，旨在保护 Web 应用程序免受跨站脚本（XSS）攻击。通过限制对潜在不安全的 DOM 操作的访问，Trusted Types 允许开发者定义和验证安全的字符串，以确保应...
Meta Keywords: trusted, types, policy, input, javascript
-->

# Trusted Types: JavaScript 中的安全类型

## 概述
Trusted Types 是一种安全性增强机制，旨在保护 Web 应用程序免受跨站脚本（XSS）攻击。通过限制对潜在不安全的 DOM 操作的访问，Trusted Types 允许开发者定义和验证安全的字符串，以确保应用程序的安全性。

## 文档
### 目的
Trusted Types 的主要目的是减少应用程序中 XSS 攻击的风险。它通过强制开发者使用类型安全的 API 处理潜在不安全的字符串，从而提供额外的安全层。

### 用法
要使用 Trusted Types，开发者需要按照以下步骤进行：

1. **启用 Trusted Types**：通过在 HTML 文档中设置 `Content-Security-Policy` (CSP) 来启用 Trusted Types。
   
   ```html
   <meta http-equiv="Content-Security-Policy" content="trusted-types myPolicy;">
   ```

2. **定义策略**：使用 `TrustedTypePolicy` 创建一个策略，该策略定义了可以信任的字符串类型。

   ```javascript
   const policy = trustedTypes.createPolicy('myPolicy', {
       createHTML: (input) => {
           // 对输入进行验证和清理
           return input; // 返回安全的 HTML 字符串
       },
       createScript: (input) => {
           // 对输入进行验证和清理
           return input; // 返回安全的脚本字符串
       }
   });
   ```

3. **使用策略**：通过策略生成受信任的类型，以安全地进行 DOM 操作。

   ```javascript
   const safeHTML = policy.createHTML('<div>安全内容</div>');
   document.body.innerHTML = safeHTML; // 安全插入 HTML
   ```

### 详细信息
- **策略创建**：每个策略都可以定义多个创建方法，例如 `createHTML`、`createScript` 和 `createScriptURL`，以满足不同的需求。
- **安全性**：通过严格控制字符串的生成和插入，Trusted Types 可以显著降低 XSS 攻击的可能性。
- **浏览器支持**：Trusted Types 是现代浏览器支持的特性，但在较旧的浏览器中可能不受支持。

## 示例
### 示例 1：创建 HTML
```javascript
const policy = trustedTypes.createPolicy('myPolicy', {
    createHTML: (input) => {
        return input; // 假设输入已被验证
    }
});

const safeHTML = policy.createHTML('<p>这是安全的内容</p>');
document.body.innerHTML = safeHTML; // 安全地插入内容
```

### 示例 2：创建脚本
```javascript
const policy = trustedTypes.createPolicy('myPolicy', {
    createScript: (input) => {
        return input; // 假设输入已被验证
    }
});

const safeScript = policy.createScript('console.log("安全脚本");');
eval(safeScript); // 安全地执行脚本
```

## 说明
- **常见陷阱**：在使用 Trusted Types 时，开发者可能会忽视输入验证，导致潜在的安全风险。因此，务必在创建受信任类型之前，对输入进行严格的验证和清理。
- **注意事项**：Trusted Types 仅在启用 CSP 的情况下生效。如果未启用 CSP，Trusted Types 将无法提供预期的安全性。

## 一句话总结
Trusted Types 是一种 JavaScript 安全机制，通过限制不安全的字符串访问来防止 XSS 攻击。