# Part 13 · Engineering-aware Product Design · 工程难度地图

> 不应做的过度工程 · MVP 必须 vs 可延后 · 关键 mitigation

---

## 0. 核心命题

> **产品设计要懂工程边界。Year 1 团队 = 杜蕊珈 + 陆洲（2 人），开发 5 个月。**

任何"听起来不错但工程量爆炸"的功能，都必须在产品决策阶段砍掉，而不是在开发中砍掉。

---

## 1. 工程难度地图（按功能）

### 1.1 难度分级
- ★ 极简（1-3 天）
- ★★ 简单（1 周）
- ★★★ 中等（2-3 周）
- ★★★★ 复杂（1 月+）
- ★★★★★ 极难（需要新岗位 / 新基础设施）

### 1.2 全功能难度表

| 功能 | 难度 | 关键依赖 | Year 1 决策 |
|---|---|---|---|
| 18 雪场静态攻略 | ★ | 静态 CMS（Notion / Webflow 兜底） | ✅ MVP |
| 用户系统 + 微信登录 | ★★ | 标准 OAuth | ✅ MVP |
| 微信小程序基础架构（uni-app / Taro） | ★★ | 框架熟悉度 | ✅ MVP |
| Website SSR | ★★★ | Next.js / Nuxt | ✅ MVP（攻略页核心） |
| 徽章系统 + 解锁触发 | ★★ | 后端 cron + event | ✅ MVP |
| 海报生成（服务端 canvas） | ★★★ | Puppeteer 或 node-canvas + queue | ✅ MVP |
| GPS 打卡 | ★★ | wx.getLocation + 雪场坐标库 | ✅ MVP |
| 拼车 CRUD | ★★ | 标准 CRUD | ✅ MVP |
| 拼车自动匹配 | ★★ | 简单 SQL 查询（无需 ML） | ✅ MVP |
| 教练 / 地接 CRUD | ★★ | 标准 CRUD | ✅ MVP |
| 全局搜索 | ★★ | SQL LIKE（Year 1）/ Algolia（Year 2） | ✅ MVP（粗糙版） |
| 消息系统 + Wave | ★★★ | 不需要 websocket，轮询足够 | ✅ MVP |
| 微信服务号 + 订阅消息 | ★★ | 模板申请 + cron job | ✅ MVP |
| 后台审核（活动 / 教练 / 地接） | ★★★ | 标准后台 + Headless CMS | ✅ MVP |
| 评价系统（只读 V1.0） | ★ | 数据库展示 | ✅ MVP |
| 评价系统（写入 V1.1） | ★★ | 关键词过滤 + 审核 | ⚠ V1.1 |
| 关注 / 被关注 | ★★ | 标准社交图 | ⚠ V1.1 |
| 关注的人动态流 | ★★★ | timeline 算法 | ⚠ V1.1 |
| 公开个人主页（Website） | ★★ | SSR 静态化 | ⚠ V1.1 |
| 雪场实时雪况 API | ★★★ | 接 OpenWeatherMap / Bergfex | ⚠ V1.1 |
| 推荐系统（个性化） | ★★★★ | 推荐算法 | ❌ Year 2 |
| 站内支付 | ★★★★ | 微信支付商户号 + 资金合规 | ❌ Year 2 |
| 实时 GPS 轨迹（Strava-style） | ★★★★★ | 需要原生 app | ❌ Year 3 |
| 个性化首页 | ★★★★ | 实时计算 + cache | ❌ Year 2 |
| 多语言 i18n | ★★★ | i18n 架构 + 翻译产能 | ❌ Year 2 |
| 互动雪场地图 | ★★★★ | GIS + 自定义 SVG | ❌ Year 2 |
| 内容社区 / 信息流 | ★★★★★ | 算法 + 内容审核 + UGC 激励 | ❌ Year 3 |
| 站内私信（用户间） | ★★★ | websocket + 离线消息 | ❌ Year 2 |
| 二手市集（完整版） | ★★★ | 信用 + 评价 + 举报 | ⚠ V1.2 |

---

## 2. 容易延期的功能 · 必须前置 mitigation

### 2.1 海报生成（服务端 canvas）

**风险**：用户在打卡瞬间触发生成 → 服务端 canvas 卡死 → 用户等待 30+ 秒

