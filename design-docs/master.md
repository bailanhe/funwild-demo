# Funwild 跨平台产品设计规格 V1 · 主文档

> 版本 V1 · 2026-05-14 · 何柏岚 起草
>
> 本文档是 Funwild 微信小程序 + Website 双端产品的完整设计规格。**输入**为 BP V7（业务方向）+ `brand_design/` design system（视觉资产）。**输出**为可直接对接 Figma、PRD、前端开发、产品 roadmap 的实施级文档。

---

## 0. 这份文档是什么 · 这份文档不是什么

### 是什么
- **跨平台 interaction 与 IA 决策**——双端任务边界、用户流动、page-level 状态机
- **17 个核心页面的 wireframe 级文字稿**——可在 10 分钟内对接 Figma low-fi
- **MVP 切分逻辑**——理想态（用户价值倒推）vs 现实态（团队产能反推），gap 即资源缺口
- **与 brand_design/ 的衔接规则**——不重新定义视觉，只决定 theme 如何分配、interaction 如何引用 token

### 不是什么
- **不是 BP V7 的替代品**——商业、法律、财务、团队分工以 BP 为准
- **不是视觉设计稿**——色彩 / 字体 / spacing / radius 全部以 `brand_design/shared-tokens.jsx` 为 SoT
- **不是研发文档**——技术选型、数据库 schema、API 设计不在本规格范围
- **不是营销文案**——海报、推送、push 文案的语气在 § 8 给方向，不给逐条文案

---

## 1. 全部 14 子文档索引

| 序号 | 文档 | 一句话 abstract | 主要读者 |
|---|---|---|---|
| 01 | [part_01_positioning.md](./part_01_positioning.md) | Funwild 不是 OTA，是"以滑雪为入口的华人户外身份与关系网络"。攻略是钩子，关系是产品，身份是护城河。 | 全员 |
| 02 | [part_02_user_personas.md](./part_02_user_personas.md) | 6 类用户 × 13 子细分。两条核心用户线（本地华人雪友 / 国内来欧游客）共享平台但**永远不应该看到同一个首页**。 | 产品、设计、运营 |
| 03 | [part_03_cross_platform_strategy.md](./part_03_cross_platform_strategy.md) | 小程序 = 关系层 + 30 秒到 3 分钟 session。Website = 决策层 + 5 到 25 分钟 session。两端共享数据，分裂体验。 | 产品、前端、SEO |
| 04 | [part_04_cross_platform_journey.md](./part_04_cross_platform_journey.md) | 3 条主 journey（国内游客 / 本地雪友 / 教练入驻）的逐步拆解。每个 CTA 配状态地图 + drop-off 估计。 | 产品、运营、增长 |
| 05 | [part_05_information_architecture.md](./part_05_information_architecture.md) | 三套 IA：小程序 5 tab、Website 6 主导航、Mobile Web 折叠抽屉。小程序 tab bar 把"出行"独立、把"雪场/教练/活动/地接"合并到"探索"。 | 产品、设计 |
| 06 | [part_06_page_ux/](./part_06_page_ux/) | 17 个核心页面 wireframe 级文字稿。每页含：页面目标 / 用户心理 / Primary CTA / States / Trust signals / Micro-interactions / 分享机制。 | 设计、前端 |
| 07 | [part_07_conversion_funnel.md](./part_07_conversion_funnel.md) | 5 大转化漏斗 + Year 1 目标转化率。最重要的是 7 天 retention loop（push → 打开 → 拼车 → 打卡 → 徽章 → 海报 → 朋友圈）。 | 增长、运营 |
| 08 | [part_08_social_community.md](./part_08_social_community.md) | 4 大社交机制（徽章 / 海报 / 拼车关系链 / 隐性 UGC）。用户从不"发动态"，动态是行为副产品。 | 产品、运营 |
| 09 | [part_09_trust_safety.md](./part_09_trust_safety.md) | "信任来自留痕，不来自承诺。"教练 / 地接的认证不是 badge，是行为轨迹。GDPR 与微信审核合规章节。 | 产品、法律 |
| 10 | [part_10_wechat_constraints.md](./part_10_wechat_constraints.md) | 微信生态 10 条硬约束 + interaction-level 解法表。订阅消息 / 分享 / 支付 / 登录 / 跳转。 | 前端、产品 |
| 11 | [part_11_seo_content.md](./part_11_seo_content.md) | URL 结构、SEO 优先级、Programmatic SEO 模板、小红书导流落地页策略。Website 不是 landing page，是 SEO 资产。 | 增长、内容 |
| 12 | [part_12_design_system.md](./part_12_design_system.md) | 不重新定义视觉。只解决：3 theme pack 如何分配（Sunset 小程序 / Pine Website 公开 / Indigo B2B） + interaction 与 token 的衔接规则。 | 设计、前端 |
| 13 | [part_13_engineering_aware.md](./part_13_engineering_aware.md) | 工程难度地图 + 不应该做的过度工程。Year 1 用 REST + 单体 + 第三方 CMS，不做微服务 / GraphQL / SSR。 | 研发、产品 |
| 14 | [part_14_mvp_strategy.md](./part_14_mvp_strategy.md) | 理想 MVP（用户价值倒推）13 个 P0 功能。现实 MVP（团队产能反推）8 个。Gap 即设计师 / 内容 / 前端 / 后台四个产能缺口。 | 全员 |
| 15 | [part_15_final_deliverables.md](./part_15_final_deliverables.md) | 8 项关键产出：onboarding flow / 3 大 conversion 页 / 5 大 UX failure / retention loop / network effect / viral 机制 / 优先开发 / 避免过度设计。 | 全员 |

