# Part 15 · 最终交付清单 · Final Deliverables

> 8 项关键产出 · 一表看清全部规格

---

## 1. 最合理的 Onboarding Flow

> **< 30 秒 · 完成率 ≥ 75%**

```
Step 1 微信一键登录（无 UI）
  ↓
Step 2 欢迎屏 "你好 张小美" + 趣野 logo（5s）
  ↓
Step 3 滑动选择 · "你滑哪种？" [单板] [双板] [都滑] [还不知道]
  ↓
Step 4 滑动选择 · "你在欧洲哪里？" [慕尼黑] [其他德国] [奥地利] [瑞士] [其他] [国内来玩]
  ↓
Step 5 解锁动画 · "趣野新人" 徽章 + "下一步：第一次打卡解锁'首次出发'"
  ↓
Step 6 首页 + spotlight · "本周末 5 位雪友计划去 Spitzingsee → 详情"
```

详见 [part_06_page_ux/15_onboarding.md](./part_06_page_ux/15_onboarding.md)。

---

## 2. 最关键的 3 个 Conversion 页面

| 页面 | 角色 | 链接 |
|---|---|---|
| **雪场详情页** | 决定用户"来 / 再来" | [02_resort_detail](./part_06_page_ux/02_resort_detail.md) |
| **教练详情页** | marketplace 第一桶金来源 | [04_coach_detail](./part_06_page_ux/04_coach_detail.md) |
| **活动详情页** | N47 + 品牌方变现路径 | [06_activity_detail](./part_06_page_ux/06_activity_detail.md) |

→ 这 3 页是 Year 1 营收的"咽喉"。如果团队设计 / 开发产能不够，**这 3 页必须做到 100%**。其他页面可砍可简。

---

## 3. 最危险的 5 个 UX Failure Points

> 这 5 个错误任何一个出现，Year 1 可能崩盘。

| # | 失败 | 出现意味着 | 防御 |
|---|---|---|---|
| 1 | **小程序首页是 banner 轮播大杂烩** | 用户不知道下一步做什么 → 流失 | 首页 = 意图分流器（详见 part_06_page_ux/00_home.md） |
| 2 | **教练联系是直接微信** | 教练被骚扰 + 平台无评价数据 | Wave 机制（详见 part_06_page_ux/04_coach_detail.md） |
| 3 | **拼车是论坛贴** | 临时取消多 + 信任不建立 | wave + 信用分（详见 part_06_page_ux/09_carpool.md） |
| 4 | **徽章是 onboarding 后才知道的"成就系统"** | 用户已经流失 | 徽章前置 onboarding（详见 part_06_page_ux/15_onboarding.md） |
| 5 | **Website 是 landing page** | 没 SEO + 没攻略 + 没社区 → Year 1 - 5 复利资产 0 | Website SSR + 18 雪场 + 教练 profile + 公开主页（详见 part_11_seo_content.md） |

---

## 4. 最重要的 Retention Mechanism

### 7 天 Habit Loop

```
   ┌─→ Day 3 周三晚 8 PM push ───┐
   │                              ↓
   │                       Day 3-5 打开小程序看动态
   │                              ↓
   │                       Day 3-5 发拼车 / 加入拼车
   │                              ↓
   │                       Day 6-7 周末出发 → 打卡
   │                              ↓
   │                       Day 6-7 解锁徽章 → 海报
   │                              ↓
   └─ Day 7 朋友圈分享 → Day 1 朋友扫码 ─┘
```

**关键依赖**：
1. 周三晚 push 内容质量（个性化按用户级别 / 地域 / 历史）
2. 拼车密度（周末至少有 3-5 个不同雪场出行计划）
3. 打卡 friction 低（5km 内自动 hero）
4. 海报视觉天花板（不舍得删）

**单 loop 时间**：7 天 · **单 loop 完成率**：30% · **雪季内**：5-15 次 / 用户

→ 缺任何一步，loop 断。详见 [part_07_conversion_funnel.md](./part_07_conversion_funnel.md) § 6。

---

## 5. 最容易形成 Network Effect 的功能

### 拼车关系链 + 关注 + 动态流

