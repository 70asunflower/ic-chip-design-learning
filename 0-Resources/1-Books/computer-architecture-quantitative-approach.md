---
title: "Computer Architecture: A Quantitative Approach"
short: CA: 量化研究方法
summary: Hennessy & Patterson 体系结构经典教材（含学习笔记链接）
source: https://www.elsevier.com/books/computer-architecture/hennessy/978-0-12-811905-1
date: 2026-03-31
tags: [book, computer-architecture, risc-v, cache, virtual-memory]
---
# Computer Architecture: A Quantitative Approach（第 6 版）

## 核心要点（摘要）

计算机体系结构领域的经典教材（Hennessy & Patterson）。第 6 版把 ISA 换成 RISC-V，
并新增领域专用体系结构（DSA）章节。全书的方法是「先量化再设计」——每个设计选择
都要求给出性能 / 功耗 / 面积的依据，而不是凭直觉。

## 详细内容

- 主线：量化设计方法 → 存储层次 → 指令级并行 → 数据级并行 → 线程级并行 → DSA
- 附录 B（Cache and Memory Hierarchy）是缓存部分的完整推导，常被单独当参考手册用
- 第 6 版新增 RISC-V 与 DSA（含 TPU 类加速器）内容，与 5 版差异较大

## 个人备注

配套中文学习笔记见
[CA: Quantitative Approach 学习笔记](../../1-Notes/1-Digital-Design/ca-quantitative-approach-notes.md)，
目前覆盖附录 B 的 Cache 与 Memory Hierarchy，持续更新。

_Last updated: 2026-04-22_