---

## 2. 读者地图

按你的角色直接跳转到该读的章节，**不需要从头读到尾**。

| 角色 | 必读 | 选读 | 跳过 |
|---|---|---|---|
| **产品负责人（何柏岚）** | 全部 | — | — |
| **主开发（杜蕊珈）** | 01 / 03 / 05 / 06 / 10 / 13 / 14 | 02 / 04 / 07 / 12 | 08 / 09 / 11 / 15 |
| **技术运营（陆洲）** | 03 / 10 / 13 / 14 | 06 / 07 | 其他 |
| **运营负责人（贺安祺）** | 01 / 02 / 04 / 07 / 08 / 09 | 06 / 15 | 10 / 13 / 14 |
| **内容（欧根）** | 02 / 04 / 11 | 01 / 07 / 08 | 其他 |
| **商务（磊子 / 詹敏杰）** | 01 / 02 / 09 / 14 / 15 | — | 06 / 10 / 12 / 13 |
| **设计（洪玮瑢）** | 02 / 05 / 06 / 12 | 08 | 10 / 13 / 14 |
| **B-kuh 对接（乔宇辰）** | 01 / 09 / 11 / 14 | 02 | 其他 |
| **法律 / Steuerberater** | 01 / 09 / 10 | — | 06 / 11 / 12 / 13 |

---

## 3. 跨章节决策摘要（10 条强主张）

下面 10 条是本规格的"宪法"——任何子文档的局部建议都不能违背。如果违背，要么修改子文档，要么修改这里。

| # | 主张 | 出处 |
|---|---|---|
| S1 | Funwild 的产品本质是"华人滑雪身份系统 + 信任型 marketplace"，不是 OTA / 攻略站 / 社区。 | 01 |
| S2 | 小程序与 Website 是两端不同心智，不是同一产品的两个壳。共享数据、分裂体验。 | 03 |
| S3 | MVP 围绕"3 个月内能完成的最小 retention loop"切，不是"上线日清单"。 | 14 |
| S4 | 两类用户共享平台，但入口、首页、推送策略完全不同。永远不应该看到同一个首页。 | 02 |
| S5 | 信任来自留痕，不来自承诺。教练 / 地接的认证 = 行为轨迹，不是 badge。 | 09 |
| S6 | 不做"全功能首页"。首页是意图分流器，不是功能展示橱窗。 | 06 |
| S7 | 徽章系统是 retention engine，不是装饰。必须前置进 onboarding。 | 08 |
| S8 | 拼车功能在 Year 1 决定生死。比雪搭子至少好 3 倍：自动匹配 + wave + 信用分。 | 06 / 08 |
| S9 | 徽章 + 海报必须好看到"用户分享出去就是品牌曝光"。不靠邀请码裂变。 | 08 / 15 |
| S10 | 不做"动态/瀑布流/信息流"。动态是用户行为的副产品，不是 UGC 产品。 | 06 / 08 |

---

## 4. Theme Allocation 锁定决策

| 表面 | Theme | 不可逆 |
|---|---|---|
| 小程序主体 UI | **Sunset**（默认）+ 用户可切 Pine | ✓ 锁定 |
| 小程序 dark mode | Sunset.dark / Pine.dark | ✓ 锁定 |
| Website 公开内容（攻略 / SEO / 社区） | **Pine** | ✓ 锁定 |
| Website 商业页面（招商 / 品牌方 / 后台） | **Indigo** | ✓ 锁定 |
| 海报 / UGC 物料 | **Sunset** + 真实雪山照片背景 | ✓ 锁定 |
| 徽章插画 | 独立色票，跨 theme 不变 | ✓ 锁定（既定） |
| Pitch deck / 投资材料 | Sunset 主、Indigo 辅 | ✓ 锁定 |

切换规则在 [part_12_design_system.md](./part_12_design_system.md) § 3。

---

## 5. 与 BP V7 的差异说明

本规格在以下 5 处与 BP V7 不一致。每处都标注理由。若 BP 后续版本采纳本规格，需在 BP V8 中显式修订。

