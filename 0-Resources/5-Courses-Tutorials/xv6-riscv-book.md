---
title: xv6-riscv Book（教学操作系统教材）
short: xv6-riscv Book
summary: Russ Cox 等著的操作系统教材，逐章拆解 xv6-riscv 源码，MIT 6.828/6.1810 指定用书，在线免费读
source: https://mit-pdos.github.io/xv6-riscv-book/
date: 2026-11-19
tags: [risc-v, operating-system, book, education, mit]
links:
  - https://github.com/mit-pdos/xv6-riscv
  - https://pdos.csail.mit.edu/6.1810/
---
# xv6-riscv Book（教学操作系统教材）

> 书全名《xv6: a simple, Unix-like teaching operating system》，作者 Russ Cox、Frans Kaashoek、Robert Morris。原文自述为「a draft text intended for a class on operating systems」，明确要求**与 xv6 源码配合阅读**。

## 核心要点（摘要）

- **作者**：Russ Cox、Frans Kaashoek、Robert Morris
- **定位**：操作系统入门教材，用研究示例内核 xv6 讲清 OS 主要概念
- **配套**：与 [xv6-riscv 源码](xv6-riscv.md) 一一对应，书中带源码超链接
- **使用课程**：MIT 6.828、6.1810（操作系统工程）
- **获取方式**：网页在线免费阅读（本站即在线版），页面顶部附 Source Code 链接
- **许可**：与 xv6 一脉相承的开放教学材料

## 详细内容

### 章节结构（13 章）

| 章节 | 主题 |
|------|------|
| Foreword | 前言与致谢 |
| 1 | Operating system interfaces |
| 2 | Operating system organization |
| 3 | Page tables |
| 4 | Traps and system calls |
| 5 | Page faults |
| 6 | Interrupts and device drivers |
| 7 | Locking |
| 8 | Scheduling |
| 9 | Sleep and wakeup |
| 10 | File system |
| 11 | Logging |
| 12 | Concurrency revisited |
| 13 | Summary |

### 阅读方法

每一章对应 xv6-riscv 内核的一份实现——先读概念，再跳进 `kernel/` 下对应文件对照。页面与课程主页 `pdos.csail.mit.edu/6.1810` 提供配套实验（lab），边读边做效果最好。

### 与 IC 学习的关系

xv6 运行在 RISC-V 上，书里讲的页表、trap、CSR、中断委托、S 模式等，正是处理器设计必须落地的硬件接口。它是「从 RTL 到能跑系统」这条链路上，衔接软件侧需求的关键参照。

## 个人备注

和源码条目配套收录。全书篇幅不大但信息密度高，适合系统性入门 OS，也适合作为 RISC-V 特权架构的实战注解。建议顺序：先读第 1–2 章建立整体框架，再按 3→4→5→6 打通内存与中断主线。

_Last updated: 2026-11-19_
