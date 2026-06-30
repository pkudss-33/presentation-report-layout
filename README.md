# presentation-report-layout

> 纯格式排版技能 — 多视图、卡片嵌套、结构清晰的演示型 HTML 报告布局。

## 这是什么

`presentation-report-layout` 是一个 **纯格式技能**（不含内容分析/提炼逻辑），提供一套经过验证的企业级设计系统，用于生成多页面切换、KPI 数据卡片、彩色语义卡、可折叠面板、sticky 侧栏分节等组件的单文件 HTML 报告模板。

**你提供结构化内容，这个技能负责排版呈现。**

## 适用场景

- 工作总结 / 年中总结 / 年终总结
- 月度 / 季度经营简报
- 多事项汇总报告
- 管理层摘要报告
- 需要分 Tab 浏览、KPI 卡片、风险提示等结构化展示的汇报材料

## 快速开始

调用本 skill 后，按以下流程：

1. **读取格式指南** `references/format-guide.md`（完整参数参考）
2. **复制模板** `assets/presentation-template.html` 到工作目录
3. **替换所有 `[[...]]` 占位符**，将用户的结构化内容填入
4. **保存为 `.html`**，浏览器直接打开即可

## 核心设计参数速查

| 参数 | 值 |
|---|---|
| 内容最大宽度 (hero) | 1260px |
| 内容最大宽度 (正文) | 1180px |
| 两侧留白 | 21px |
| Section 上下间距 | 56px |
| 卡片内边距 | 17–20px |
| 默认网格间距 | 14px |
| 卡片圆角 | 10px |
| Pill 圆角 | 999px |
| Hover 上浮 | translateY(-2px) |
| 过渡动画 | 220ms cubic-bezier |
| 正文字号 | 16px |
| 正文行高 | 1.72 |
| KPI 数值字号 | 32px |
| h1 字号 | clamp(38px, 5vw, 66px) |
| h2 字号 | clamp(30px, 3.2vw, 44px) |

## 色彩语义

| 颜色 | CSS class | 含义 |
|---|---|---|
| 蓝 | `.b-card.blue` | 数据基建 / 中性信息 |
| 绿 | `.b-card.green` | 正向结果 / 利好 / 达成 |
| 琥珀 | `.b-card.amber` | 策略 / 需关注 / 中度风险 |
| 红 | `.b-card.red` | 风险 / 警告 / 未达成 |

## 组件目录

| 组件 | CSS class | 用途 |
|---|---|---|
| Hero 头部 | `.hero` > `.hero-inner` | 标题 + eyebrow + lead + Tab 导航 |
| Chapter Tabs | `.chapter-tabs` > `a[data-view-toggle]` | 顶层视图切换 (3-5 个 Tab) |
| Quick Nav | `.quick-nav` > `a` | Pill 型视图内快捷锚点 |
| KPI 卡片 | `.kpi-row` > `.kpi-card` | 5 列指标仪表盘 |
| 2 列卡片 | `.grid-2` > `.card` | 并列对比 |
| 3 列卡片 | `.grid-3` > `.card` / `.b-card` | 三支柱 / 三选项 |
| 4 列卡片 | `.grid-4` > `.card` | 四象限 / 四能力 |
| 彩色语义卡 | `.b-card.blue` / `.green` / `.amber` / `.red` | 色彩编码关键信息 |
| Tagline | `.tagline` | 卡片内小分类标签 (999px 圆角) |
| 表格 | `table` | 结构化数据，圆角 + 表头灰底 |
| 可折叠面板 | `details.panel` | "展开 ▼" / "收起 ▲" 交互 |
| 引用块 | `.quote` / `.quote.warn` / `.quote.risk` | 左侧 4px 色条 (绿/琥珀/红) |
| 风险卡片 | `.risk-alert` | 红色左边框 + 红色标题 |
| 时间线 | `.timeline` > `.step` | 5 列阶段推进 |
| Biz 分节 | `.biz-section` | 270px sticky 侧栏 + 1fr 内容 |
| Biz 网格 | `.biz-grid` > `.biz-box` | 2 列业务卡片 |
| Pill 行 | `.pill-row` > `.pill` | 标签云 |
| Section 说明 | `.section-note` | h2 下方灰色导语 (max-width 1040px) |
| 进度条 | `.progress` | 顶部固定渐变色阅读进度 |

## 中英文混排规则

- 中文字符与数字/拉丁字母之间使用 **thin space** (`&thinsp;` U+2009)，约 1/5 em 宽
- 不使用全角空格（太宽），也不省略空格（太挤）
- 正文层级 `letter-spacing: 0`，只在 `.eyebrow`、`.tagline`、`th` 等装饰性短标签上使用 letter-spacing

## 文件结构

```
presentation-report-layout/
├── SKILL.md                              # 技能定义文件
├── README.md                             # 本文件
├── references/
│   └── format-guide.md                   # 完整格式参数参考（权威规范）
└── assets/
    └── presentation-template.html         # 空白模板（复制并填入内容）
```

## 安装

### 方式一：Git 克隆

```bash
mkdir -p ~/.claude/skills
cd ~/.claude/skills
git clone https://github.com/pkudss-33/presentation-report-layout.git
```

### 方式二：手动安装

将整个 `presentation-report-layout/` 目录放到 `~/.claude/skills/` 下。

安装后重启 Claude Code 或新开会话即可使用。调用方式：

```
用 presentation report 格式帮我做 XXX 报告
```

## 与其它 skill 的区别

- **presentation-report-layout** (本 skill)：纯格式排版，多 Tab 视图 + 卡片嵌套 + KPI 仪表盘，不含内容分析逻辑
- **management-report-builder**：管理报告，一页纸线性滚动，含信息提炼工作流
- **huangwei-report-builder**：研究型报告，多章节弧形叙事，证据密集型

## License

MIT
