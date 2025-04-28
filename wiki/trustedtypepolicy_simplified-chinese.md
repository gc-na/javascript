<!--
Meta Description: # TrustedTypePolicy：JavaScript中的安全字符串处理 ## 概述 `TrustedTypePolicy` 是 JavaScript 中用于防止跨站脚本攻击（XSS）的一种机制。它通过定义受信任的类型来确保应用程序在处理动态内容时的安全性。 ## 文档 `TrustedTyp...
Meta Keywords: trustedtypepolicy, trustedtypes, javascript, const, createhtml
-->

# TrustedTypePolicy：JavaScript中的安全字符串处理

## 概述
`TrustedTypePolicy` 是 JavaScript 中用于防止跨站脚本攻击（XSS）的一种机制。它通过定义受信任的类型来确保应用程序在处理动态内容时的安全性。

## 文档
`TrustedTypes` 是一种 Web API，它允许开发者创建 `TrustedTypePolicy` 实例，以便为特定上下文定义受信任的字符串类型。通过使用 `TrustedTypes`，开发者可以减少在 DOM 中直接插入不安全字符串的风险，从而增强应用程序的安全性。

### 目的
`TrustedTypePolicy` 的主要目的是限制和控制应用程序使用的字符串，以防止 XSS 攻击。它确保只有经过验证的字符串可以用于敏感操作，如插入到 DOM。

### 使用方法
1. **创建 TrustedTypePolicy 实例**：
   使用 `trustedTypes.createPolicy(name, policy)` 方法创建一个新的 `TrustedTypePolicy` 实例。

   ```javascript
   const policy = trustedTypes.createPolicy('myPolicy', {
       createHTML: (input) => {
           return input; // 这里可以加入额外的验证逻辑
       }
   });
   ```

2. **使用 TrustedTypePolicy**：
   使用创建的策略生成受信任的类型。

   ```javascript
   const safeHTML = policy.createHTML('<div>Hello World</div>');
   document.body.innerHTML = safeHTML; // 安全插入
   ```

3. **配置安全策略**：
   在创建策略时，可以定义不同的方法来处理不同类型的内容，如 `createScript`, `createURL`, 等。

## 示例
以下是 `TrustedTypePolicy` 的基本使用示例：

```javascript
// 创建一个新的 TrustedTypePolicy
const myPolicy = trustedTypes.createPolicy('examplePolicy', {
    createHTML: (input) => {
        // 在这里可以添加检查或清理输入的代码
        return input; // 返回安全的 HTML
    }
});

// 使用策略创建受信任的 HTML
const trustedHTML = myPolicy.createHTML('<p>安全的内容</p>');
document.body.innerHTML = trustedHTML; // 安全插入到 DOM
```

## 说明
### 常见问题
- **未定义的 TrustedTypes**：确保浏览器支持 `Trusted Types`。如果不支持，可能会导致代码无法正常运行。
- **策略名称冲突**：每个策略名称在同一文档中必须唯一，否则会覆盖之前的策略。
- **输入验证**：在创建受信任的类型时，确保对输入进行适当的验证和清理，以避免潜在的安全风险。

### 附加说明
- `TrustedTypes` 仅适用于现代浏览器。对于不支持的浏览器，需要考虑替代方案。
- 可以通过 `trustedTypes.getPolicy(name)` 方法获取现有策略，以便进行调试或验证。

## 一句话总结
`TrustedTypePolicy` 是一种增强 JavaScript 应用程序安全性的工具，通过限制字符串类型来防止跨站脚本攻击。