```
用户 A 关注 5 人
  ↓
首页"关注的人动态"显示 5 人本周计划
  ↓
A 看到 B 计划周六去 Stubaier → 加入
  ↓
拼车成行 + 1 周后系统 push "互相关注吗？"
  ↓
默认双向 → A 关注变 6 人 + B 关注变 N+1 人
  ↓
每多 1 人，整个 network 更密
```

**网络效应飞轮**：
- 用户越多 → 拼车选择越多 → 留存越高 → 新用户越愿意来
- 唯一前提：单一雪场至少 3-5 个拼车候选（Year 1 末 1500 用户能达到）

详见 [part_08_social_community.md](./part_08_social_community.md) § 3。

---

## 6. 最适合 Viral Growth 的机制

### 海报体系

> **让用户分享出去就是品牌曝光。**

- 不是邀请码
- 不是裂变红包
- 不是"分享得奖励"

**4 类海报**：
1. 打卡海报（雪场图 + 用户头像 + 打卡数 + 二维码）
2. 徽章海报（大徽章 + 用户头像 + 解锁日期）
3. 拼车海报（雪场图 + 日期 + 还差 X 位）
4. 评价海报（教练头像 + 评价摘录）

**让海报好看到不舍得删**：
- 背景 = 真实雪场照片（雪场提供）
- 设计师产能投入这里（Year 1 必须）
- Sunset 主题色

详见 [part_08_social_community.md](./part_08_social_community.md) § 2。

---

## 7. 最应该优先开发的功能（Top 5）

按 **用户价值 × 工程难度** 排序：

| # | 功能 | 价值 | 难度 | 必须前置 |
|---|---|---|---|---|
| 1 | 微信登录 + onboarding | 极高 | ★★ | 一切的入口 |
| 2 | 雪场静态攻略（小程序内 + Website） | 高 | ★ | SEO + 决策 |
| 3 | GPS 打卡 + 徽章系统 | 极高 | ★★ | retention loop 核心 |
| 4 | 海报生成（2 模板首发） | 高 | ★★★ | viral growth |
| 5 | 拼车（发布 + 列表 + 微信跳转 V1.0） | 极高 | ★★ | network effect 起点 |

→ 这 5 个完成 = Year 1 V1.0 上线条件达到。

---

## 8. 最应该避免过度设计的功能（Top 5）

| # | 功能 | 为什么避免 | Year 1 替代 |
|---|---|---|---|
| 1 | **后台数据看板** | 工程量大 | Mixpanel + Metabase 第三方 |
| 2 | **推荐系统** | 用户量不够训练 | 规则替代 |
| 3 | **全局搜索"模糊匹配 / 拼音 / 同义词"** | 工程难 | SQL LIKE |
| 4 | **评价系统（写入功能）** | 教练 / 地接数量不够 | V1.1 再做，V1.0 只显示已有评价 |
| 5 | **个性化首页** | 实时计算工程难 | 规则分两套（本地华人 / 国内游客） |

