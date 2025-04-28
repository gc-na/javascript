<!--
Meta Description: # Atomics：JavaScript 中的原子操作 ## 概述 Atomics 是 JavaScript 中用于并发编程的一组静态方法，允许在共享内存中进行原子操作。它提供了一种机制，以确保在多线程环境中对内存的操作是安全的，避免了数据竞争和不一致的问题。 ## 文档 ### 目的 Atomic...
Meta Keywords: atomics, typedarray, index, value, 并返回新的值
-->

# Atomics：JavaScript 中的原子操作

## 概述
Atomics 是 JavaScript 中用于并发编程的一组静态方法，允许在共享内存中进行原子操作。它提供了一种机制，以确保在多线程环境中对内存的操作是安全的，避免了数据竞争和不一致的问题。

## 文档
### 目的
Atomics 的主要目的是支持在 Web Workers 和其他多线程环境中进行安全的原子操作。它确保对共享内存的操作不会被其他线程中断，从而提供了一种安全、有效的方式来处理并发数据。

### 用法
Atomics 主要用于与 `SharedArrayBuffer` 对象一起使用。`SharedArrayBuffer` 允许多个线程共享相同的内存区域，而 Atomics 提供了一系列方法来安全地操作这些区域。

### 主要方法
- `Atomics.add(typedArray, index, value)`：将指定位置的值增加给定的值，并返回新的值。
- `Atomics.sub(typedArray, index, value)`：将指定位置的值减少给定的值，并返回新的值。
- `Atomics.and(typedArray, index, value)`：对指定位置的值进行按位与操作，并返回新的值。
- `Atomics.or(typedArray, index, value)`：对指定位置的值进行按位或操作，并返回新的值。
- `Atomics.xor(typedArray, index, value)`：对指定位置的值进行按位异或操作，并返回新的值。
- `Atomics.exchange(typedArray, index, value)`：将指定位置的值替换为给定的值，并返回旧的值。
- `Atomics.compareExchange(typedArray, index, expectedValue, newValue)`：如果指定位置的值等于预期值，则将其替换为新值，并返回旧值。
- `Atomics.wait(typedArray, index, value, timeout)`：使当前线程等待，直到指定位置的值不再等于给定的值，或超时。
- `Atomics.notify(typedArray, index, count)`：唤醒等待在指定位置的线程。

## 示例
以下是 Atomics 的基本使用示例：

```javascript
// 创建共享内存
const sharedBuffer = new SharedArrayBuffer(4); // 4 字节
const int32View = new Int32Array(sharedBuffer);

// 使用 Atomics 方法进行原子加法
Atomics.add(int32View, 0, 10);
console.log(Atomics.load(int32View, 0)); // 输出 10

// 使用 Atomics 方法进行原子比较和交换
const oldValue = Atomics.compareExchange(int32View, 0, 10, 20);
console.log(oldValue); // 输出 10
console.log(Atomics.load(int32View, 0)); // 输出 20
```

## 说明
使用 Atomics 时需要注意以下几点：

- Atomics 方法只能用于 `TypedArray`，如 `Int32Array`、`Float64Array` 等，并且它们必须是基于 `SharedArrayBuffer` 的。
- Atomics 的操作是原子的，这意味着在一个线程执行 Atomics 操作时，其他线程无法干扰该操作。
- 在使用 `Atomics.wait` 和 `Atomics.notify` 方法时，确保正确管理线程的等待和唤醒逻辑，以避免死锁。

## 一句话总结
Atomics 提供了一组原子操作方法，用于在 JavaScript 的多线程环境中安全地处理共享内存。