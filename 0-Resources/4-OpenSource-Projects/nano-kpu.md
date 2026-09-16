---
source: https://github.com/MoonshotAI/nano-kpu
date: 2026-09-16
tags: [rtl, verilog, inference-chip, accelerator, moe, mla, linear-attention, quantization, int4, verilator, yosys, openroad, nangate45, ai-designed, open-source]
links:
  - https://github.com/MoonshotAI/nano-kpu
  - https://github.com/MoonshotAI/nano-kpu/blob/main/README_CN.md
---

# nano-kpu（MoonshotAI）

> nano 级**混合架构推理芯片**的完整 RTL 设计 + 功能仿真 + 时序/面积评估流程，**由 Kimi-K3 全程设计实现**（仓库自述为 Kimi K3 的演示，非 Moonshot AI 官方项目）。Apache 2.0。目标模型是混合注意力 MoE transformer：**KDA（Kimi Delta Attention）线性注意力 + NoPE MLA + sigmoid-routed MoE（top-2 路由专家 + 1 共享专家）+ attention-residual mixing**，权重 int4 group-128，teacher-forced 逐 token 解码。

## 仓库结构

| 目录 | 内容 |
|------|------|
| `rtl/` | 芯片 RTL，顶层模块 `msh_chip_top`，`filelist.f` 为编译清单；`roms/` 放 LUT 初始化 hex（sigmoid/alpha/expneg/rsqrt/recip）；`selfmodel/` 是 bit-exact 定点 Python 模型（仿真辅助） |
| `reference/` | float32 黄金参考模型（正确性判据，golden 在评估时重算） |
| `harness/` | 功能仿真 + 性能评估流程：`evaluate.py` 主入口、Verilator C++ testbench（16 B/cycle DRAM 端口模型）、`msh_sram`/`msh_rom` 宏模型、`synth_area.ys`/`synth_tech.ys`/`synth_netlist.ys`（yosys 面积/NE、Nangate45 映射时序、门级网表） |
| `docs/` | 架构 / 接口 / memory_map / 量化 / TASK_SPEC 规格文档 |
| `weights/` | 权重格式说明 |

## 接口与判据（工程细节值得学）

- **接口**：命令流（`RUN 0x1` → `DONE 0xD0DE`）+ **128-bit DRAM 端口**（顺序读、≥24 cycle 延迟、posted write）+ 自描述内存镜像（header + descriptor table）
- **正确性判据**：逐行 logits **cosine ≥ 0.98**、pooled **argmax ≥ 0.99**（对 float32 参考）
- **吞吐**：`cycles_per_token = 长稳仿真周期 / seq_len`，`tokens/s = clock / cpt`
- **存储规则**：所有超过触发器的阵列必须走 `msh_sram`/`msh_rom` 宏；宏位按 **~1 Mbit/mm²** 计价并计入面积预算

## 工具链与运行

```bash
bash scripts/setup_env.sh        # 一次性：conda 环境 + Nangate45 cell library
source scripts/kpu-env.sh
python3 harness/evaluate.py --quick   # 功能仿真（分钟级）
python3 harness/evaluate.py           # 完整评估（仿真 + 时序/面积，小时级）
make synth / lint / audit / selftest
```

依赖 Verilator 5.x（基线 5.050）、yosys ≥ 0.64、python 3.12 + numpy。Nangate45 库不随仓分发，setup 脚本从 OpenROAD-flow-scripts 按 commit + SHA-256 拉取。

## ⚠️ 方法论边界（引用时注意）

面积与时序是**综合阶段**的预估（yosys/abc 映射 + 静态时序），**未经后端布局布线验证**，且使用**冻结的固定综合参数**（刻意不做设计专属调优）——因此公布数字是**保守、可复现的基线，不是最佳 QoR，也不是 sign-off 数值**。引用时不要当流片指标。

## 为什么值得放进 IC 学习库

- **AI 设计芯片的实证样本**：RTL 由 Kimi-K3 生成，是"AI 参与芯片设计"这条线难得的完整可复现仓库（含黄金模型 + testbench + 综合脚本）
- **推理芯片全流程骨架**：从定点 self-model → RTL → Verilator 仿真 → yosys 综合 → 标准单元库时序/面积，一条链打通，可作为自己设计加速器的流程模板
- **量化与精度判据的工程写法**：int4 group-128、cosine/argmax 双阈值，比只谈"支持 int4"具体得多
- 与库内 NEORV32 / 玄铁（通用 RISC-V SoC）互补：那些是通用处理器，这个是**领域专用推理加速器**

## 配套阅读

- 中文 README：https://github.com/MoonshotAI/nano-kpu/blob/main/README_CN.md
- 规格文档：`docs/`（架构 / 接口 / memory_map / 量化 / TASK_SPEC）

_Last updated: 2026-09-16_