详见 [part_13 § 3 不应该做的过度工程](./part_13_engineering_aware.md#3-year-1-不应该做的过度工程)。

---

## 9. 跨子文档关键 reference

| 想了解 | 看这里 |
|---|---|
| 产品本质 / 对标 / 护城河 | [part_01](./part_01_positioning.md) |
| 6 类用户 / 13 子细分 | [part_02](./part_02_user_personas.md) |
| 小程序 vs Website 边界 | [part_03](./part_03_cross_platform_strategy.md) |
| 3 条 user journey 完整步骤 | [part_04](./part_04_cross_platform_journey.md) |
| IA / sitemap / URL | [part_05](./part_05_information_architecture.md) |
| 17 个 page wireframe | [part_06_page_ux/](./part_06_page_ux/) |
| 5 大漏斗 + Year 1 KPI | [part_07](./part_07_conversion_funnel.md) |
| 4 大社交机制 + viral | [part_08](./part_08_social_community.md) |
| 教练 / 地接 / 用户信任 + GDPR | [part_09](./part_09_trust_safety.md) |
| 微信生态约束 + interaction 解法 | [part_10](./part_10_wechat_constraints.md) |
| Website SEO + 内容策略 | [part_11](./part_11_seo_content.md) |
| Theme allocation + 视觉系统 | [part_12](./part_12_design_system.md) |
| 工程难度 + 推荐技术栈 | [part_13](./part_13_engineering_aware.md) |
| MVP 切分 + 资源缺口 | [part_14](./part_14_mvp_strategy.md) |

---

## 10. 给团队各成员的 1 句话总结

| 角色 | 你最需要记住的 |
|---|---|
| **何柏岚（你）** | Funwild = 身份系统 + 关系网络，不是 OTA / 攻略站。所有 product decisions 以此为准。 |
| **磊子** | 教练 / 地接 / 品牌方的入驻必须易 + 信任来自留痕 + V1.0 接受 10 教练 / 5 地接 / 1 品牌方。 |
| **杜蕊珈** | 5 个月正好够 V1 必须功能。海报 / 拼车 / 徽章是 retention 三件套，必须做扎实。 |
| **陆洲** | 用 LLM + 第三方服务节省开发量。Year 1 不自建数据看板 / 推荐 / 搜索引擎。 |
| **贺安祺** | 客服 24h 内回复 = 类型 2 用户的命门。审核 24h 内 = 教练 / 地接 入驻保证。 |
| **欧根** | 18 雪场不要一次写完，先 10 雪场 + 雪季中补 8 个。每篇必含 ❗ 特别提醒。 |
| **詹敏杰** | 30+ 教练资源 1v1 沟通 + 首批 5-10 免费 + 用户绕单别管，让平台数据吸住教练。 |
| **洪玮瑢** | 5 月必须签 / 8 月必须完成 25 徽章 + 2 海报模板 + Logo 优化。设计师产能是 Year 1 关键瓶颈。 |
| **乔宇辰** | B-kuh 沟通 Year 1 是导流位 + 代金券机制。Year 2 才是真闭环。 |
| **法律 / Steuerberater** | N47 / Funwild / B-kuh 三实体边界 + GDPR + 微信审核合规。 |

---

## 11. 接下来 4-6 周的验证计划（重复 master.md）

按 [master.md § 8](./master.md#8-接下来-4-6-周的验证计划) 执行：

| 周次 | 动作 | 负责人 |
|---|---|---|
| 第 1 周 | 把 part_01 + part_02 发给 5 个 N47 核心，收"哪句不对" | 贺安祺 |
| 第 2 周 | 把 part_04 Journey A 发给 3 个国内来欧洲滑过的人 | 何柏岚 |
| 第 3 周 | 把 part_06 教练详情页 + part_02 § 3.3 发给 3 个教练 | 磊子 |
| 第 4 周 | 把首页 + 雪场详情 + 教练详情做成 Figma low-fi，5 个用户点击测试 | 洪玮瑢 + 何柏岚 |
| 第 5-6 周 | 根据反馈出 V1.1，进入开发交底 | 全员 |

---

## 12. 与 BP V7 的 5 处偏差总结（来自 master）

| BP V7 | 本规格 | 理由 |
|---|---|---|
| 小程序底部 5 = 雪场/教练/活动/地接/我的 | 5 tab = 首页/出行/探索/消息/我的 | 拼车独立成 tab 驱动 retention loop |
| 教练入驻 "认证 badge" | 教练页不显示 badge，显示行为轨迹 | "留痕信任 > 承诺信任" |
| 联系教练 = 跳微信 | wave 机制 | 防绕单 + 留住评价数据 |
| 报名 = 占位 + 客服收款 | 同 + 24h 未付款自动释放 | 防恶意抢位 |
| 徽章 142 个全量上线 | Year 1 50 个 + V1.1 100 + Year 2 满 | 设计 / 测试 / 内容产能 |

---

## 13. 结语

V1 共 15 部分 60,000+ 字 + 17 个页面 wireframe + 4 张主图 + 跨文档 reference。

预期使用方式：
- 团队每人**只读自己角色的章节**（master § 2 读者地图）
- Figma 设计师**直接对接 part_06**
- 杜蕊珈**直接拆 sprint 对接 part_13 + 14**
- 商务 / 运营**直接对接 part_07 + 08 + 09**

---

如果 Year 1 末 KPI 达到，说明本规格的判断是对的。
如果失败，本规格本身需要 V2 reflection（哪个 S1-S10 主张错了）。

**Funwild · 让我们在阿尔卑斯的雪山上相遇。**

—— 何柏岚 · 2026-05-14
