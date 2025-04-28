<!--
Meta Description: # TrustedHTML：JavaScript中的安全HTML处理 ## 简介 TrustedHTML 是一种用于安全处理 HTML 内容的机制，旨在防止跨站脚本（XSS）攻击。它通过提供一种受信任的方式来插入 HTML，从而确保网页的安全性。 ## 文档 ### 目的 TrustedHTML 的...
Meta Keywords: html, trustedhtml, createhtml, xss, input
-->

# TrustedHTML：JavaScript中的安全HTML处理

## 简介
TrustedHTML 是一种用于安全处理 HTML 内容的机制，旨在防止跨站脚本（XSS）攻击。它通过提供一种受信任的方式来插入 HTML，从而确保网页的安全性。

## 文档
### 目的
TrustedHTML 的主要目的是确保在动态生成的 HTML 中不包含恶意代码。它特别适用于需要从不受信任的源插入 HTML 的场景，如用户输入的数据。

### 用法
使用 TrustedHTML 时，开发者可以通过 Trusted Types API 创建受信任的 HTML 对象。这些对象可以安全地插入到 DOM 中，而不必担心 XSS 攻击。

```javascript
// 创建 TrustedHTML 对象
const trustedHTML = TrustedTypes.createPolicy('myPolicy', {
    createHTML: (input) => {
        // 这里可以添加自定义的 HTML 清理逻辑
        return input; // 返回安全的 HTML
    }
});

// 使用 TrustedHTML 对象
const safeHTML = trustedHTML.createHTML('<div>Hello, World!</div>');
document.body.innerHTML = safeHTML; // 安全插入到 DOM 中
```

### 详细信息
- **Trusted Types API**：这是一个防止 XSS 攻击的 API，允许开发者定义受信任的内容类型。创建一个政策（policy）后，开发者可以使用该政策生成受信任的 HTML。
- **createPolicy(name, policy)**：定义一个新的政策，该政策包含用于生成受信任内容的逻辑。
- **createHTML(input)**：生成受信任的 HTML 对象。开发者可以在这里实现额外的安全性检查，例如过滤不安全的标签或属性。

## 示例
### 基本用法
```javascript
// 创建政策
const policy = TrustedTypes.createPolicy('examplePolicy', {
    createHTML: (input) => {
        // 这里可以实现安全检查
        return input.replace(/<script.*?>.*?<\/script>/g, ''); // 移除脚本标签
    }
});

// 使用政策创建安全的 HTML
const safeContent = policy.createHTML('<div>Safe content</div><script>alert("XSS");</script>');
document.body.innerHTML = safeContent; // 只插入安全内容
```

## 解释
- **常见陷阱**：
  - 忘记创建 Trusted Types 政策：在使用 TrustedHTML 前，必须先创建政策，否则将无法使用。
  - 不正确的内容清理逻辑：确保在 `createHTML` 方法中实现有效的内容清理逻辑，以防止不安全的 HTML 被插入。
  
- **注意事项**：
  - TrustedHTML 主要用于保护动态内容插入的场景，对于静态内容，仍然建议使用服务器端渲染。
  - 并非所有浏览器都支持 Trusted Types，开发者需考虑兼容性问题。

## 一句总结
TrustedHTML 是 JavaScript 中一种用于安全插入 HTML 内容的机制，有效防止 XSS 攻击。