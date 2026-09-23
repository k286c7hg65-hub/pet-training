# PET 训练场

剑桥 **B1 Preliminary（PET）** 写作与口语练习工具。给孩子在家练，不用买账号、不用装 App。

线上：https://k286c7hg65-hub.github.io/pet-training/

## 它做什么 / 不做什么

**做**：出题、计时、写、自评、记录进度。
**不做**：批改和口语对话——那两步在飞书里找 Ariste。这样页面本身**零凭据**，公开挂着也不怕。

阅读和听力没做：那两块用现成真题 App 刷效率最高，agent 帮不上忙。

## 三个部分

**写作**（对应官方 Paper 2）
- 7 道题：3 封回信（Part 1）+ 2 篇文章 + 2 个故事（Part 2）
- 计时 20 分钟（官方两张卷共 45 分钟）
- 实时字数：80–125 词算刚好；太短或太长按官方说明提示风险
- 写完先自己按**官方四项**打分（Content / Communicative Achievement / Organisation / Language，各 0–5），每档给儿童化解释，并提示「想多拿 1 分要做什么」
- 一键复制成批改请求，粘到飞书给 Ariste

**口语**（对应官方 Paper 4，四部分时长按官方）
- Part 1 考官问答 2 分钟｜Part 2 描述照片 3 分钟（独白约 1 分钟，站内 4 张练习图抽签）｜Part 3 商量讨论 4 分钟｜Part 4 聊开 3 分钟
- 页面负责抽图和计时；对话在飞书里练

**赛季数据**：练习篇数、口语次数、连续天数、四项自评均分、最近 12 篇明细。

## 数据与隐私

全部存在浏览器 localStorage（键 `pet-buddy-v1`）。没有服务器、没有账号、没有埋点、不收集任何个人信息。
「赛季数据」页可以导出备份、也可以一键清空。

## 来源

- 评分标准与考试结构：Cambridge English **B1 Preliminary Handbook for Teachers**（官方 PDF，2026-09-23 实抓），四项描述符逐字抄录见 `../pet-rubric.json`
- 题目：仿官方题型的**自编模拟题**，不是真题。真题请用剑桥官方 Sample Papers
- 口语练习图：AI 生成的示意图，不是官方素材

## 技术

单文件 `index.html`（内联 CSS/JS，系统字体，零外链、零 CDN）。四张练习图是 WebP，共约 650KB。
部署到 GitHub Pages（`k286c7hg65-hub/pet-training`，main 分支根目录）。

## 本地改完怎么发

```bash
python3 /home/gem/.openclaw/workspace/projects/pet-agent/deploy.py
```

部署脚本会：建仓（幂等）→ 推送 → 开 Pages → 轮询到线上 200。
⚠️ GitHub Pages 边缘缓存 `max-age=600`，改动后约 10 分钟内可能仍看到旧版；验收时给 URL 加 `?t=<时间戳>` 绕开缓存。
