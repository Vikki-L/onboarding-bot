# 01 · Problem & Context

## 🌍 Business Context

一个北美 AI 教育出海产品的获客模式：**雇佣 600+ 北美校园大使** 在 TikTok / Instagram / YouTube 拍短视频。每月有持续的**新大使入职**——需要 Onboarding 团队走完完整的入职流程后，新人才能开始拍视频。

## 🎯 The Concrete Problem

### Painpoint A · 人工 DM 一对一是死循环

新人入职原本依赖 **Onboarding 团队人工 DM**：

```
收候选人邮件 → 在 Discord 上 DM 他确认身份
   ↓
让他改昵称（按内部规范）
   ↓
手动给他加 role（解锁对应频道）
   ↓
手动拉他进对应 Coach 的小组群
   ↓
发欢迎消息 + 介绍任务流程
   ↓
回答他的常见问题（"什么是 template？"、"怎么提交视频？"...）
   ↓
跟进他是否完成首次视频提交
```

每月新人 N 个 → Onboarding 团队**完全被这条链路淹没**。

### Painpoint B · Discord 平台的特殊难点

之前的 Onboarding 流程在 **Slack** 上跑——Slack 有邮箱即身份的映射，候选人填邮箱注册 = 自动知道是谁。

但**迁移到 Discord 后**：
- Discord 没有"邮箱注册"机制
- 加入服务器只能看到一个匿名的 Discord 账号名
- Bot **不知道谁是谁** → 没法自动做任何事

→ Discord 平台对 Onboarding 自动化最大的卡点 = **身份识别**。

### Painpoint C · FAQ 问烂了

新人入职常见问题就那几个，但每个新人都要问一遍：
- "什么是 template？怎么找？"
- "怎么提交视频？"
- "我什么时候能拿到第一笔钱？"
- "我的 Coach 是谁？"

Onboarding 团队每天回答同样的问题 N 次。

## 🔍 What I Set Out To Build

不是"做一个简单的 welcome bot"，而是一套**完整的入职自动化系统**：

1. **解决身份识别**：用邀请码机制实现 Discord 的身份映射
2. **自动化全流程 5 步**：识别 → 改昵称 → 加角色 → 拉群 → 发欢迎
3. **FAQ 智能问答**：把人工回答的高频问题交给 Bot
4. **状态持久化**：Bot 挂了重启不丢任何人
5. **数据驱动二期优化**：用历史 Slack 消息聚类找出真正的 FAQ → 不是拍脑袋设计知识库

## 🧠 Key Design Decisions

| 决策 | 理由 |
|------|------|
| **邀请码识别身份**（一次性 + 限时过期 + 与候选人一对一）| 这是 Discord 平台没有邮箱映射的唯一解 |
| **状态持久化（json）** | Bot 挂了重启不丢人——这是 Onboarding 类 Bot 的生死线 |
| **知识库分两层**（自动 FAQ + 转人工兜底） | 不是所有问题 Bot 都能答，必须有"转人工"兜底 |
| **二期需求基于数据聚类**（不是拍脑袋）| 历史 Slack 消息能告诉你真正高频的 FAQ 是什么 |

---

[← Back to README](../README.md)
