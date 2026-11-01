# 参与维护

**一条资源只需要改一个地方**：资源文件自己的 frontmatter。其余全部由
`scripts/build.py` 生成。

> 脚本清单见 [`scripts/README.md`](scripts/README.md)。

## 加一条资源（0-Resources/）

### 1. 建文件

在对应子目录建 `<name>.md`，文件名小写连字符（如 `axi-bus-protocol.md`）。
frontmatter 五项**全部必填**：

```markdown
---
title: 显示名称（网页卡片 / 表格 / 导航都用它）
summary: 一句话说明，40–60 字最佳（同时用于网页卡片和子目录表格）
source: 原始链接
date: YYYY-MM-DD
tags: [tag1, tag2]
---
```

正文建议按 `## 核心要点（摘要）` / `## 详细内容` / `## 个人备注` 组织。

> 子目录：`1-Books` · `2-Papers` · `3-EDA-Tools` · `4-OpenSource-Projects` ·
> `5-Courses-Tutorials` · `6-Industry-Standards` · `7-Videos`

### 2. 跑生成

```bash
python scripts/build.py
```

它会从 frontmatter 重新生成下面这些文件，**不要手改它们**：

| 文件 | 说明 |
|------|------|
| `0-Resources/0-Index.md` | 整个文件 |
| `0-Resources/<子目录>/README.md` | 表格部分（`BUILD:TABLE` 标记之间） |
| `README.md` | 资源导航（`BUILD:NAV` 标记之间） |
| `index.html` | 整个文件 |
| `assets/roadmap-*.svg` | 学习路线图（节点标题取自 frontmatter） |

### 3. 记一笔 changelog

在根 `README.md` 的 Changelog 表**表头下方**加一行（日期倒序，CI 强制）：

```markdown
| YYYY-MM-DD | Added <名称> — 一句话说明 |
```

### 4. 提交

```bash
python scripts/check_consistency.py      # 语义检查
python scripts/build.py --check          # 生成物是否最新
git add -A && git commit -m "feat(resources): add <名称>"
```

## 加一条笔记（1-Notes/）

笔记**不进网页索引**，所以流程不同（没有生成的环节）：

1. 在对应子目录建 `.md` 文件（如 `1-Notes/1-Digital-Design/fsm-design.md`）
2. frontmatter 用笔记的 schema（以 `1-Notes/0-Template.md` 为准，**和资源不同**）：
   ```markdown
   ---
   topic: 主题
   date: YYYY-MM-DD
   tags: []
   status: reading   # reading / writing / done
   ---
   ```
3. 正文：自己的理解、代码实验、踩过的坑
4. 加进该目录的 `README.md` 索引
5. 手动加进根 `README.md` 的 `📝 Personal Notes` 导航段（这段不是生成的）
6. 加一行 changelog

## 加一个代码示例（2-Code/）

1. 建子目录 `2-Code/<project-name>/`，含源文件与 `README.md`
2. 加进 `2-Code/README.md`

## 硬性规则

- **文件名**：小写、连字符分隔（如 `axi-bus-protocol.md`）
- **frontmatter**：`title` / `summary` / `source` / `date` / `tags` 缺一不可，
  `check_consistency.py` 会直接报错
- **标签**：只用规范写法。`scripts/tags.json` 登记了「废弃写法 → 规范写法」，
  `python scripts/normalize_tags.py` 会改写，CI 会拒绝任何残留别名；
  `--report` 打印标签频次和单例标签（判断该不该合并）
- **Changelog**：新行插在表头下方（日期倒序，CI 强制）
- **不要手改生成块**：`BUILD:NAV` / `BUILD:TABLE` 标记之间、`0-Index.md`、
  `index.html`、`assets/roadmap-*.svg` 都是生成物，下次构建会被覆盖
- **不需要 `_Last updated` footer**：`date` 是唯一的日期来源，footer 会漂移

## 改学习路径

路线图的节点标题来自 frontmatter，**路径结构**在 `scripts/build.py` 顶部的
`ROADMAP` 里（哪条目标 → 先读哪篇 → 接着哪篇）。改完重跑 `build.py`。
引用不存在的资源会直接构建失败，不会静默少一行。

## 更新 README 预览图

`assets/preview.png` 是 `index.html` 的截图，界面有较大变化时重截一次：

```bash
python -m http.server 8791 --bind 127.0.0.1     # 另开一个终端
curl -s http://127.0.0.1:8791/index.html | head -c 120   # 先确认端口上是本站
chrome --headless=new --disable-gpu --hide-scrollbars \
  --window-size=1200,1000 --virtual-time-budget=4000 \
  --screenshot="$PWD/assets/preview.png" \
  "http://127.0.0.1:8791/index.html"
```

无头 Chrome 默认按暗色渲染，所以预览图是暗色版。
**务必先 curl 确认端口**——端口被别的本地服务占用时，会截到完全无关的页面。