**Mitigation**：
- 队列异步化（Bull / RabbitMQ）
- 客户端先显示"海报正在生成"loading + 完成后 push 通知
- 缓存常用模板的中间结果

### 2.2 拼车自动匹配 + 周三晚 push

**风险**：周三 20:00 全平台用户同时收到 push → 同时打开小程序 → 数据库查询打爆

**Mitigation**：
- 周三晚分批 push（每 5 分钟 100 用户）
- 拼车列表查询走 Redis cache（5 分钟刷一次）
- 数据库 read replica

### 2.3 教练日程发布

**风险**：教练（特别是兼职 3B）懒得维护"本周行程"，导致页面信息过时

**Mitigation**：
- 行程发布**极简**（3 步内）
- 周日晚自动 push "发布你的本周行程"
- 7 天未更新 → 页面顶部 hint "本周行程待更新"（不下架）

---

## 3. Year 1 不应该做的"过度工程"

| 不做 | 原因 | Year 1 替代 |
|---|---|---|
| **GraphQL** | REST 足够 + 团队不熟 | REST API |
| **微服务** | 用户量小 + 运维复杂 | 单体 Node.js / Python |
| **小程序原生开发（无框架）** | 工程量大 | uni-app / Taro |
| **自建数据看板** | 工程量大 | Mixpanel / Metabase 第三方 |
| **自建 search engine** | Algolia 太贵 | SQL LIKE（Year 2 升级） |
| **A/B test 平台** | 用户量不够 | 简单分流脚本 |
| **K8s** | 流量小 | 单服务器 + Docker |
| **CDN 自建** | Year 1 流量低 | 阿里云 / 七牛 CDN |
| **机器学习** | 数据少 | 规则 |

---

## 4. Year 1 推荐技术栈

### 4.1 前端

- **小程序**：uni-app（Vue 3 + 跨平台）
- **Website**：Next.js（React + SSR + SEO 友好）
- **设计 token**：CSS Custom Properties + 自动生成 less / sass

### 4.2 后端

- **语言**：Node.js（TypeScript）
- **框架**：NestJS 或 Express
- **数据库**：PostgreSQL
- **缓存**：Redis
- **队列**：Bull (Redis-backed)
- **文件存储**：阿里云 OSS（图片 / 海报）

### 4.3 第三方服务

| 服务 | 用途 |
|---|---|
| 微信小程序 + 服务号 | 登录 / push |
| Mixpanel / Amplitude | 用户行为分析 |
| Sentry | 错误监控 |
| Cloudflare（Year 2） | CDN + DDoS |
| Mailgun / SES | 系统邮件 |

### 4.4 后台 / CMS

- **后台**：Strapi 或 NocoBase（headless CMS）
- 节省 14 个子模块的开发量（约 60% 时间）

---

## 5. 数据库 schema 关键决策

### 5.1 用户系统

```
users (
  id, openid, nickname, avatar,
  city, sport_pref, level_pref,
  created_at, updated_at, deleted_at
)
```

### 5.2 内容系统

```
resorts (id, slug, country, name, ...)
coaches (id, slug, user_id, status, ...)
activities (id, slug, organizer_id, ...)
outfitters (id, slug, status, ...)
```

### 5.3 行为系统

```
checkins (user_id, resort_id, timestamp, gps)
badges_unlocked (user_id, badge_id, unlocked_at)
follows (follower_id, followee_id, created_at)
waves (sender_id, receiver_id, type, status, created_at)
carpools (organizer_id, resort_id, date, status)
carpool_members (carpool_id, user_id, status)
```

### 5.4 关键 index

- 拼车列表查询 → `carpools.date + status` 复合 index
- 雪场打卡 → `checkins.resort_id + user_id` 复合
- 关注流 → `follows.follower_id` index

---

## 6. 性能预算

| 指标 | Year 1 预算 |
|---|---|
| 小程序冷启动 | < 2s |
| 首页加载 | < 1s（80% 缓存命中） |
| 雪场详情页加载 | < 1.5s |
| 海报生成 | < 5s（异步） |
| 搜索响应 | < 500ms |
| Website 攻略页 LCP | < 2.5s |
| Website 首屏 | < 1s（SSR） |

---

## 7. 安全工程

