# SeestarAI 小红书 HTML 设计规范

## 画布与卡片

| 属性 | 值 |
|------|-----|
| 卡片尺寸 | 540 × 720px（3:4） |
| 圆角 | 24px |
| 页面边距 | 36px 上 / 42px 左右 / 36px 下 |
| 卡片间距 | 27px |
| 背景色（整体） | #e8e4de |
| 字体 | -apple-system, BlinkMacSystemFont, PingFang SC, Hiragino Sans GB, Microsoft YaHei, sans-serif |

## 配色

| 用途 | 浅色卡片 | 深色卡片 |
|------|---------|---------|
| 背景 | #faf8f5 | #1c1c1e |
| 主文字 | #1c1c1e | #e8e4de |
| 次要文字 | #8c8880 | #7a7670 |
| 强调色 | #c44a2a | #d4744a |
| 浅色卡片边框 | #eee | — |
| 浅色卡片信息块背景 | #fff | — |
| 深色卡片信息块背景 | — | rgba(255,255,255,0.04) |
| 深色卡片信息块边框 | — | rgba(255,255,255,0.05) |

## 排版

| 元素 | 字号 | 字重 | 行高 | 其他 |
|------|------|------|------|------|
| 品牌 "SeestarAI分享" | 18px | 800 | — | letter-spacing: 3px |
| 导航标签 | 12px | 400 | — | letter-spacing: 3px, 右对齐 |
| 页面标题 h2 | 28px | 700 | 1.3 | letter-spacing: -0.3px |
| 封面标题 h1 | 40px | 800 | 1.14 | letter-spacing: -0.5px |
| 封面英雄数字 | 66px | 900 | 1 | letter-spacing: -2px |
| 封面导语 | 17px | 400 | 1.55 | — |
| 指标行数值 | 30px | 800 | 1 | min-width: 100px |
| 指标行描述 | 15px | 400 | 1.5 | — |
| 网格卡数值 | 26-28px | 800 | 1 | — |
| 网格卡标签 | 13-14px | 400 | — | — |
| 引语文字 | 15px | 400 | 1.5 | 左边框 3px |
| 引语出处 | 13px | 600 | — | — |
| 底部注释 | 14-15px | 400 | 1.5 | 顶部分割线 |
| 辩论栏标题 | 13px | 700 | — | letter-spacing: 3px |
| 辩论栏内容 | 13px | 400 | 1.5 | — |
| 柱状图标签 | 14px | 600 | — | — |
| 柱状图数值 | 14px | 600 | — | min-width: 95px |

## 页头组件

```
┌──────────────────────────────────────────────┐
│ SeestarAI分享                    深度报道    │
│                                              │
│ (标题 h2)                                    │
└──────────────────────────────────────────────┘
```

```html
<div class="page-header">
  <div class="brand">SeestarAI分享</div>
  <div class="section-tag">导航标签</div>
</div>
```

## 可用布局组件

### 1. 指标行列表 (metric-stack / metric-row)
适用于：展示 3-4 个关键数字+说明
```html
<div class="metric-stack">
  <div class="metric-row">
    <div class="mv accent">数值</div>
    <div class="md sec">描述文字</div>
  </div>
  ...
</div>
```

### 2. 2×2 网格卡片 (grid2 / gc)
适用于：4 个并列指标
```html
<div class="grid2">
  <div class="gc"><div class="gv accent">数值</div><div class="gl">标签</div></div>
  ...
</div>
```

### 3. 柱状图 (bar-list / bar-item)
适用于：与多家公司的市值/估值对比
```html
<div class="bar-list">
  <div class="bar-item">
    <div class="bn">公司名</div>
    <div class="bt"><div class="bfill" style="width:X%;background:#颜色;"></div></div>
    <div class="bv">数值</div>
  </div>
  ...
</div>
```
注意：Anthropic/当前公司用强调色，其余用#1c1c1e（浅色背景）或对应深色。

### 4. 双栏辩论 (debate-cols / debate-col)
适用于：泡沫论 vs 价值论
```html
<div class="debate-cols">
  <div class="debate-col bear">
    <div class="dh">泡沫论</div>
    <div class="di">论点</div>
  </div>
  <div class="debate-col bull">
    <div class="dh">价值论</div>
    <div class="di">论点</div>
  </div>
</div>
```

### 5. 引语列表 (quote-stack / quote-block)
适用于：3 条权威信源引语
```html
<div class="quote-stack">
  <div class="quote-block">
    引语内容
    <div class="qa">— 出处</div>
  </div>
</div>
```

### 6. 4 格机构卡片 (fund-grid / fund-card)
适用于：展示融资参与方
```html
<div class="fund-grid">
  <div class="fund-card">
    <div class="fname accent">机构名</div>
    <div class="frole">角色描述</div>
  </div>
</div>
```

### 7. 时间线 (tl / tl-i)
适用于：展望或回顾序列
```html
<div class="tl">
  <div class="tl-i">
    <div class="tl-d">时间标签</div>
    <div class="tl-t">描述</div>
  </div>
</div>
```

### 8. 来源列表 (src-stack / src-item)
适用于：第10页数据来源
```html
<div class="src-stack">
  <div class="src-item">
    <div class="st">信源名称 · 日期</div>
    <div class="sd">具体描述</div>
  </div>
</div>
```

## 交色规律

页码配色交替：

| 页码 | 配色 |
|------|------|
| 1 封面 | 深色 |
| 2 速度/规模 | 深色 |
| 3 核心事件 | 浅色 |
| 4 竞争格局 | 深色 |
| 5 参照系 | 浅色 |
| 6 正反辩论 | 浅色 |
| 7 增长剖面 | 深色 |
| 8 多方观点 | 浅色 |
| 9 展望 | 深色 |
| 10 来源 | 浅色 |

## 底部注释

大多数页面底部有一条分割线 + 注释：
```
─────────────────────
注释文字
```

使用 `.footnote` 类，自动推到卡片底部（margin-top: auto）。
