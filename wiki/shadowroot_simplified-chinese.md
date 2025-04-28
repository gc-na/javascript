<!--
Meta Description: # ShadowRoot：JavaScript 中的影子 DOM ## 概述 `ShadowRoot` 是 Web Components 规范的一部分，它允许开发者在元素中创建封闭的 DOM。通过使用影子 DOM，开发者可以将样式和结构封装在组件内部，避免全局样式的冲突并提高可重用性。 ## 文档 ...
Meta Keywords: dom, shadowroot, const, document, shadow
-->

# ShadowRoot：JavaScript 中的影子 DOM

## 概述
`ShadowRoot` 是 Web Components 规范的一部分，它允许开发者在元素中创建封闭的 DOM。通过使用影子 DOM，开发者可以将样式和结构封装在组件内部，避免全局样式的冲突并提高可重用性。

## 文档
### 目的
`ShadowRoot` 的主要目的是提供一个独立的 DOM 树，允许开发者创建封装的组件。这样，组件的内部实现不会影响外部页面的样式和行为。

### 用法
要创建一个 `ShadowRoot`，可以使用元素的 `attachShadow` 方法。此方法接受一个配置对象，指定影子 DOM 的模式（如 `open` 或 `closed`）：

```javascript
let shadow = element.attachShadow({ mode: 'open' });
```

- **mode**: 
  - `open`: 允许外部代码访问影子 DOM。
  - `closed`: 不允许外部代码访问影子 DOM。

### 详细说明
- 当你调用 `attachShadow` 时，它将返回一个 `ShadowRoot` 实例。
- 通过 `ShadowRoot`，你可以向影子 DOM 添加元素、样式等，构建完整的组件结构。
- 影子 DOM 使得组件的样式不受外部 CSS 的影响，并且可以通过 CSS 自定义属性来实现主题化。
- 影子 DOM 的内容仅限于影子树内，不会被外部选择器选择。

## 示例
### 创建一个简单的影子 DOM

```javascript
const host = document.createElement('div');
const shadow = host.attachShadow({ mode: 'open' });

const para = document.createElement('p');
para.textContent = '这是影子 DOM 中的段落。';
shadow.appendChild(para);

document.body.appendChild(host);
```

### 使用样式封装

```javascript
const host = document.createElement('div');
const shadow = host.attachShadow({ mode: 'open' });

const style = document.createElement('style');
style.textContent = `
  p {
    color: blue;
    font-weight: bold;
  }
`;
shadow.appendChild(style);

const para = document.createElement('p');
para.textContent = '这是影子 DOM 中的段落。';
shadow.appendChild(para);

document.body.appendChild(host);
```

## 说明
- **常见陷阱**：使用 `closed` 模式时，外部代码无法通过 JS 访问影子 DOM，这可能会导致调试困难。
- **样式冲突**：虽然影子 DOM 可以避免样式冲突，但如果使用了全局选择器，仍可能影响影子 DOM 中的元素。
- **兼容性**：在老旧浏览器上，影子 DOM 可能不被支持，建议使用 Polyfill 来确保兼容性。

## 一句话总结
`ShadowRoot` 是 JavaScript 中用于创建封闭的影子 DOM 的机制，提供更好的组件封装和样式隔离。