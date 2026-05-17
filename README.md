# SeestarAI 小红书推送

Claude Code Skill：全自动将当日最重要 AI 新闻转化为 10 页小红书 HTML 报道卡片 + 配套文案。

## 做什么

不是堆新闻标题——每天从 TechCrunch、FT、Bloomberg 等信源中选出 1 条最重要的 AI 事件，深度拆解为 10 页卡片：封面定调 → 速度/规模 → 核心事件 → 竞争格局 → 参照系 → 正反辩论 → 增长剖面 → 多方观点 → 展望 → 数据来源。

每页一张 3:4 比例的 HTML 卡片，浏览器打开直接截图就能发。

## 核心设计

- **5 阶段全自动流程**：新闻发现 → 选题与审查 → 叙事设计 → HTML 生成 → 文案输出
- **三级数据审查**：信源交叉验证 + 原始报告追溯 + 上下文校准，低于"高"置信度的数据标注限定语
- **10 页固定模板**：深/浅色交替，540×720px 卡片，PingFang SC 字体
- **配色**：SeestarAI 品牌色系，浅色 `#faf8f5` / 深色 `#1c1c1e`，强调色 `#c44a2a`

## 安装

```bash
# 克隆到 Claude Code skills 目录
git clone https://github.com/zushover/seestarai-xiaohongshu.git ~/.claude/skills/seestarai-xiaohongshu
```

## 使用

在 Claude Code 对话中说：

> "做一期 AI 日报" / "今天 AI 圈发生了什么" / "帮我做一个小红书 AI 报道"

Skill 自动执行全流程，输出：
1. `~/Downloads/seestarai-YYYYMMDD.html` — 10 页报道卡片
2. 小红书配套文案

## 示例

桌面上的 `seestarai-YYYYMMDD.html`，浏览器打开后每页 540×720px，直接截图发布。

## 文件结构

```
SKILL.md                  # Skill 定义与完整流程说明
references/
  design-spec.md          # HTML 设计规范（色板/排版/布局组件）
assets/
  template.html           # 10 页 HTML 模板骨架
```

## 技术栈

Claude Code Skill · HTML/CSS · WebFetch 信源抓取 · 多信源交叉验证
