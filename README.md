# Onboarding Bot

> Discord Bot 5 步自动化新人入职 · 配套 Slack 数据分析 pipeline 反哺二期优化 · 让 Onboarding 团队从"人工 DM 一对一"中解放

🎯 这是 [Creator Ops Portfolio](https://github.com/Vikki-L/creator-ops-portfolio) 的精选独立项目。

---

## TL;DR

**Problem**：北美 AI 教育出海产品每月有大量新校园大使加入，原本 Onboarding 团队需要**人工 DM 一对一处理**（收集姓名 / 拉群 / 改状态 / 答 FAQ）。Discord 平台没有"邮箱即身份"的天然映射，是从 Slack 迁移过来后最大的卡点。

**Approach**：设计 Discord Bot 实现 _5 步自动化_（邀请码识别身份 → 改昵称 → 加角色 → 建私密频道 → 发欢迎消息）+ 知识库 FAQ 智能问答 + 状态持久化。二期优化基于一套完整的 Slack 历史消息分析 pipeline（用 LLM 聚类 FAQ）。

**Result**：

- ✅ Onboarding 团队**人工 DM 工作量显著下降**
- ✅ Bot 挂掉重启**不丢人状态**（持久化生效）
- ✅ 二期优化**有数据依据**（不是拍脑袋）

---

## 🏗️ Repo Structure

```
onboarding-bot/
├── README.md                          ← 你正在看
├── docs/
│   ├── 01-problem-and-context.md      ← Onboarding 痛点 + Discord 平台特殊难点
│   ├── 02-bot-design.md               ← 5 步自动化 + 邀请码机制 + 状态持久化
│   ├── 03-data-pipeline.md            ← ⭐ Slack 数据分析 pipeline · 二期数据依据
│   └── 04-results.md                  ← 业务影响 + 复盘
└── assets/                            ← (截图待添加)
```

> ⚠️ **Bot 代码与详细配置未公开**：Discord 邀请码生成机制、Bot 业务流程具体实现、Slack 历史消息原文等因含商业敏感性暂不在本仓库公开。本仓库以**设计方案 + 数据 pipeline 思路 + 业务影响**为主，可在面试时单独 demo。

---

## 📐 Bot Highlights

### 5 步自动化主流程

```
邀请码识别身份 → 改昵称 → 加角色 → 建私密频道 → 发欢迎消息
```

### 关键设计

| 设计 | 说明 |
|------|------|
| **邀请码识别身份机制** | 一次性 / 限时过期 / 与候选人姓名一对一映射，解决 Discord 没有邮箱映射的根本问题 |
| **状态持久化** | Bot 挂了重启也不丢人 |
| **完整 Onboarding 流程** | 邀请 → 身份确认 → 群组接入 → 任务说明 → FAQ 回复 → 首次视频提交 |
| **知识库智能问答** | 录入数据库，能智能回答大使的常见问题 |
| **与 Recruiting 系统衔接** | 候选人状态在两个系统间自动同步 |

### 二期数据驱动优化

为了知道二期"该优化什么"，我设计了一套 **Slack 历史消息分析 pipeline**：

```
拉取 Slack 数据 → 筛选 Onboarding 阶段 → 标注 → LLM 聚类 FAQ → 输出 dashboard
```

输出 FAQ 聚类成果 → **直接驱动二期 Bot 知识库内容**。详见 [docs/03-data-pipeline.md](docs/03-data-pipeline.md)。

---

## 💡 Key Insights from This Project

1. **平台特性差异**（Slack vs Discord）需要专门的迁移设计——Discord 没有邮箱映射这一条就改变了所有 Onboarding 流程
2. **状态持久化**是 Bot 类系统的生死线——挂一次没人状态就破产
3. **数据驱动优化** vs **拍脑袋优化**：差异在于"二期想做什么"是从历史消息聚类里跑出来的，不是拍脑袋猜的
4. **知识库 FAQ 智能问答**让 Bot 从"功能型工具"升级为"半个 Onboarding 助理"

---

## 👤 About

**LIU Zibing (Vikki)** · zibingl2@illinois.edu

- 🎓 UIUC Grainger College of Engineering · 金融工程硕士
- 💼 AI 教育出海产品 · 产品助理（2025.01 – 2026.06）
- 🐙 [Main Portfolio](https://github.com/Vikki-L/creator-ops-portfolio)

---

*Last updated: 2026-06-03*
