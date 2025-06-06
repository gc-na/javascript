# [操作系统] C Shell (csh) vmstat 用法: 显示系统虚拟内存统计信息

## 概述
vmstat 命令用于报告虚拟内存、进程、CPU 活动等系统性能信息。它能够帮助用户监控系统的资源使用情况，从而进行性能调优。

## 用法
基本语法如下：
```
vmstat [options] [arguments]
```

## 常用选项
- `-a`：显示活动和非活动的内存。
- `-m`：显示内存的使用情况，包括缓存和缓冲区。
- `-s`：显示系统统计信息。
- `-t`：显示时间戳。

## 常见示例
1. 显示每 2 秒的系统统计信息：
   ```bash
   vmstat 2
   ```

2. 显示所有内存信息：
   ```bash
   vmstat -a
   ```

3. 显示系统统计信息：
   ```bash
   vmstat -s
   ```

4. 显示带时间戳的统计信息：
   ```bash
   vmstat -t 1 5
   ```

## 提示
- 定期监控系统性能可以帮助及时发现问题。
- 使用 `vmstat` 的输出结合其他命令（如 `top` 或 `iostat`）可以获得更全面的系统状态。
- 在高负载情况下，增加采样频率可以帮助更好地分析性能瓶颈。