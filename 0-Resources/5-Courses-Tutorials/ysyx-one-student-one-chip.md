---
source: https://ysyx.oscc.cc
date: 2026-07-28
tags: [risc-v, processor, cpu-design, rtl, verilog, chisel, tapeout, open-source-eda, computer-architecture, education]
links:
  - https://ysyx.oscc.cc/docs/2205/schedule-origin.html
  - https://space.bilibili.com/2107852263
  - https://github.com/PKUFlyingPig/cs-self-learning/blob/master/docs/%E4%BD%93%E7%B3%BB%E7%BB%93%E6%9E%84/YSYX.md
---

# 一生一芯（One Student One Chip）

> 由中国科学院大学 / 中国科学院计算技术研究所于 2019 年发起的 chip 设计人才培养计划。指导学生**从零设计一款 RISC-V 处理器芯片**，在其上运行自己开发的系统软件与演示程序，并通过开源 EDA 工具与开源 PDK 完成物理设计流程、最终流片。

## 核心定位

- **全链条设计能力**：覆盖计算机系统全栈抽象层——从应用程序、运行时环境、简易操作系统、指令集，到处理器微结构设计、RTL 开发、逻辑综合、布局布线、时序分析，最终生成晶体管级可流片 GDSII 版图。
- **开放 + 公益**：面向全球芯片设计爱好者，不限学校、专业、年级，全年开放报名（报名与学习均免费），随到随学，可零基础起步。
- **免费流片机会**：达成指定学习目标（完成 B 阶段）的在校生，可获得免费或低成本流片指标，带着自己设计的芯片毕业。
- **规模**：累计报名已逾 12000 人，覆盖全球 900 余所高校及科研院所。

## 学习路径概览（以 2205 期为例）

| 阶段 | 关键产出 |
|------|----------|
| 预学习阶段 | Linux 环境、Verilator 仿真、数字电路基础、C 语言复习（PA1） |
| 基础阶段 | 简易调试器、支持 RV64IM 的 NEMU 指令集模拟器、单周期处理器 |
| 进阶阶段 | 异常/中断、系统调用、总线与外设、SoC 计算机系统、Cache、流水线 |
| 达成流片指标 | 接入 SoC，获得流片机会 |
| 专家阶段 | 多道程序、分页虚拟内存、xv6 / Linux 运行、双发射、乱序执行、分支预测等 |

学习始于 C 语言与数字电路基础，逐步引导实现可运行「超级玛丽」的 RISC-V 指令集模拟器 NEMU，并在其辅助下完成自己的处理器设计，最终在自己设计的 CPU 上运行 RT-Thread 乃至 Linux。新版讲义引入更细的阶段划分（FEDCBA），学习坡度更友好。

## 关键资源

- **课程官网 / 讲义**：https://ysyx.oscc.cc（项目概述、学习规划、实验指导）
- **B 站视频号「一生一芯」**：https://space.bilibili.com/2107852263
- **社区学习路线整理**（含 YSYX 说明）：https://github.com/PKUFlyingPig/cs-self-learning/blob/master/docs/体系结构/YSYX.md

## 为什么放进 IC 学习库

「一生一芯」是把前面分散的知识点（RISC-V 指令集、RTL、综合、时序、流片）串成一条**端到端实践主线**的最佳项目化入口，特别适合想从「读懂芯片」走向「造出芯片」的学习者。

_Last updated: 2026-07-28_
