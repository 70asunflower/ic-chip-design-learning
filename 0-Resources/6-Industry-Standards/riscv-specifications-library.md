---
title: RISC-V 规范库（Ratified Specifications Library）
short: RISC-V 规范库
summary: RISC-V International 官方规范库，ISA/配置集/平台/软件全部批准规范 HTML+PDF 一站式查阅
source: https://docs.riscv.org/reference/home/index.html
date: 2026-11-20
tags: [risc-v, isa, specification, platform, reference]
links:
  - https://docs.riscv.org/reference/rva23/index.html
  - https://docs.riscv.org/reference/server-platform/index.html
  - https://docs.riscv.org/reference/isa/priv/priv-index.html
---
# RISC-V 规范库（Ratified Specifications Library）

> RISC-V International 官方维护的**唯一权威规范汇总站**：收录全部已批准（Ratified）的 RISC-V 规范，按主题分组，每份提供 HTML 在线阅读与 PDF 下载。查规范不必再翻各个 GitHub 仓库和邮件列表。

## 核心要点（摘要）

- **发布方**：RISC-V International，站点声明只收录 ratified（已批准、稳定）规范
- **形式**：每条规范都有 HTML + PDF 两种格式，另有 "More" 链到原始文档 / Jira
- **分类**：Core Architecture / Profiles / Platforms / System Architecture / Debug, Trace, RAS / Platform Software / Application Enablement 七大类
- **状态语义**：标为 Ratified 的文档不可再修改，后续演进通过新扩展或新版本发布
- **价值**：做 RISC-V 处理器、系统软件或服务器平台时，这里是判定"合不合规范"的最终依据

## 详细内容

### 核心架构（Core Architecture）

| 规范 | 版本 | 时间 |
|------|------|------|
| Unprivileged ISA（非特权指令集） | v20260120 | 2026-01 |
| Privileged ISA（特权架构 / M、S 模式） | v20260120 | 2026-01 |

### 配置集（Profiles）

| 规范 | 版本 | 时间 |
|------|------|------|
| RISC-V Profiles（框架） | v1.0 | 2023-04 |
| RVA23（应用处理器） | v1.0 | 2024-10 |
| RVB23（嵌入式与边缘） | v1.0 | 2024-10 |

### 平台（Platforms）

- **Server Platform v1.0**（2026-05）：服务器平台硬件 / 固件 / 安全能力的最小契约
- **Server SoC v1.0**（2025-02）：服务器级 SoC 要求与约定

### 系统架构（System Architecture）

- Advanced Interrupt Architecture（AIA）v1.0（2023-06）
- IOMMU v20260222（2026-02）
- Platform-Level Interrupt Controller（PLIC）v1.0.0（2023-02）
- Server SoC v1.0（2025-02）

### 调试、追踪与 RAS（Debug, Trace, RAS）

- Debug Specification v1.0（2025-02）、Efficient Trace v2.1（2026-10）、RERI v1.0（2024-05）
- Trace 系列：N-Trace、Trace Connectors、Trace Control Interface（均 2024-11）、HART Trace Interface v1.0（2026-09）、Unformatted Trace & Data Encapsulation v1.0（2024-06）
- QoS Register Interface v1.0（2024-06）

### 平台软件（Platform Software）

- Supervisor Binary Interface（SBI）v3.0（2025-07）
- Boot and Runtime Services（BRS）v1.0（2025-08）
- UEFI Protocol v1.0.0（2022-05）、Platform Management Interface v1.0（2025-07）
- Semihosting v1.0（2025-02）、IO Mapping Table v1.0（2025-03）、Functional Fixed Hardware v1.0.1（2024-10）、QoS Controllers Table v1.0（2026-06）

### 应用使能（Application Enablement）

- Application Binary Interface v1.0（2022-11）
- Vector C Intrinsic v1.0（2025-04）

## 个人备注

这份规范库是 RVA23、Server Platform 等专题的**源头**——想确认某个扩展是不是强制、某个 CSR 定义，直接回这里查 PDF，不要依赖二手博客。搭配仓库里的 [xv6-riscv](../5-Courses-Tutorials/xv6-riscv.md) 使用效果最好：读源码时对照特权 ISA 规范里的 `stvec`/`sepc`/`satp` 等 CSR，能把"软件行为 ↔ 硬件接口"这条链路真正打通。

_Last updated: 2026-11-20_
