---
source: null
date: 2026-06-09
tags: [computer-architecture, survey, cpu, gpu, dsa, memory-hierarchy, chiplet]
---

# 计算机体系结构「森林导览」

> 一篇面向研一新生的计算机体系结构综述——"地图式"体例，从通用处理器到新兴范式

## 基本信息

| 项目 | 详情 |
|------|------|
| **页数** | 87 页 |
| **定位** | 研一新生入学级综述 |
| **体例** | 地图式：每章先讲分支解决的问题 + 核心张力，再点锚点文献 |
| **证据分级** | 奠基★ / 必读★★ / 有争议† / 推测性⚠ |

## 内容架构

### 第一圈：通用处理器

| 子主题 | 核心内容 |
|--------|----------|
| 指令集架构 (ISA) | CISC vs RISC, RISC-V 开放 ISA |
| 微架构 | 超标量、乱序执行、Tomasulo、分支预测、超线程 |
| 存储层次 | 多级 Cache、局部性原理、虚拟内存、TLB、大页 |
| 多核与一致性 | MESI、内存一致性模型 (SC/TSO/弱序)、片上网终 (NoC) |
| 数据并行 & GPU | CUDA、SIMT、Tensor Core |

### 第二圈：领域专用架构 (DSA)

| 子主题 | 核心内容 |
|--------|----------|
| AI/深度学习加速器 | 脉动阵列、数据流、稀疏加速 |
| LLM/Transformer 加速 | KV Cache、FlashAttention、PagedAttention、推测性解码 |
| 可重构计算 | FPGA、粗粒度重构 (CGRA) |
| 其他领域加速 | 图计算、数据库、基因组 |

### 第三圈：打破瓶颈

| 子主题 | 核心内容 |
|--------|----------|
| 近存/存内计算 | 内存墙、PIM、HBM、CXL、OpenCAPI |
| 新型存储与内存解耦 | 内存池化、CXL.mem |
| 互连与集成 | Chiplet、先进封装、UCIe、D2D 互联 |
| 网络与 I/O 卸载 | SmartNIC、DPU (BlueField)、RDMA |

### 第四圈：物理与安全约束

| 子主题 | 核心内容 |
|--------|----------|
| 微架构安全 | Spectre/Meltdown、RowHammer、侧信道、机密计算 (SGX/TDX/SEV/CCA) |
| 可靠性 | 软错误、老化、变异、近似计算 |
| 能效与数据中心 | Dark Silicon、PUE、Dennard Scaling 终结 |

### 远景林：新兴范式

| 子主题 | 核心内容 |
|--------|----------|
| 神经形态计算 | Loihi、TrueNorth、SNN、忆阻器 |
| 量子计算 | Surface Code、纠错、超导 |
| 光子/模拟计算 | 光子矩阵乘法、Lightmatter、Lightelligence |

## 与现有资源关联

- **Computer Architecture: A Quantitative Approach**（仓库 1-Books）— 体系结构经典教材，这篇森林导览可作为快速索引和知识地图配合使用

## PDF 原文

见本目录同名 PDF 文件。

_Last updated: 2026-06-09_
