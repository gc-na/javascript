<!--
Meta Description: # NodeIterator：JavaScript 中的节点迭代器 ## 概述 NodeIterator 是一种用于遍历 DOM 树中节点的接口，允许开发者以高效的方式访问和处理节点。它是 DOM 树操作中的一个重要工具，特别是在需要对节点进行选择和修改的场景中。 ## 文档 ### 目的 Node...
Meta Keywords: nodeiterator, dom, document, nodefilter, iterator
-->

# NodeIterator：JavaScript 中的节点迭代器

## 概述
NodeIterator 是一种用于遍历 DOM 树中节点的接口，允许开发者以高效的方式访问和处理节点。它是 DOM 树操作中的一个重要工具，特别是在需要对节点进行选择和修改的场景中。

## 文档
### 目的
NodeIterator 提供了一种简单的方式来遍历 DOM 中的节点。与传统的遍历方法相比，NodeIterator 提供了更灵活和高效的选择机制，尤其适用于需要频繁访问节点的场景。

### 用法
NodeIterator 是通过 `document.createNodeIterator()` 方法创建的。该方法接受三个参数：
1. `root`：要开始遍历的根节点。
2. `whatToShow`（可选）：一个整型值，指示应当遍历哪些节点。默认值为 `NodeFilter.SHOW_ALL`。
3. `filter`（可选）：一个 NodeFilter 对象，用于过滤遍历的节点。

#### 创建 NodeIterator
```javascript
const iterator = document.createNodeIterator(
    document.body, // 根节点
    NodeFilter.SHOW_ELEMENT, // 只遍历元素节点
    null // 不使用过滤器
);
```

### 详细信息
NodeIterator 提供了以下主要方法：
- `nextNode()`：返回当前节点并将迭代器移动到下一个节点。如果没有下一个节点，返回 `null`。
- `previousNode()`：返回当前节点并将迭代器移动到前一个节点。如果没有前一个节点，返回 `null`。

可以通过 `iterator.referenceNode` 属性获取当前的参考节点。

## 示例
### 基本用法示例
以下是使用 NodeIterator 遍历 DOM 节点的基本示例：

```javascript
// 创建一个 NodeIterator 来遍历文档中的所有元素节点
const iterator = document.createNodeIterator(
    document.body,
    NodeFilter.SHOW_ELEMENT
);

// 使用 nextNode() 方法遍历所有节点
let currentNode;
while (currentNode = iterator.nextNode()) {
    console.log(currentNode.tagName); // 打印每个元素的标签名
}
```

### 使用过滤器的示例
以下示例展示了如何使用过滤器来选择特定的节点：

```javascript
// 创建一个过滤器，只选择 <div> 元素
const filter = {
    acceptNode(node) {
        return node.nodeName === 'DIV' ? NodeFilter.FILTER_ACCEPT : NodeFilter.FILTER_REJECT;
    }
};

// 创建 NodeIterator
const iterator = document.createNodeIterator(
    document.body,
    NodeFilter.SHOW_ELEMENT,
    filter
);

// 遍历所有 <div> 元素
let divNode;
while (divNode = iterator.nextNode()) {
    console.log(divNode); // 打印每个 <div> 元素
}
```

## 说明
- **常见陷阱**：使用 NodeIterator 时需要注意，`nextNode()` 和 `previousNode()` 方法在到达节点的开始或结束时会返回 `null`。确保在使用这些方法时处理 `null` 返回值。
- **性能注意事项**：NodeIterator 的性能相对较高，尤其是在大型 DOM 树中，使用它可以避免不必要的 DOM 查询。
- **浏览器兼容性**：NodeIterator 在现代浏览器中广泛支持，但在某些旧版本的浏览器中可能存在限制。

## 一句话总结
NodeIterator 是一个强大的工具，允许开发者高效地遍历和操作 DOM 树中的节点。