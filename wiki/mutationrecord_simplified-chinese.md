<!--
Meta Description: # MutationRecord: JavaScript 中的变更记录对象 ## 概述 `MutationRecord` 是一个 JavaScript 对象，用于描述 DOM 变更的详细信息。它在监控和处理 DOM 变更时非常重要，通常与 `MutationObserver` 一起使用，以便开发者可...
Meta Keywords: mutationrecord, dom, mutationobserver, attributes, mutation
-->

# MutationRecord: JavaScript 中的变更记录对象

## 概述
`MutationRecord` 是一个 JavaScript 对象，用于描述 DOM 变更的详细信息。它在监控和处理 DOM 变更时非常重要，通常与 `MutationObserver` 一起使用，以便开发者可以捕捉和响应对 DOM 的修改。

## 文档
### 目的
`MutationRecord` 主要用于存储有关 DOM 变更的信息，包括节点的添加、删除和属性的修改。这使得开发者能够有效地追踪和处理这些变化，尤其在构建动态用户界面时。

### 用法
`MutationRecord` 是由 `MutationObserver` 生成的，开发者通常不需要手动创建 `MutationRecord` 实例。它包含以下属性：

- **type**: 变更的类型，可能的值有 `"childList"`、`"attributes"` 和 `"characterData"`。
- **target**: 发生变更的节点。
- **addedNodes**: 一个 `NodeList`，包含所有被添加的节点。
- **removedNodes**: 一个 `NodeList`，包含所有被移除的节点。
- **previousSibling**: 变更的节点之前的兄弟节点。
- **nextSibling**: 变更的节点之后的兄弟节点。
- **attributeName**: 如果变更类型是 `"attributes"`，该属性包含被修改的属性名称；否则为 `null`。
- **attributeNamespace**: 如果变更类型是 `"attributes"`，该属性包含被修改属性的命名空间；否则为 `null`。

### 示例
以下示例展示了如何使用 `MutationObserver` 和 `MutationRecord` 来监控 DOM 变更：

```javascript
// 创建一个观察者实例
const observer = new MutationObserver((mutationsList) => {
    for (const mutation of mutationsList) {
        if (mutation.type === 'childList') {
            console.log('子节点发生了变化:', mutation);
        } else if (mutation.type === 'attributes') {
            console.log('属性发生了变化:', mutation);
        }
    }
});

// 配置观察者以监控目标节点
const targetNode = document.getElementById('myElement');
const config = { attributes: true, childList: true, subtree: true };

// 开始观察
observer.observe(targetNode, config);

// 修改目标节点以触发变更
targetNode.setAttribute('data-example', '新值');
targetNode.appendChild(document.createElement('div'));
```

### 解释
在使用 `MutationRecord` 时，开发者需注意以下几点：

- **性能问题**: 观察器可以监控大量变更，但过多的变更可能会导致性能下降。应谨慎配置观察的目标和变更类型。
- **异步处理**: `MutationObserver` 的回调是异步执行的，因此在处理变更时，要考虑到这一点，确保不会造成状态不一致。
- **节点的动态变化**: 在调用 `observe` 方法后，如果目标节点被移除，则观察将停止。务必在适当的时机调用 `disconnect` 方法以停止观察。

## 一句话总结
`MutationRecord` 是用于描述 DOM 变更的对象，通常在使用 `MutationObserver` 监控 DOM 变化时生成和使用。