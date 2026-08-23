---
source: https://github.com/simplex-micro/riscv-vector-primer
date: 2026-08-23
tags: [risc-v, rvv, vector, matrix-extension, vector-processor, cpu-design, compiler, gemm, ai, architecture]
links:
  - https://github.com/simplex-micro/riscv-vector-primer
  - https://mp.weixin.qq.com/s?__biz=MjM5NDczOTA4NQ==&mid=2447904731&idx=1&sn=5f64137c90261c786a381ccccde5f61a
---

# RISC-V Vector Primer (RVV 1.0 指南)

> 一本面向**硬件架构师、编译器工程师与嵌入式/边缘 AI 开发者**的 RVV 实践指南。核心主张：把 RISC-V Vector Extension 从「一堆术语」翻译成「可被工程师操作的心智模型」，并延伸到新兴的 Matrix Extension。

- **仓库**：https://github.com/simplex-micro/riscv-vector-primer
- **性质**：开放技术书（非软件项目），内容集中在 Markdown 章节与配图，无构建系统/测试脚本/源码目录。README 建议直接浏览章节文件，从第一章开始读。

## 项目核心思想

**RVV 的核心野心：让软件摆脱固定硬件宽度，让同一套二进制能够在 128 / 256 / 512 甚至更宽的实现上自然伸缩。**

传统 SIMD（MMX/SSE/AVX/AVX-512）把硬件宽度写进软件假设：每次扩展带来新寄存器宽度、新编码、新指令组合，硬件升级后软件要吃满新宽度往往要重新编译或运行时选择代码路径。

RVV 更锋利：
- ISA 描述「对一组元素执行操作」，硬件实际一次容纳多少元素由实现决定；
- 软件通过 `vsetvl` 系列指令**动态询问并设置**当前可处理元素数。

> 一句话心智模型：SIMD 是固定宽度的尺子，一次量多少由尺子长度决定；**RVV 是一套测量协议，硬件告诉软件本轮能处理多长，软件按这个长度推进循环**。

## 章节结构

| 章节 | 内容 |
|------|------|
| chapter-01 | RVV 概念、SIMD 对比、strip mining、chaining |
| chapter-02 | RVV 核实现、512-bit VRF、lane、port pressure |
| chapter-03 | SEW、LMUL、VL、vtype、掩码、vstart |
| chapter-04 | load/store、compute、mask、permutation 指令族 |
| chapter-05 | GEMM、MAC pipeline、性能分析、确定性执行 |
| chapter-06 | 从一维向量到二维矩阵 tile 与 Matrix Extension |

## 关键概念（VL / SEW / LMUL）

- **SEW**：单个元素宽度（8/16/32/64 bit）
- **VLEN**：单个向量寄存器的硬件宽度（芯片实现固定）
- **LMUL**：把多个向量寄存器逻辑拼成一组，牺牲寄存器数量换取更长向量
- **VL**：当前指令真正参与计算的元素数
- **VLMAX**：当前 SEW 与 LMUL 下，一组向量寄存器最多容纳多少元素

核心机制 `vsetvli`：同时设置 VL 与 vtype。编译器把剩余元素数放进 `a0`，硬件给出这次最合适的 VL——循环不硬编码「512 位能放 16 个 int32」，也不用知道目标机器实际 VLEN。这也让「尾巴处理」变得自然：VL 让最后一轮自动变短，循环结构仍然统一。

## 硬件视角：512-bit VPU 的真实代价

典型 RVV 核 = 标量 CPU + 向量处理单元 VPU。CPU 负责取指/提交/CSR 状态等控制逻辑；VPU 拥有向量寄存器文件（VRF）、向量整数/浮点/掩码/置换/load-store 单元。

- **lane 切分**：512-bit VLEN / 4 lanes，每个 lane 处理 128-bit 切片，寄存器文件按 lane 切分，局部连线变短、时钟频率更易收敛。
- **chaining**：前一条指令第一批结果刚出来，后一条依赖指令就能立刻消费，无需等整个向量写回 VRF——显著隐藏长向量延迟。

> 项目核心判断：高性能 RVV 实现需要**调度、端口规划、旁路路径和异常语义共同配合**，向量性能来自流水线、寄存器文件、内存带宽与编译器循环形态的合奏。

## 指令与编译器：内存形态决定性能

指令分四类：memory / compute / mask / permutation。内存模式是关键成本模型：
- **unit-stride**：连续访问，最易跑满带宽
- **strided**：固定步长，适合列访问
- **indexed**：任意偏移，表达力强但硬件冲突多
- **segment**：AoS → SoA，适合 RGB/复数/结构数组

置换指令把「不规则性从内存搬进寄存器」：`vrgather`/`vslideup`/`vslidedown`/`vcompress` 让程序先用连续 load 高效取数，再在 VRF 内重排。

## 从向量到矩阵（下一层抽象）

矩阵天然二维，RVV 向量寄存器是一维抽象。第六章提出的路线：
- **RVV 承担**：控制流、数据搬运、layout transform、不规则与混合负载
- **Matrix Extension 承担**：tile register file、二维 PE array、tile-level 矩阵乘加、降低指令开销、提高数据复用

符合现代处理器趋势：标量管控制，向量管通用数据并行，矩阵单元管高度规则密集计算。

## 为什么放进 IC 学习库

RVV 是当前 CPU/AI 芯片设计的关键指令集扩展，直接衔接你的研究方向（AI 推理系统、加速器架构、数字 IC）。这本 Primer 相比正式 ISA 规格书更「可操作」，能把 VLEN/LMUL/vtype/vsetvl 等术语落到「编译器如何生成循环、处理器如何组织寄存器文件、AI 与矩阵计算如何获得吞吐」三层真实问题上。

## 配套中文解读

RISC-V 中文社区（公众号「RVV Primer」）于 2026-08-21 发布过一篇对本书的解读，从「规格书翻译器」视角逐章梳理，含推荐阅读路径与关键代码片段：
- 微信公众号文章：https://mp.weixin.qq.com/s?__biz=MjM5NDczOTA4NQ==&mid=2447904731&idx=1&sn=5f64137c90261c786a381ccccde5f61a

_Last updated: 2026-08-23_