---
title: xv6-riscv（MIT 教学操作系统）
short: xv6-riscv
summary: MIT PDOS 出品的 RISC-V 教学操作系统，Unix v6 的 ANSI C 重实现，配套 6.1810 课程，10.8k 星
source: https://github.com/mit-pdos/xv6-riscv
date: 2026-11-19
tags: [risc-v, operating-system, teaching, c, open-source, mit]
links:
  - https://pdos.csail.mit.edu/6.1810/
  - https://mit-pdos.github.io/xv6-riscv-book/
---
# xv6-riscv（MIT 教学操作系统）

> Dennis Ritchie 与 Ken Thompson 的 Unix Version 6 的现代重实现，用 ANSI C 编写，目标平台是多核 RISC-V。它是 MIT 操作系统课程 6.1810 的教学用系统，**主要目的是简化与讲清概念，而非堆砌新特性**。

## 核心要点（摘要）

- **定位**：教学操作系统（teaching OS），不是生产级内核；代码简洁可读，专为配合课程与教材设计
- **血缘**：复刻 Unix v6 的结构与风格，灵感来自 John Lions 的《Commentary on UNIX 6th Edition》
- **语言 / 平台**：ANSI C 实现，面向 modern RISC-V multiprocessor（RV64）
- **维护方**：MIT PDOS（Parallel and Distributed Operating Systems group）
- **人气**：约 10.8k stars / 4.6k forks / 1700+ commits（截至收录时）
- **许可**：BSD 系列开源许可（见仓库 LICENSE）

## 详细内容

### 操作系统子系统（源码逐章可对照）

- 进程与内存管理：页表、trap 与系统调用、缺页
- 中断与设备驱动、锁、调度、sleep/wakeup
- 文件系统与日志（logging）
- 多处理器支持（MP）：早期版本由 Cliff Frey、Xiao Yu 贡献

### 构建与运行

需要 RISC-V newlib 工具链（`riscv-gnu-toolchain`）与编译了 `riscv64-softmmu` 的 QEMU，加入 PATH 后执行 `make qemu` 即可启动；仓库提供 `test-xv6.py` 做回归测试。

主要贡献者包括 Russ Cox（上下文切换、锁）、Nickolai Zeldovich、Austin Clements 等；错误与建议由 Frans Kaashoek 和 Robert Morris 接收。

### 配套资源

- 课程主页：https://pdos.csail.mit.edu/6.1810/ （含实验作业与在线资料）
- 配套教材：[xv6-riscv Book](xv6-riscv-book.md) — 逐章讲解这份源码

## 个人备注

xv6 是理解「CPU 之上第一层软件如何运转」的最佳最小样本：进程、页表、中断、锁、文件系统都有清晰可读的实现。对于做 RISC-V 处理器的人，它能和「一生一芯」形成闭环——自己设计的核跑通 xv6，才算真正把指令集、特权级、CSR、中断控制器这些纸面概念串起来。建议与教材对照阅读，边读源码边打断点。

_Last updated: 2026-11-19_
