---
source: https://github.com/stnolting/neorv32
date: 2026-05-29
tags: [risc-v, vhdl, soc, fpga, open-source]
---

# NEORV32 — RISC-V SoC

## 核心要点（摘要）

NEORV32 是一个完全用 VHDL 编写的可定制 RISC-V 微控制器 SoC，目标是成为 FPGA 上的辅助控制器或独立微控制器。零外部依赖、平台无关、开箱即用，适合 RISC-V 入门和实际项目开发。

## 详细内容

### 处理器核心

- 基础 ISA：RV32I / RV32E，可选扩展：M、A、C、B、U、X
- 支持大量标准扩展：位操作（Zba/Zbb/Zbc/Zbs）、加密（Zkn/Zks 系列）、浮点（Zfinx，使用整数寄存器）
- 支持 SMP 双核配置
- 自定义指令单元（CFU）
- RISC-V Architecture ID 19，通过官方 RISC-V ACT 认证测试

### SoC 外设

- JTAG 片上调试器（兼容 OpenOCD、GDB、Segger）
- 预装 bootloader，支持 UART/I²C/SPI Flash/SD 卡启动
- DMA、真随机数发生器、Trace 端口（RVFI 兼容）
- 丰富的可配置外设

### FPGA 支持

- 已验证 6 大 FPGA 厂商：AMD(Xilinx)、Intel(Altera)、Lattice、Microchip、Gowin、Cologne Chip
- 也有多次 ASIC 流片记录
- 示例：Cyclone IV E 上 ~130 MHz，约 2300 LUTs + 1000 FFs

### 软件生态

- RISC-V GCC 工具链 + Eclipse IDE
- Zephyr RTOS、FreeRTOS 官方支持
- MicroPython、Ada(HAL)、Rust(Embassy) 移植
- LiteX SoC 构建器集成
- 可运行 nommu-Linux

### 项目数据

- GitHub Stars: 2100+
- Commits: 10291
- License: BSD-3-Clause
- CoreMark: 95.23 (0.9523 CoreMarks/MHz, rv32imc 配置)

## 个人备注

NEORV32 是学习 RISC-V 处理器设计的优秀开源参考项目。纯 VHDL 实现、文档完善、社区活跃，适合从 RTL 入门到实际 FPGA 部署。后续可以结合学习笔记深入分析其流水线设计和外设架构。

_Last updated: 2026-05-29_
