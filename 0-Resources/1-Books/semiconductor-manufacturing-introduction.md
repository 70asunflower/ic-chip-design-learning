---
source: https://github.com/chenwei810/Semiconductor_Manufacturing_Introduction
date: 2026-10-16
tags: [semiconductor-manufacturing, fab, process-flow, cmos, lithography, etch, thin-film, cmp, packaging, test, textbook, chinese, beginner]
links:
  - https://github.com/chenwei810/Semiconductor_Manufacturing_Introduction
  - https://github.com/chenwei810/Semiconductor_Manufacturing_Introduction/tree/main/zh-TW
---

# 半導體製造概論（Introduction to Semiconductor Manufacturing）

> 面向初学者的开放教材（**913★**），追踪一片硅晶圆从**沙子 → 晶圆厂 → 制程模块与整合 → 测试 → 封装 → 芯片**的全过程。刻意跳过重物理，专注**制程流程、术语与现场实务（know-how）**——每章配「术语框（term boxes）」和「实务知识框（know-how boxes）」，零半导体物理基础可读。繁体中文为原版，另有英/日/韩三版。

## 章节结构（7 部 24 章 + 3 附录）

| 部 | 主题 | 章节 |
|----|------|------|
| Part 0 | 開始之前 | 0 半導體製造全景 / 1 晶圓廠如何運作 |
| Part 1 | 基礎 | 2 從物理到電晶體 / 3 從沙子到晶圓 |
| Part 2 | 製程模組 | 4 微影 / 5 薄膜 / 6 蝕刻 / 7 離子佈植與熱處理 / 8 CMP / 9 清洗與污染控制 / 10 金屬化 |
| Part 3 | 製程整合 | 11 完整 CMOS 流程 / 12 先進電晶體結構 / 13 記憶體製程 / 14「幾奈米」是什麼意思 |
| Part 4 | 品質與良率 | 15 量測與檢測 / 16 良率與故障分析 / 17 製程控制 / 18 異常處理與工程變更 |
| Part 5 | 後段（測試與封裝） | 19 晶圓測試 / 20 封裝 / 21 先進封裝 / 22 最終測試與可靠度 |
| Part 6 | 走出晶圓廠 | 23 工廠如何被系統管理 / 24 製程如何影響韌體 |
| 附錄 | A 術語總表 / B 現場行話 / C 延伸閱讀 | |

## 内容特色

- **每章 Markdown 独立成篇**（GitHub 直接阅读），多语言目录并列：`zh-TW/`（原版）/ `en/` / `ja/` / `ko/`
- **term box + know-how box** 双框设计：术语给定义、现场给经验——这是它区别于普通科普的核心
- **阅读路径按人群分流**（README "Reading paths"）：

| 读者 | 推荐章节 |
|------|----------|
| 快速概览 | 0、1、11、14 |
| 软件/固件工程师 | 0、2、11、13、14、22、23、24 |
| 半导体新入行者 | 全书，重点 1、11、15–18 + 附录 B |
| 封装与测试人员 | 0、11、19–22 |

- 仓库 1.5MB 量级，含 `images/`、`templates/`、`STYLE_GUIDE.md`（内容工程化程度高）；2026-10-11 完成中英双语版并新增日韩版
- 仓库根含 `LICENSE`，但 GitHub SPDX 自动识别为 `NOASSERTION`——**具体许可条款待核实**，正式引用前先看 LICENSE 原文

## 与库内资源的关系

- **互补 Bits on Chips**（同在 `1-Books`）：Veendrick 讲器件/电路/系统**原理**，这本讲制造**流程与现场**——制造侧缺的那块正好补上
- **互补 7-Videos 芯片制造抖音视频**：那个是动画科普建立直觉，这本是 24 章系统教材建立完整知识框架
- 第 3/4/5/11 章（从沙子到晶圆→微影/薄膜/蚀刻→完整 CMOS 流程）是 IC 设计学习者理解工艺约束的底子；第 24 章「制程如何影响固件」对你这种系统/固件方向的人少见地实用

_Last updated: 2026-10-16_