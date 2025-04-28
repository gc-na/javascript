<!--
Meta Description: # FinalizationRegistry：JavaScript中的终结器注册表 ## 摘要 `FinalizationRegistry` 是 JavaScript 中的一个内置对象，用于在对象被垃圾回收时提供回调功能。这使得开发者可以在对象生命周期结束时执行特定的清理操作。 ## 文档 `Fin...
Meta Keywords: finalizationregistry, obj, javascript, const, registry
-->

# FinalizationRegistry：JavaScript中的终结器注册表

## 摘要
`FinalizationRegistry` 是 JavaScript 中的一个内置对象，用于在对象被垃圾回收时提供回调功能。这使得开发者可以在对象生命周期结束时执行特定的清理操作。

## 文档
`FinalizationRegistry` 允许开发者注册一个回调函数，该函数会在指定的对象被垃圾回收后调用。此功能在处理需要显式清理资源的情况时非常有用，尤其是在与底层资源（如 DOM 元素或 Web API）交互时。

### 目的
使用 `FinalizationRegistry` 可以确保在对象不再使用并被垃圾回收时，执行任何必要的清理逻辑，例如释放外部资源或解除事件监听器。

### 用法
创建一个 `FinalizationRegistry` 实例需要一个回调函数作为参数。该回调函数接收一个与被垃圾回收对象相关联的键值。

```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`对象已被清理，持有值为: ${heldValue}`);
});
```

要注册一个对象，使用 `register()` 方法，并传入对象、持有值以及可选的清理提示：

```javascript
const obj = {};
registry.register(obj, '这是一个持有值');
```

当 `obj` 被垃圾回收时，回调会被调用，输出持有值。

## 示例
以下是 `FinalizationRegistry` 的基本用法示例：

```javascript
const registry = new FinalizationRegistry((heldValue) => {
    console.log(`对象已被清理，持有值为: ${heldValue}`);
});

function createObject() {
    const obj = {};
    registry.register(obj, '这是一个持有值');
    return obj;
}

let myObj = createObject();
myObj = null; // 使对象可被垃圾回收
// 可能在某个时刻后，obj 被垃圾回收，并触发回调
```

## 说明
- **常见问题**： 使用 `FinalizationRegistry` 时，回调函数的执行并不保证及时发生。垃圾回收的具体时间取决于 JavaScript 引擎。
- **陷阱**： 不要依赖 `FinalizationRegistry` 来管理重要的应用逻辑，因为其行为可能会受到浏览器的实现差异影响。
- **额外注意**： `FinalizationRegistry` 只能在支持 ECMAScript 2021 的环境中使用。确保你的运行环境支持该特性。

## 一句话总结
`FinalizationRegistry` 允许开发者在对象被垃圾回收时执行特定的清理操作，从而有效管理资源。