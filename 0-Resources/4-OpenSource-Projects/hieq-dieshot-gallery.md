---
source: https://hieq-home404.pages.dev/#/layout
date: 2026-09-27
tags: [dieshot, layout, chip-images, intel, amd, apple-silicon, nvidia, qualcomm, hisilicon, process-node, reference, gallery]
links:
  - https://hieq-home404.pages.dev/#/layout
  - https://github.com/HiEq/Dieshot
---

# HiEq · Layout — Die Shot 裸片图库

> 个人维护的**处理器芯片裸片显微图（die shot）在线图库**：222 张高清裸片图，覆盖 **25 家厂商**，每张标注**工艺节点**（desc 字段，如 TSMC N3P / GlobalFoundries 14nm / IBM 32nm SOI），支持在线浏览与原图直下。图床与清单完全开源（[HiEq/Dieshot](https://github.com/HiEq/Dieshot)，manifest 为 `gallery.json`），站点部署在 Cloudflare Pages。

## 厂商覆盖（张数）

| 厂商 | 数量 | 厂商 | 数量 |
|------|------|------|------|
| Intel | 44 | Samsung | 12 |
| AMD | 33 | MediaTek | 7 |
| Apple Silicon | 31 | Microsoft | 5 |
| NVIDIA | 24 | Google / Sony | 各 4 |
| Qualcomm | 21 | Xiaomi | 3 |
| **海思 Hisilicon** | 15 | IBM / Baikal / MCST-Elbrus | 各 2 |
| 另有 | Cavium、Ampere、Centaur、Fungible、Glenfly（格罗方同）、**海光 Hygon**、**龙芯 Loongson**、**摩尔线程 MooreThreads**、Nikon、Spacemit（先楫）等 | | |

## 内容质量

- **分辨率极高**：原图宽度 2333 ~ **20958 px**（多数为摄影级拼接显微图），另有缩略图（`*.thumb.jpg`）供快速浏览
- **工艺节点标注齐全**：Apple M5（TSMC N3P）、AMD Zen4 CCD（N5）、Storm Peak IOD（6nm）、Raven Ridge（GF 14nm）、IBM Power 7+（32nm SOI）、MediaTek Helio G95（12nm）等
- 覆盖 CPU / GPU / SoC / 基带 / 游戏主机芯片，含**国产芯片**（海思、海光、龙芯、摩尔线程、先楫）

## 用法

- **在线浏览**：https://hieq-home404.pages.dev/#/layout （搜索、标签筛选、灯箱逐张看图、←/→ 翻页）
- **原图直下**：图片 URL 规律 `images/dieshot/{vendor}/{file}`，右键另存即可；`gallery.json` 是机器可读清单（id/title/desc/tags/src/thumb/w/h），可程序化批量拉取
- 杂图区：https://hieq-home404.pages.dev/#/misc

## 为什么值得收藏

- **微架构学习的直观素材**：对照 ISA/论文读 die shot，能直观看到 core/缓存/IO 的面积占比与多核拓扑
- **工艺节点演进的视觉证据**：同一厂商跨节点（如 Intel 44 张横跨多代）对比，晶体管密度变化一目了然
- 与库内 nano-kpu（推理芯片 RTL）互补：那个给你**怎么设计**，这个给你**造出来长什么样**

⚠️ 版权注意：die shot 原片多来自社区摄影（Flickr 等），个人学习/研究使用，转载发表前自行确认授权。

_Last updated: 2026-09-27_