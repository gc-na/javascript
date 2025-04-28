<!--
Meta Description: # TrustedScript: JavaScript 中的安全脚本信任机制 ## 摘要 TrustedScript 是一种 JavaScript API，旨在增强 Web 应用程序的安全性，确保只执行经过验证的脚本，以防止跨站脚本（XSS）攻击。 ## 文档 ### 目的 TrustedScrip...
Meta Keywords: trustedscript, javascript, api, script, trustedtypes
-->

# TrustedScript: JavaScript 中的安全脚本信任机制

## 摘要
TrustedScript 是一种 JavaScript API，旨在增强 Web 应用程序的安全性，确保只执行经过验证的脚本，以防止跨站脚本（XSS）攻击。

## 文档
### 目的
TrustedScript 通过提供一个安全的脚本执行环境，确保只有被信任的脚本可以被执行。这种机制是 Web 开发中防止恶意代码注入的重要措施。

### 使用方法
在 JavaScript 中，TrustedScript 通常与其他安全 API（如 Trusted Types）结合使用。开发者可以创建和使用 TrustedScript 实例，确保传递给 DOM 操作的脚本是安全的。

```javascript
// 示例创建 TrustedScript 的过程
const trustedScript = TrustedScript.create('console.log("Hello, world!");');

// 执行被信任的脚本
eval(trustedScript);
```

### 细节
- **创建 TrustedScript**: 通过 `TrustedScript.create()` 方法创建一个新的 TrustedScript 实例。
- **执行安全性**: 只有通过 TrustedScript 创建的脚本才能被安全地执行，其他未验证的脚本将被阻止。
- **浏览器支持**: 目前，TrustedScript API 还处于实验阶段，并非所有浏览器均支持该功能。

## 示例
### 基本用法
```javascript
// 创建一个 TrustedScript 实例
const trustedScript = TrustedScript.create('alert("This is a trusted script.");');

// 安全地执行 TrustedScript
eval(trustedScript);
```

### 结合使用 Trusted Types
```javascript
// 启用 Trusted Types
if (window.TrustedTypes) {
  const trustedTypes = TrustedTypes.createPolicy('default', {
    createScript: (script) => TrustedScript.create(script),
  });

  // 使用 TrustedTypes 创建和执行脚本
  const script = trustedTypes.createScript('console.log("Executed safely!");');
  eval(script);
}
```

## 解释
### 常见问题
- **不支持的浏览器**: 在不支持 TrustedScript 的浏览器中，使用该 API 将会导致错误。
- **错误的脚本内容**: 如果创建 TrustedScript 的内容不安全或格式不正确，可能会导致意外的执行错误。

### 注意事项
- **安全性第一**: 始终确保传递给 TrustedScript 的内容是经过验证和信任的。
- **开发阶段**: 由于该 API 仍在开发阶段，建议在生产环境中谨慎使用，并关注浏览器的更新和支持情况。

## 一句话总结
TrustedScript 是一种增强 JavaScript 应用程序安全性的机制，通过验证脚本内容来防止跨站脚本攻击。