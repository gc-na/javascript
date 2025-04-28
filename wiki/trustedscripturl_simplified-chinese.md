<!--
Meta Description: # TrustedScriptURL：JavaScript 中的信任脚本 URL ## 概述 `TrustedScriptURL` 是一种用于安全地处理和存储 JavaScript 脚本 URL 的接口，旨在防止跨站脚本攻击（XSS）和确保代码的安全性。 ## 文档 `TrustedScriptUR...
Meta Keywords: trustedscripturl, url, trusted, types, javascript
-->

# TrustedScriptURL：JavaScript 中的信任脚本 URL

## 概述
`TrustedScriptURL` 是一种用于安全地处理和存储 JavaScript 脚本 URL 的接口，旨在防止跨站脚本攻击（XSS）和确保代码的安全性。

## 文档
`TrustedScriptURL` 是一种受信任的脚本 URL 对象，主要用于在 Web 应用程序中以安全的方式加载和执行脚本。它是 Web 安全上下文的重要组成部分，通常与其他安全技术（如`Trusted Types`）一起使用，以防止恶意代码的执行。

### 目的
通过使用 `TrustedScriptURL`，开发者能够确保只有经过验证和信任的脚本能够被加载，从而增强应用程序的安全性。

### 用法
`TrustedScriptURL` 不能直接实例化，而是通过特定的 API 创建。例如，使用 `TrustedTypes` API 创建受信任的脚本 URL。以下是使用 `TrustedScriptURL` 的步骤：

1. 启用 `Trusted Types`。
2. 使用 `createPolicy` 创建一个政策。
3. 使用该政策生成 `TrustedScriptURL`。

### 详细信息
- `TrustedScriptURL` 对象由 `Trusted Types` API 生成。
- 通过政策，开发者可以定义哪些字符串被视为受信任的脚本 URL。
- 一旦创建，`TrustedScriptURL` 对象便可以被用于动态加载脚本，例如使用 `<script>` 标签或 `eval()` 函数等。

## 示例
以下是如何使用 `TrustedScriptURL` 的简单示例：

```javascript
// 启用 Trusted Types
if (window.TrustedTypes) {
    const policy = TrustedTypes.createPolicy('default', {
        createScriptURL: (input) => {
            // 仅允许特定的 URL
            if (input.startsWith('https://trusted-source.com/')) {
                return input;
            }
            throw new Error('不受信任的脚本 URL');
        }
    });

    // 创建受信任的脚本 URL
    const trustedURL = policy.createScriptURL('https://trusted-source.com/script.js');

    // 使用受信任的脚本 URL
    const scriptElement = document.createElement('script');
    scriptElement.src = trustedURL;
    document.head.appendChild(scriptElement);
}
```

## 说明
- **常见问题**：未正确实现 `Trusted Types` 可能导致安全漏洞，因此务必仔细检查政策的配置。
- **注意事项**：在处理用户输入时，始终要进行严格的验证，以避免引入恶意脚本。
- **浏览器支持**：确保所使用的浏览器支持 `Trusted Types`，以避免兼容性问题。

## 一句话总结
`TrustedScriptURL` 是一种安全的脚本 URL 接口，旨在防止跨站脚本攻击并增强 Web 应用的安全性。