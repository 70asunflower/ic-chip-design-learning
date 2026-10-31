---
source: https://github.com/Tencent/wave-mcp
date: 2026-10-31
tags: [verification, waveform, mcp, ai-agent, fst, vcd, fsdb, pyslang, pylibfst, debug, x-state, diff, tencent, open-source]
links:
  - https://github.com/Tencent/wave-mcp
  - https://mp.weixin.qq.com/s/1S4aN6f-opERFy9qAN3RpA
---

# wave-mcp（腾讯开源）

> 腾讯蓬莱实验室验证团队开源的 **波形调试 MCP Server**：**不跑仿真器，只消费你已经产出的波形 + RTL 源码**，给 LLM/Code Agent 提供 **37 个工具（12 类）**的波形调试能力。纯开源栈（pylibfst + pyslang），免 License、不限并发、不限机器数——这正是 Agent 深度接入验证流程的前提。

## 为什么值得关注

商用调试 MCP 要 License 且并发受限，而 Agent 调试的特点是**高频、并发、海量点查询**（动辄成千上万条波形），License 成本撑不住。wave-mcp 的价值不在"又一个波形工具"，而在三点：

1. **把波形调试变成 Agent 可调用的原语**——从"看 log 猜原因"升级为真读信号值、查驱动链、做 pass/fail diff
2. **静态网表 + 动态波形在同一套工具里**——商用工具中这是两个产品，这里 `signal_drivers` 和 `signal_values` 同属一个 session
3. **免 License 解除规模化瓶颈**

## 核心能力

| 能力 | 说明 |
|------|------|
| **波形查询（FST 直读）** | 层次、实例、信号位宽/方向/类型、点查询/区间查询、按时钟边沿对齐的逐拍采样；FST 随机访问契合 AI 的点查询模式 |
| **静态分析（pyslang 网表）** | 连接、驱动、扇入/扇出、声明位置（文件:行号）；完整精化（参数/generate/interface 全展开），持久化为静态设计数据库 |
| **无波形也能用** | `open_static_session` 只凭 RTL 建 session——仿真前就能查接口、查驱动、浏览层次、做 code review；波形出来后同一份 RTL 用 `prepare_session` 自动升级，网表复用 |
| **值追踪与 X 态追踪** | `trace_value` 沿驱动链反向遍历、跨模块下钻，每个节点带真实 FST 值；`trace_x` 直接追 X 根因；`active_drivers` 用波形值对驱动语句门控条件做 **4 值求值**，回答"这一拍到底哪条语句在起作用" |
| **pass/fail 波形对比** | `diff_waveforms` 对多份波形定位**首个分歧时刻**，按分歧时间排序信号、时钟对齐采样过滤毛刺；分歧信号可接 `signal_fanin`/`active_drivers` 做因果回溯 |
| **Agent 驱动的浏览器波形查看器** | `open_wave_view` 让 Agent 分析完直接弹浏览器波形：嫌疑信号 + 游标钉在出错时刻 + 分析说明弹窗，双波形对比两栏同步；几十 GB FST 秒开（服务端流式，浏览器按需取数） |

**典型闭环**：case 挂了 → `diff_waveforms([pass, fail])` 定位首分歧 → `signal_fanin`/`active_drivers` 回溯根因 → `open_wave_view` 双波形 + 分歧 marker + 说明一次呈现。

37 个工具**全部同时提供 CLI 接口**，不挂 Agent 也能在终端直接调，适合写 CI 脚本。

## 波形格式与仿真器支持

| 格式 | 支持情况 |
|------|----------|
| **FST** | ✅ 直读。Verilator `--trace-fst`、Icarus `-fst` 直接产出 |
| **VCD** | ✅ 自动转 FST（依赖 GTKWave 的 `vcd2fst`），体积约为 VCD 的 1/50；支持流式转换，把转换时间藏进仿真时间 |
| **FSDB** | ✅ 自带 `fsdb2fst` 转换，只需本机有 Verdi 的 FsdbReader 运行库，**运行时不占 Verdi License** |
| **SHM** | ❌ 不支持，也不在计划内。Xcelium 用户推荐用 `fstdumper` VPI 插件从仿真源头直接产 FST（免 License、零转换） |

因此 VCS、Xcelium、Questa、Verilator、Icarus 都能接，区别只在走哪条转换通道。

## 可信度（README 验证数据）

- 真实生产级芯片项目（几十个模块）+ **OpenTitan 27 个 IP** + **香山 38 个 IP**，一百多个测试 case
- **225 万信号级验证，值查询正确性 100%**；**310 万多次工具调用全部通过**；百万级 scope 的超大模块稳定完成分析
- 工程细节（区分 demo 与生产工具的关键）：网表缺 `+incdir+` 时从 pyslang 诊断自愈重编；单 top 精化失败（如 UVM 环境拉不到 `uvm_pkg`）只影响该 top；网表以 `partial` 标志照常服务且 `session_info` 如实上报覆盖率；源码或波形变了但网表未更新会**报警，绝不静默给错结果**

## 上手

```bash
pip install wave-mcp                                    # Linux x86_64，Python 3.10–3.13
wave-session --fst sim/dump.fst --top top_tb --filelist rtl.f   # 波形+filelist → session
python -m wave_mcp.server --session sessions/my_module   # 启动 MCP Server
```

接入 Code Agent（Claude Code / Cursor / Gemini CLI / Cline / Windsurf 通用）在 MCP 配置里加：

```json
{ "mcpServers": { "wave-mcp": {
    "command": "python",
    "args": ["-m", "wave_mcp.server", "--session", "/abs/path/to/sessions/my_module"] } } }
```

⚠️ **两个坑**：
1. 环境变量（`VERDI_HOME`、filelist 里的 `$PROJ_ROOT`）要写进 MCP 配置的 `env` 块，**不能用 shell export**——Agent 以子进程拉起 Server，继承不到交互式 shell 变量
2. 隔离网 / CentOS 7 / 无 Python 3.10 的老机器：用 `deploy/docker_build_all.sh` 打离线 bundle，自带独立 Python 3.11 与全部依赖

## 限制与边界

- **平台**：Linux x86_64 官方支持；macOS / Windows 需自行编译 pylibfst，且波形查看器不可用
- **查看器资产**（Surfer WASM + surver，EUPL-1.2）不随包分发，需按文档自行构建一次
- 不内置任何协议库（事务定义由调用方给）；FSM 工具只报实际发生的转移，不做覆盖率
- 不做多租户，一台机器服务多人需每人起一个进程
- 目前更适合 **IP / 模块级调试**，SoC 级全芯片波形的实际表现待更多外部项目验证
- 许可：文章与项目声明 **Apache-2.0**；GitHub SPDX 接口返回 `NOASSERTION`（未自动识别），正式引用以 LICENSE 原文为准

## 与库内资源的关系

- 与 `4-OpenSource-Projects/nano-kpu` 天然配对：那边是**设计**（RTL + Verilator 仿真流程），这边是**验证**（把仿真产出的 FST 交给 Agent 追根因）——Verilator `--trace-fst` 正好直接产出 wave-mcp 直读的格式
- 对学 RTL 的人：`open_static_session` 只凭 RTL 就能做 code review 和驱动关系梳理，**不用先跑仿真**，是很低门槛的上手入口

_Last updated: 2026-10-31_