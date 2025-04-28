<!--
Meta Description: # HTMLBaseElement：JavaScript中的基础元素 ## 概述 `HTMLBaseElement` 是一个用于表示 HTML `<base>` 标签的接口。该元素主要用于指定相对 URL 的基准 URL，以便在文档中使用的所有相对链接都能正确解析。 ## 文档 `HTMLBaseE...
Meta Keywords: html, base, url, href, htmlbaseelement
-->

# HTMLBaseElement：JavaScript中的基础元素

## 概述
`HTMLBaseElement` 是一个用于表示 HTML `<base>` 标签的接口。该元素主要用于指定相对 URL 的基准 URL，以便在文档中使用的所有相对链接都能正确解析。

## 文档
`HTMLBaseElement` 接口继承自 `HTMLElement`，并提供了两个主要属性：

- `href`：一个字符串，代表文档中所有相对 URL 的基准 URL。
- `target`：一个字符串，定义了在何处打开链接（如 `_blank`、`_self` 等）。

### 目的
`HTMLBaseElement` 使开发者能够设置文档中相对链接的基准，确保所有相对路径链接都能被正确解析和加载。

### 用法
在 HTML 文档中，可以通过如下方式使用 `<base>` 标签：

```html
<base href="https://www.example.com/" target="_blank">
```

在 JavaScript 中，可以通过 `document.getElementsByTagName('base')[0]` 来访问和修改该元素的属性。

## 示例
### 示例 1：设置基准 URL
```html
<!DOCTYPE html>
<html>
<head>
    <base href="https://www.example.com/" target="_blank">
    <title>示例页面</title>
</head>
<body>
    <a href="page.html">前往新页面</a>
</body>
</html>
```
在这个示例中，点击链接将会打开 `https://www.example.com/page.html`。

### 示例 2：使用 JavaScript 修改基准 URL
```html
<!DOCTYPE html>
<html>
<head>
    <base id="baseElement" href="https://www.example.com/" target="_self">
    <title>示例页面</title>
    <script>
        function changeBase() {
            var base = document.getElementById('baseElement');
            base.href = "https://www.anotherexample.com/";
        }
    </script>
</head>
<body>
    <a href="page.html">前往新页面</a>
    <button onclick="changeBase()">更改基准 URL</button>
</body>
</html>
```
在这个示例中，点击按钮会更改基准 URL，从而影响后续的链接解析。

## 说明
使用 `HTMLBaseElement` 时，有一些常见的注意事项：

- **只允许一个 `<base>` 标签**：在一个 HTML 文档中，只能有一个 `<base>` 标签。如果有多个标签，浏览器只会使用第一个。
- **位置影响**：`<base>` 标签必须在 `<head>` 部分中定义，且在任何其他链接或脚本之前，以确保所有相对链接都能正确解析。
- **跨域问题**：如果基准 URL 指向不同的域，可能会导致 CORS（跨源资源共享）问题，尤其是在尝试通过 JavaScript 访问外部资源时。

## 一句话总结
`HTMLBaseElement` 使开发者能够设置 HTML 文档中所有相对链接的基准 URL，从而确保它们正确解析。