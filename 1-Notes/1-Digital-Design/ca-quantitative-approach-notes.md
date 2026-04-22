---
source: https://uvj574p5lja.feishu.cn/wiki/M1Vfwgx8liLoIbkhOCAcBcuLnne
date: 2026-04-22
tags: [computer-architecture, cache, virtual-memory, quantitative-approach, study-notes]
---

# Computer Architecture: A Quantitative Approach — 学习笔记

> 经典计算机体系结构教材学习笔记，持续更新中。
> 飞书原文（含完整内容）: https://uvj574p5lja.feishu.cn/wiki/M1Vfwgx8liLoIbkhOCAcBcuLnne

## Overview

《Computer Architecture: A Quantitative Approach》（Hennessy & Patterson）是计算机体系结构领域的圣经级教材。本笔记目前覆盖 Appendix B: Cache and Memory Hierarchy 部分，持续更新。

## 当前笔记进度

### Appendix B: Cache and Memory Hierarchy

#### B.2 Cache Performance
- **B.2.1 Average Memory Access Time and Processor Performance**
  - AMAT = Hit Time + Miss Rate × Miss Penalty
  - AMAT 对 CPU 执行时间的量化影响
- **B.2.2 Miss Penalty and Out-of-Order Execution Processors**
  - 乱序执行处理器中 miss penalty 的重新定义
  - 参考：Figure B.7 列出了本附录所有 cache 公式

#### B.3 Six Basic Cache Optimizations
1. **Larger Block Size** — 降低 miss rate（但增大 miss penalty）
2. **Larger Caches** — 降低 miss rate（但增大 hit time 和功耗）
3. **Higher Associativity** — 降低 miss rate（但增大 hit time）
4. **Multilevel Caches** — 降低 miss penalty（L1 miss → L2 hit）
5. **Priority to Read Misses over Writes** — 降低 miss penalty（写缓冲优化）
6. **Avoiding Address Translation During Indexing** — 降低 hit time（物理索引 vs 虚拟索引）

#### B.4 Virtual Memory
- 四个存储层次问题的再审视
- 快速地址翻译技术（TLB）
- 页大小选择

#### B.5 Protection and Examples of Virtual Memory
- 进程保护机制

#### B.6 Fallacies and Pitfalls
- 常见误区与陷阱

## Key Insights

- Cache 优化的 3C 模型：Compulsory / Capacity / Conflict miss
- 六大优化的本质是分别优化 miss rate / miss penalty / hit time 三个维度
- AMAT 公式是所有 cache 性能分析的基石
- 虚拟存储和 cache 的交互（aliasing 问题）是设计难点

## References

- 书籍：*Computer Architecture: A Quantitative Approach*, 6th Edition, Hennessy & Patterson
- 飞书笔记（完整内容）: https://uvj574p5lja.feishu.cn/wiki/M1Vfwgx8liLoIbkhOCAcBcuLnne

---

*Last updated: 2026-04-22*