| BP V7 立场 | 本规格立场 | 理由 |
|---|---|---|
| 小程序底部导航 5 项 = 雪场 / 教练 / 活动 / 地接 / 我的（暗示），首页入口"其余" | 5 tab = 首页 / 出行 / 探索 / 消息 / 我的。雪场/教练/活动/地接合并到"探索" | S6 + S8：首页是分流器；拼车独立成 tab 才能驱动 retention loop |
| 教练入驻"€99/年 + 认证 badge" | 教练页**不显示** "认证 badge"，显示真实雪场打卡轨迹 + 24h 回复率 + 学员头像列表 | S5：留痕信任 > 承诺信任 |
| "联系教练 → 跳转微信" | wave 机制：用户发 wave → 教练回 wave → 才打开微信 | 防教练被骚扰 + 平台留住评价数据 |
| "活动报名 → 占位 + 客服线下收款" | 同 + **未付款的位置 24h 内自动释放**，避免假占位 | 防恶意抢位 |
| 徽章 142 个全量上线 | Year 1 上线 50 个 + V1.1 补到 100 + Year 2 满 142 | 设计 / 测试 / 内容产能限制 |

---

## 6. 术语表（中英对照）

| 术语 | 中文 | 英文 | 定义 |
|---|---|---|---|
| **CTA** | 行动召唤 | Call to Action | 用户在页面上被引导执行的具体动作（点按钮、扫码、报名等）。**Primary CTA** = 该页面的最重要行动；**Secondary CTA** = 次要行动。 |
| **IA** | 信息架构 | Information Architecture | 内容的组织结构、导航、命名、分类。本规格指 sitemap + 导航 + 分类规则。 |
| **wave** | 挥手 / 意向 | wave | 用户对教练 / 拼车伙伴发起的"我对你感兴趣"信号。**双向 wave** 后才打开微信。降低双方 friction。 |
| **habit loop** | 习惯回路 | Habit Loop | Cue（信号）→ Routine（动作）→ Reward（奖励）的循环。Funwild 的 habit loop 是"周三推送 → 打开看动态 → 发拼车 → 周末打卡 → 解锁徽章 → 朋友圈分享"。 |
| **KPI** | 关键指标 | Key Performance Indicator | Year 1 的 KPI 见 BP V7 § 1.5。 |
| **MAU / DAU** | 月活 / 日活 | Monthly / Daily Active Users | 一个月 / 一天内打开过小程序的独立用户数。 |
| **drop-off** | 流失点 | Drop-off Point | 用户在 funnel 某一步退出的比例。本规格估计了 5 大漏斗的 drop-off %。 |
| **conversion funnel** | 转化漏斗 | Conversion Funnel | 用户从入口到目标动作的多步流程，每步会有流失。 |
| **retention loop** | 留存循环 | Retention Loop | 让用户回来的机制。Funwild 的 retention loop 单次循环 = 7 天。 |
| **network effect** | 网络效应 | Network Effect | 用户越多，产品价值越高。Funwild 的 NE 来自拼车关系链。 |
| **viral growth** | 病毒增长 | Viral Growth | 用户主动分享带来新用户的增长。Funwild 的 viral 机制 = 海报。 |
| **onboarding** | 新手引导 | Onboarding | 用户首次打开到完成首个动作的流程。Funwild 的 onboarding < 30 秒。 |
| **UGC** | 用户产生内容 | User-Generated Content | 用户发布的内容。Funwild 的 UGC = 打卡 / 评价 / 行后攻略。 |
| **deep link** | 深链 | Deep Link | 直接跳到 app 内特定页面的链接。Website 扫码 → 小程序特定页用 deep link。 |
| **eyebrow** | 眉标 | Eyebrow Label | 标题之上的小字标签。例："SNOW REPORT · 今日"。本规格里全部用 micro 字号 + Geist Mono。 |
| **SoT** | 唯一可信源 | Source of Truth | 同一数据 / 决策的唯一权威来源。视觉 SoT = `brand_design/`；业务 SoT = BP V7。 |

---

## 7. 版本日志

| 版本 | 日期 | 主要变化 | 撰写人 |
|---|---|---|---|
| V1.0 | 2026-05-14 | 首版。基于 BP V7 + brand_design/ 输出 15 part + 17 page UX wireframe + theme allocation。 | 何柏岚 |

---

## 8. 接下来 4-6 周的验证计划

按 plan § 19.2 执行：

| 周次 | 动作 | 负责人 |
|---|---|---|
| 第 1 周 | 把 part_01 + part_02 发给 5 个本地华人雪友（N47 核心成员），收"哪句不对" | 贺安祺 |
| 第 2 周 | 把 part_04 Journey A 发给 3 个国内来欧洲滑过的人，收"哪一步你会退出" | 何柏岚 |
| 第 3 周 | 把 part_06 教练详情页 + part_02 § 3.3 教练 persona 发给 3 个教练，收"你愿意上来吗" | 磊子 |
| 第 4 周 | 把首页 + 雪场详情页 + 教练详情页做成 Figma low-fi，5 个用户点击测试 | 洪玮瑢 + 何柏岚 |
| 第 5-6 周 | 根据反馈出 V1.1，进入开发交底 | 全员 |

---

接下来逐 part 展开：先读 [part_01_positioning.md](./part_01_positioning.md)。
