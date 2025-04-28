<!--
Meta Description: # ValidityState 在 JavaScript 中的使用 ## 摘要 `ValidityState` 是一个接口，用于表示 HTML 表单元素的有效性状态。它提供了一组属性，帮助开发者判断表单字段是否符合特定的验证规则。 ## 文档 `ValidityState` 接口是由浏览器实现的，用...
Meta Keywords: validitystate, 则返回, true, validity, form
-->

# ValidityState 在 JavaScript 中的使用

## 摘要
`ValidityState` 是一个接口，用于表示 HTML 表单元素的有效性状态。它提供了一组属性，帮助开发者判断表单字段是否符合特定的验证规则。

## 文档
`ValidityState` 接口是由浏览器实现的，用于描述表单元素的有效性。每个输入元素都有一个 `validity` 属性，该属性返回一个 `ValidityState` 对象。这个对象包含多个布尔值属性，指示字段是否有效或无效。

### 目的
通过 `ValidityState`，开发者可以快速检查表单字段的有效性，提供用户友好的表单验证反馈。

### 用法
`ValidityState` 主要用于表单验证。可以通过访问 DOM 元素的 `validity` 属性来获取其 `ValidityState` 对象，然后检查其属性。

### 属性
- `valid`: 如果表单元素的值有效，则返回 `true`。
- `valueMissing`: 如果元素的值是必需的但未提供，则返回 `true`。
- `typeMismatch`: 如果输入值不符合元素的类型要求，则返回 `true`。
- `tooLong`: 如果输入的值超过了允许的最大长度，则返回 `true`。
- `tooShort`: 如果输入的值小于允许的最小长度，则返回 `true`。
- `rangeUnderflow`: 如果输入的值低于允许的最小值，则返回 `true`。
- `rangeOverflow`: 如果输入的值高于允许的最大值，则返回 `true`。
- `patternMismatch`: 如果输入的值不符合指定的模式，则返回 `true`。
- `stepMismatch`: 如果输入的值不符合步骤要求，则返回 `true`。

## 示例
```html
<form id="myForm">
  <input type="email" id="email" required>
  <button type="submit">提交</button>
</form>

<script>
  const form = document.getElementById('myForm');
  const emailInput = document.getElementById('email');

  form.addEventListener('submit', function(event) {
    if (!emailInput.validity.valid) {
      if (emailInput.validity.valueMissing) {
        alert('邮箱是必填项');
      } else if (emailInput.validity.typeMismatch) {
        alert('请输入有效的邮箱地址');
      }
      event.preventDefault(); // 阻止表单提交
    }
  });
</script>
```

## 解释
在使用 `ValidityState` 时，有一些常见的陷阱：
- 确保在表单提交时检查有效性，而不是在输入时。
- 不同浏览器可能对某些输入类型的支持有所不同，因此需要进行充分的测试。
- 不要依赖于浏览器的默认错误信息，提供自定义反馈可以提升用户体验。

## 一句话总结
`ValidityState` 接口用于检查 HTML 表单元素的有效性状态，帮助开发者实现高效的表单验证。