---
name: tech-earnings-deepdive-external
description: Analyzes a given tech company using the tech-earnings-deepdive framework with external-only data sources, judges buy/sell/hold, and appends the report to _sidebar.md. Use when the user asks to analyze a company for investment, run tech-earnings-deepdive on a stock, or create a fresh analysis without referencing project documents. All data must come from web search, SEC filings, earnings transcripts, and other external sources—never from analysis_2026/, analysis/, or any existing project documents.
---

# 科技股财报深度分析（外部数据版）

基于 tech-earnings-deepdive 框架，对指定公司进行投资分析，**仅使用外部获取的最新信息**，判断是否值得买入，并将报告写入项目并添加到侧边栏。

---

## 核心约束

### 数据来源铁律

**禁止**引用或参考以下项目内文档：
- `analysis_2026/` 下任何分析报告
- `analysis/` 下任何历史分析
- 项目中其他已有公司相关文档

**必须**使用的外部来源：
- Web Search：最新财报、新闻、分析师观点
- mcp_web_fetch：SEC 10-K/10-Q/8-K、财报原文、Earnings Call 实录
- 一手来源：CEO/CFO 原话、官方投资者关系页面、交易所公告
- 事实来源：法庭文件、监管文件

找不到数据时注明「未获取」，不得编造或从项目文档推断。

---

## 执行流程

### 1. 读取分析框架

执行分析前，读取以下文件以获取完整方法论：
- `.cursor/skills/tech-earnings-deepdive/SKILL.md` — 16 模块、Key Forces、输出模板
- `.cursor/skills/tech-earnings-deepdive/valuation-models.md` — 估值模型
- `.cursor/skills/tech-earnings-deepdive/investing-philosophies.md` — 6 大投资哲学
- `.cursor/skills/tech-earnings-deepdive/bias-checklist.md` — 反偏见检查

### 2. 执行分析

按 tech-earnings-deepdive 的完整流程执行：
- 第零步：Key Forces 识别
- 第一步：16 大分析模块（A–P）
- 第二步：6 大投资哲学视角
- 第三步：估值矩阵
- 第四步：反偏见与 Pre-Mortem
- 第五步：决策框架与输出

所有数据通过 Web Search、mcp_web_fetch 等工具从外部获取。

### 3. 保存报告

**文件路径**：`analysis_2026/[公司文件夹]/[公司中文名]_财报深度分析_[yyyy-MM-dd].md`

公司文件夹命名规则：
- 美股：股票代码小写（如 `nvda`、`meta`、`msft`）
- 港股/中概：公司英文名或拼音（如 `meituan`、`alibaba`、`ponyai`）

**示例**：`analysis_2026/nvda/英伟达_财报深度分析_2026-03-11.md`

### 4. 更新 _sidebar.md

在「2026年分析报告」区块中新增一行，格式为：

```markdown
- [公司中文名_财报深度分析_yyyyMMdd](analysis_2026/[公司文件夹]/[公司中文名]_财报深度分析_[yyyy-MM-dd].md)
```

**日期格式**：
- 文件名：`yyyy-MM-dd`（如 2026-03-11）
- 链接标题：`yyyyMMdd`（如 20260311）

**示例**：
```markdown
- [英伟达_财报深度分析_20260311](analysis_2026/nvda/英伟达_财报深度分析_2026-03-11.md)
```

插入位置：按时间或字母顺序，与其他 2026 年分析报告保持一致。

---

## 输出要求

### 决策结论

报告开头必须明确给出：
- **推荐动作**：买入 / 加仓 / 持有 / 减仓 / 清仓 / PASS
- **信心水平**：高 / 中 / 低
- **Action Price**：买入价、加仓价、减仓价（基于估值，非当前股价）
- **Kill Condition**：触发退出的具体条件

### 报告结构

遵循 tech-earnings-deepdive 的完整输出模板，包含：
- 执行摘要、Key Forces
- 模块 A–P 分析
- 估值矩阵、6 大哲学视角、Variant View
- Pre-Mortem、反偏见检查
- 长期监控变量清单、Action Trigger
- 证据来源表

---

## 检查清单

执行完成后自检：
- [ ] 未引用 analysis_2026/、analysis/ 或项目内公司文档
- [ ] 所有关键数据标注了外部来源
- [ ] 报告已保存到 `analysis_2026/[公司文件夹]/`
- [ ] _sidebar.md 已添加链接，标题含 yyyyMMdd
- [ ] 决策结论（买/卖/持有）与估值、Key Forces 一致
