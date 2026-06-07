---
name: tech-earnings-deepdive-external-new
description: Runs tech-earnings-deepdive on a company using external-only data (web search, HKEX/SEC filings, IR pages, earnings calls), outputs a buy/sell/hold memo with Action Price and Kill Condition, saves under analysis_2026/, updates _sidebar.md 最新分析, and appends a company-specific earnings glossary. Use when the user asks for /tech-earnings-deepdive-external-new, fresh external earnings analysis, or re-analysis without reading project analysis_2026/ or analysis/ docs.
---

# 科技股财报深度分析（外部数据版 v2）

基于 tech-earnings-deepdive 框架，**仅使用外部最新信息**完成投资分析，写入项目并更新侧边栏。相对 v1 的增强：报告标题 Variant View 化、QoQ 拐点表格、强制 bear case、**文末术语表附录**。

---

## 核心约束

### 数据来源铁律

**禁止**引用或参考：
- `analysis_2026/`、`analysis/` 及项目内任何已有公司分析文档

**必须**使用的外部来源（按优先级）：
1. **事实**：交易所公告（HKEX / SEC 10-K/10-Q/8-K）、公司 IR 页面、官方业绩新闻稿
2. **一手**：Earnings Call 管理层原话（引号标注 + 媒体/ transcript 来源）
3. **观点**：卖方研报、FactSet/Yahoo 共识、财经媒体深度稿
4. **Bear case**：主动搜索 `[代码] bear case` / `sell thesis` / 做空逻辑

找不到数据时写「未获取」，不得编造或从项目文档推断。

### 时效性

用户若要求「最近 N 个月」，以**分析当日**为基准检索；优先使用最新一季财报及财报后 2–4 周内的卖方更新、股价、电话会表态。

### 侧边栏铁律

链接**仅**写入 `_sidebar.md` 标题含 **「最新分析」** 的区块内（当前为 `- **2026年 5 月分析（最新分析）**：` 下同级列表），**不得**放入归档区。

格式：
```markdown
- [公司中文名_财报深度分析_yyyyMMdd](analysis_2026/[文件夹]/[公司中文名]_财报深度分析_[yyyy-MM-dd].md)
```
新报告按日期插入该列表（通常最新在最上或最下，与既有条目对齐）。

---

## 执行流程

### 0. 读取方法论（非公司数据）

- `.cursor/skills/tech-earnings-deepdive/SKILL.md`
- `.cursor/skills/tech-earnings-deepdive/valuation-models.md`
- `.cursor/skills/tech-earnings-deepdive/investing-philosophies.md`
- `.cursor/skills/tech-earnings-deepdive/bias-checklist.md`

### 1. 外部数据采集

并行检索：
- 最新季报/年报 PDF（HKEX 或 SEC）
- 官方 IR / 新闻稿
- 当前股价、市值、52 周区间（Yahoo Finance / Investing.com）
- 分析师目标价与 Q1 后评级更新
- 行业竞争与监管动态（近 1 个月）
- Bear case / sell thesis 至少 2 条

### 2. Key Forces → 模块优先级

先识别 1–3 个决定性力量，相关模块（通常 A/B/D/E/F/K）给 **2–3 倍篇幅**；G–J、N–P 可精要覆盖。

### 3. 撰写报告

**路径**：`analysis_2026/[文件夹]/[公司中文名]_财报深度分析_[yyyy-MM-dd].md`

**文件夹**：美股小写代码（`nvda`）；港股/中概拼音或英文名（`meituan`）。

**报告结构**：见 [report-template.md](report-template.md)

**必填结论（报告开头）**：
- 推荐动作：买入 / 加仓 / 持有 / 减仓 / 清仓 / PASS
- 信心水平：高 / 中 / 低
- Action Price：买入价、加仓价、减仓价（基于独立估值，非现价）
- Kill Condition：可量化、可验证

**标题格式**：
```markdown
# $CODE: [一句话 Variant View——这就是你的投资论点]
```

**报告首段声明**：
```markdown
> 本报告数据均来自外部公开来源（…），未引用项目内任何历史分析文档。
```

**竞争/拐点型公司**（如本地生活、补贴战后修复）：必须含 **QoQ 对比表**（最新季 vs 上季），覆盖经营亏损、分部利润率、销售费用率等。

### 4. 术语表附录（必填）

在「证据来源」之后、「免责声明」之前，新增：

```markdown
## 附录：财报典型术语表
```

规则见 [glossary-template.md](glossary-template.md)：
- 只收录**本报告实际出现**的术语
- 每条：术语 | 英文全称 | 在本公司语境下的简要含义（可带最新数字）
- 按 7 类分组：财务指标、业务分部、运营竞争、产品战略、估值研究、监管治理、时间缩写
- 港股/中概额外覆盖：Non-IFRS、经调整净利润、WVR、SAMR 等（若出现）

### 5. 更新 _sidebar.md

在「最新分析」列表添加链接；文件名 `yyyy-MM-dd`，链接标题 `yyyyMMdd`。

---

## 估值与决策

- 至少 2–3 种估值方法 + 概率加权情景（牛/基/熊）
- **IRR 铁律**：做多 ≥15% 才推荐买入；未达门槛 → PASS 或标注 Action Price 等待
- Action Price 推导顺序：**独立估值区间 → 减 15–20% 安全边际 → 再对比现价**
- Variant View 三段式：市场共识 ___ / 我们的观点 ___ / 为什么可能错 ___

---

## 反偏见（执行时必做）

- 搜索并写入至少 2 条 bear case（如 Compounder Fund 式 sell thesis）
- 估值给区间，非单点
- Pre-Mortem 3 条失败路径
- 🔴/🟡/✅ 红旗检查

---

## 证据来源表

| # | 来源 | 链接 | 类型(一手/事实/观点) | 摘要 |

全报告至少 3 条**一手**、核心数字必须追溯**事实**来源。

---

## 检查清单

- [ ] 未读 analysis_2026/、analysis/ 或项目内公司文档
- [ ] 关键数据有外部来源；QoQ/YoY 与共识 beat/miss 已写清
- [ ] 开头有推荐动作、信心、Action Price、Kill Condition
- [ ] Variant View 与 Key Forces 一致
- [ ] **附录术语表**已写，术语均出自本报告
- [ ] 报告已保存；_sidebar.md「最新分析」已更新
- [ ] 决策与估值、IRR 门槛一致

---

## 参考文件

- 报告骨架：[report-template.md](report-template.md)
- 术语表规则与分类：[glossary-template.md](glossary-template.md)
