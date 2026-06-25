---
source: https://mlc.ai/modern-gpu-programming-for-mlsys/
date: 2026-06-25
tags: [gpu, blackwell, gemm, flash-attention, tirx, kernel-optimization, tma, warp-specialization, hardware-architecture]
---

# Modern GPU Programming For MLSys

> MLC.ai 出品，基于 Blackwell 架构的现代 GPU Kernel 编程实战教材，聚焦硬件底层与极致性能优化。

## 基本信息

| 项目 | 详情 |
|------|------|
| **作者** | MLC.ai (Tianqi Chen 团队) |
| **来源** | CMU Machine Learning Systems 课程系列 |
| **编程模型** | TIRx Python DSL（贴近硬件的底层编程接口） |
| **目标架构** | NVIDIA Blackwell (B200/B100) |
| **核心案例** | GEMM 优化 + FlashAttention 4 |

## 核心要点（摘要）

从硬件架构视角理解现代 GPU：Blackwell 引入 TMA（Tensor Memory Accelerator）、更丰富的内存层级、新的协作模式（2-CTA Cluster）。本书提供从硬件模型到 Kernel 实现的全链路方法论，适合理解 GPU 微架构与编程模型的对应关系。

## 目录结构

### Part I: Understanding the GPU
GPU 整体组织、编写快速 Kernel 的通用方法、数据布局、异步内存操作与协调机制。

### Part II: TIRx Overview
TIRx 语言关键元素，后续所有代码示例的基础。

### Part III: GEMM — Tiled to SOTA
分块 GEMM → TMA Pipelining → Persistent Scheduling → Warp Specialization → 2-CTA Clusters。

### Part IV: Flash Attention 4
完整 Attention Kernel：双 MMA + Softmax、Online-Softmax Rescaling、Causal Masking、GQA。

### Reference
TIRx 语言参考与编译器内部实现。

## 硬件特性覆盖

| Blackwell 特性 | 用途 | 所在章节 |
|---------------|------|----------|
| **TMA (Tensor Memory Accelerator)** | 异步数据搬运，减少指令开销 | Part III |
| **SMEM 层级** | 共享内存与分布式共享内存 | Part I |
| **Warp Specialization** | 生产者-消费者流水线 | Part III |
| **2-CTA Cluster** | 跨 CTA 协作共享 SMEM | Part III |
| **异步执行模型** | 计算与数据搬运重叠 | Part I/III |

## 与 IC 设计学习的关联

本书从「使用方视角」深入 GPU 微架构特性（TMA、Cluster、SMEM 层级），对理解 GPU 硬件设计动机和加速器架构（如 AI 专用加速器中的类似设计模式）有直接参考价值。配合 ysyx 项目中的 RISC-V 处理器设计，可建立「软件优化 ↔ 硬件特性」的双向理解。

_Last updated: 2026-06-25_