### 7.1 数据加密
- 数据库 at-rest 加密
- 传输 TLS 1.2+
- 用户密码不存（OAuth only）
- 敏感字段（手机号 / 真实姓名）字段级加密

### 7.2 防滥用
- API rate limit（每 IP 每分钟 60 次）
- 验证码（关键操作 + 异常 IP）
- 用户行为反作弊（刷代金券检测）

### 7.3 隐私
- 日志脱敏（手机号 / 邮箱替换）
- GDPR 数据导出 + 删除接口

---

## 8. 部署 / DevOps

### 8.1 Year 1 基础设施

- **服务器**：1 个 Linux VPS（4 core 8GB），€50/月
- **数据库**：托管 PostgreSQL（DigitalOcean / Hetzner）
- **CDN**：阿里云 / 七牛
- **域名 + DNS**：Cloudflare

### 8.2 部署流程

- Git 主分支自动部署到 staging
- 手动 promote 到 production
- 数据库迁移用 Knex / Prisma
- 监控：Sentry + Uptime Robot

### 8.3 备份

- 数据库每日自动备份 + 异地存储
- 用户上传图片 OSS 自动多 region

---

## 9. 团队工程产能反推

### 9.1 杜蕊珈（主开发，全职 5 个月）

5 个月 × 20 工作日 × 8 小时 = 800 小时

| 任务 | 工时估计 |
|---|---|
| 项目初始化 + 架构 | 80 |
| 用户系统 + 登录 | 60 |
| 雪场 / 教练 / 活动 / 地接 CRUD | 200 |
| 拼车 + Wave | 100 |
| 徽章 + 打卡 | 80 |
| 海报生成 | 80 |
| 消息系统 + push | 60 |
| 后台审核 | 80 |
| Bug 修复 + 优化 | 60 |
| **小计** | **800** |

→ **杜蕊珈 5 个月正好够 V1 必须功能**，几乎没有 buffer。

### 9.2 陆洲（辅助 + AI + 数据，兼职 50% × 5 个月）

5 个月 × 20 × 4 = 400 小时

| 任务 | 工时估计 |
|---|---|
| LLM 起草雪场攻略 | 60 |
| LLM 优化 / programmatic SEO 内容（V1.1） | 80 |
| 数据看板配置 Mixpanel | 40 |
| Sentry 配置 + 错误监控 | 20 |
| 雪场坐标库 + 第三方雪况 API | 60 |
| AI 客服 prompt 调优（V1.1） | 60 |
| 帮助主开发联调 | 80 |
| **小计** | **400** |

→ 陆洲产能用于"辅助 + AI 加速"，不分担主开发。

### 9.3 Website 工程缺口

主开发杜蕊珈忙小程序 + 后台，**Website 谁来开发？**

→ Year 1 用 Notion / Webflow / Astro 静态站兜底，Year 1 末转 Next.js 自建。

---

## 10. 工程风险红线

| 风险 | 影响 | 红线 |
|---|---|---|
| 主开发离职 / 病假 | Year 1 上线延期 | 必须有 Stille Beteiligung（已签） + 备份 |
| 设计师产能不足 | UI / 海报延期 | 必须 5 月签 + AI 打底 |
| 内容产能不足 | 雪场攻略不全 | 必须团队众包 |
| 微信审核被拒 | 上线延期 1-2 月 | 严格合规审查 |
| 服务器爆掉 | 用户体验差 | Auto scaling 准备 |

---

## 11. Year 2+ 工程演进

| 阶段 | 升级 |
|---|---|
| Year 2 Q1 | 上 Algolia 搜索 |
| Year 2 Q2 | 站内支付（微信支付）|
| Year 2 Q3 | 推荐系统（基于规则 → 简单协同过滤） |
| Year 2 Q4 | 多语言 i18n |
| Year 3 | 原生 app（iOS / Android）|
| Year 3+ | 互动雪场地图 + 实时 GPS |

---

## 12. 工程哲学

> **Year 1 做对的事，不做"完美的事"。**

- 选成熟技术，不追新
- 用第三方服务，不自建
- 写直白代码，不过早抽象
- 监控 + bug fix 优于 feature
- 让产品上线 > 让代码完美

---

→ 下一篇：[part_14_mvp_strategy.md](./part_14_mvp_strategy.md) MVP 切分策略。
