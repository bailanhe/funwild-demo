# Part 11 · SEO 与内容策略 · SEO & Content Strategy

> Website 不是 landing page · 是 Year 1 - 5 的复利资产 · 18 雪场攻略 + Programmatic SEO

---

## 0. 核心命题

> **Website ≠ landing page。**

Website 是 Year 1 - 5 的**复利 SEO 资产**：
- Year 1 投入：18 雪场 × 2,000 字攻略 + 5-8 横向专题 + URL 架构
- Year 2 收益：Google 长尾词排第一 + 小红书反向引流
- Year 5 复利：500-1000 篇内容 + 50%+ 自然流量

---

## 1. URL 结构（必须 Year 1 定下来）

```
funwild.com/
├── /                                  ← 首页
├── /resort/                           ← 雪场总览
│   └── /[country]/                    ← 国家
│       └── /[resort-slug]/            ← 雪场详情
│           └── /season-[year]/        ← 季节性 Programmatic
├── /coach/                            ← 教练总览
│   └── /[coach-slug]/                 ← 教练 profile
├── /activity/                         ← 活动总览
│   └── /[activity-slug]/              ← 活动详情
├── /outfitter/                        ← 地接总览
│   └── /[outfitter-slug]/             ← 地接详情
├── /guide/                            ← 横向专题
│   └── /[topic-slug]/                 ← 专题文章
├── /tag/                              ← 标签聚合
│   └── /[tag-slug]/                   ← 标签页
├── /u/                                ← 用户公开主页
│   └── /[user-slug]/                  ← 用户
├── /b/                                ← 徽章公开页
│   └── /[badge-slug]/                 ← 徽章详情
├── /about/                            ← 关于
└── /api/                              ← API（不被 indexed）
```

详见 [part_05 § 6](./part_05_information_architecture.md)。

---

## 2. SEO 优先级

### P0 · 18 雪场攻略（核心 SEO 资产）

| 关键词 | 月搜索量 | 优先级 |
|---|---|---|
| "Stubaier 中文攻略" | ~500 | ⭐⭐⭐⭐⭐ |
| "Sölden 滑雪" | ~800 | ⭐⭐⭐⭐⭐ |
| "Kitzbühel 攻略" | ~1,000 | ⭐⭐⭐⭐⭐ |
| "Zermatt 滑雪" | ~1,200 | ⭐⭐⭐⭐⭐ |
| "欧洲滑雪 中文" | ~2,500 | ⭐⭐⭐⭐⭐ |
| 18 个雪场各自 | 200-1,500 | ⭐⭐⭐⭐⭐ |

**总 PV 潜力**：18 × 平均 500 月搜索 × 5%（排第 1 CTR）= 450 PV/月

### P0 · 横向专题（5-8 篇）

| 主题 | 月搜索量 | 优先级 |
|---|---|---|
| "第一次去欧洲滑雪" | ~300 | ⭐⭐⭐⭐ |
| "欧洲滑雪 家庭" | ~200 | ⭐⭐⭐⭐ |
| "单板新手 欧洲" | ~150 | ⭐⭐⭐⭐ |
| "欧洲滑雪 价格" | ~400 | ⭐⭐⭐⭐ |
| "欧洲滑雪季节" | ~350 | ⭐⭐⭐⭐ |
| "欧洲滑雪 装备" | ~250 | ⭐⭐⭐ |
| "性价比 7 天" | ~100 | ⭐⭐⭐ |
| "2026 雪季总览" | 季节性 | ⭐⭐⭐ |

### P1 · 教练 profile

- URL：`/coach/[coach-slug]/`
- 教练名字 + "中文" + "教练" 等长尾
- 每个教练贡献 50-200 月 PV

### P1 · 徽章公开页

- URL：`/b/[badge-slug]/`
- "趣野徽章 X 是什么" 反向 SEO
- 分享传播时落地页

### P2 · 用户公开主页

- URL：`/u/[user-slug]/`
- 隐私默认私密，需用户 opt-in 公开
- 用户名搜索 / 雪友互查

---

## 3. Programmatic SEO（自动生成长尾页）

### 3.1 模板 A · 雪场 × 季节

```
/resort/austria/stubaier-gletscher/season-2026-12/
"Stubaier 2026 年 12 月雪况、价格、人流量"
```

- 18 雪场 × 6 季节段（10/11/12/01/02/03）= **108 页**
- LLM 生成 + 人工审核
- 每页含：雪况预测 + 历史平均 + 实时数据（Year 2）

### 3.2 模板 B · 雪场 × 难度

```
/resort/germany/spitzingsee/for-beginners/
"Spitzingsee 适合新手吗？详细分析"
```

- 18 × 4（新手/中级/高级/家庭）= **72 页**

### 3.3 模板 C · 雪场 × 装备 / 运动

```
/resort/switzerland/zermatt/for-snowboarders/
"Zermatt 适合单板吗？"
```

- 18 × 4（单板/双板/Ski Touring/Freeride）= **72 页**

### 3.4 模板 D · 雪场 × 行程组合

```
/guide/austria-7-days-stubaier-soelden/
"奥地利 7 天 Stubaier + Sölden 行程"
```

- 重要雪场组合 ~30 篇

### 3.5 Year 1 + Year 2 总目标

| 时间 | 静态页 | Programmatic |
|---|---|---|
| Year 1 | 30 篇（18 雪场 + 8 专题 + 4 引导） | 0 |
| Year 1.5 | 50 篇 | 108 季节 + 72 难度 + 30 行程 |
| Year 2 | 100 篇 | 全部 282+ 页 |
| Year 3 | 200 篇 | 500+ 页 |

→ **5 年累计 1000+ 页 = SEO 复利资产**。

---

## 4. 内容模板（每篇雪场攻略）

详见 BP V7 § 2.2.2。结构：

1. **基础信息卡片**（车程 / 海拔 / 雪道 / 缆车 / 雪季 / 单双板适合度）
2. ❗ **特别提醒**（避坑卡片）
3. **怎么去**（机场 / 火车 / 自驾 / 停车 / Vignette）
4. **新手一日动线**（5 步图文）
5. **进阶推荐**（红道 / 黑道 / 公园）
6. **实用贴士**（租板 / 储物 / 住宿 / 温泉）
7. **教练联动**
8. **用户评价**
9. **雪道图**

### 4.1 SEO meta 优化

```html
<title>Stubaier Gletscher 中文攻略 2026 · 冰川 + 公园 · 距慕尼黑 2h | 趣野 Funwild</title>
<meta name="description" content="Stubaier Gletscher 完整中文攻略：18 缆车、35km 雪道、夏季冰川、新手动线、停车避坑提醒、教练推荐。距慕尼黑 2h。" />
<link rel="canonical" href="https://funwild.com/resort/austria/stubaier-gletscher/" />
```

### 4.2 schema.org markup

每个雪场页加 SkiResort schema：
```json
{
  "@context": "https://schema.org",
  "@type": "SkiResort",
  "name": "Stubaier Gletscher",
  "address": {...},
  "telephone": "+43-...",
  "image": [...],
  "aggregateRating": {...}
}
```

→ Google rich results 增强 CTR。

---

## 5. Internal Linking 策略

### 5.1 雪场页内的内部链接

- 邻近雪场互链（Stubaier ↔ Sölden）
- 同难度雪场互链
- 雪场 → 教练（在该雪场教学）
- 雪场 → 活动（在该雪场举办）
- 雪场 → 横向专题（"第一次去欧洲滑雪"）

### 5.2 横向专题内的内部链接

- 专题 → 推荐的 5-8 个雪场（具体链接）
- 专题 → 推荐的教练 / 地接
- 专题 → 相关其他专题

### 5.3 SEO 价值

- 内部链接 = PageRank 传递
- 用户在 Website 平均访问页面 > 3 = 信号好

---

## 6. 小红书导流策略

### 6.1 笔记 + Website 关系

```
小红书笔记
├─ 标题 + 封面图
├─ 正文（详细内容）
├─ #趣野Funwild 标签
└─ 文末："详细攻略 + 教练 + 拼车 → funwild.com/r/stubaier"
       ↓ 短链
       Website 落地页（包含完整 SEO 内容 + 扫码进小程序）
```

### 6.2 不要直接放小程序二维码

- 小红书算法对"二维码 / 微信 / 跳转"信号敏感，会限流
- 用 Website 短链作中转，绕过限流

### 6.3 落地页设计

- 标题 = 小红书笔记标题
- "你在小红书看到的攻略 → 完整版"
- 中间是雪场详细内容
- 底部扫码进小程序

### 6.4 KOL 合作

- Year 1 与 10-20 个欧洲华人滑雪 KOL 合作
- 提供 Funwild 教练 / 地接 / 攻略素材
- KOL 写笔记带 #趣野Funwild + 短链
- 让 KOL 在小红书拿"小红书种草官"徽章（公开主页可显示）

---

## 7. 多语言扩展（Year 2+）

### 7.1 Year 2

- 英文版（Funwild 国际化 wedge）
- URL：`funwild.com/en/`
- 内容：精选 8-10 篇翻译

### 7.2 Year 3

- 德文版（本地客户）
- URL：`funwild.com/de/`
- 内容：5-8 篇核心

### 7.3 多语言架构

- 同一 CMS，按语言生成静态页
- `hreflang` 标签
- 用户偏好 cookie 自动跳转

---

## 8. 内容产能规划

### 8.1 Year 1 内容团队

- **欧根**：18 雪场攻略主笔
- **欧根 + 团队众包**：每人认领 2-3 雪场
- **LLM + 欧根 编辑**：Programmatic SEO 长尾页（V1.1）
- **磊子**：教练 profile 协助起草
- **贺安祺**：活动 / 地接项目协助
- **客服反馈**：转化为 FAQ 内容（V1.1）

### 8.2 Year 2 计划

- 招内容编辑 1 人 fulltime
- 持续雪场 update（每季）
- 新增冰川 / 夏季内容
- 多语言扩展

---

## 9. 内容生命周期

| 阶段 | 周期 | 动作 |
|---|---|---|
| 起草 | 写完后 24h 内 | LLM 优化 + 内部 review |
| 审核 | 1 周 | 团队成员 / 教练 review |
| 上线 | 雪季前 1-2 个月 | 同步发布 + 小红书推广 |
| 维护 | 每雪季 1 次 | update 价格 / 缆车 / 新政策 |
| 归档 | 5 年 | 历史季节内容保留 |

---

## 10. 内容防抄袭

- 每篇内容加 "© 趣野 Funwild" 水印
- 关键句子用具体细节（"我去年 12 月去 Sölden，停车场 8:50 已满"）—— AI 复制不出来
- 监控 Google 检索 ("inurl:funwild" + 主题词) 反向 search 检测复制
- 严重抄袭 → 通过 Google DMCA 投诉

---

## 11. SEO 健康度 metric

| 指标 | 目标 | 周期 |
|---|---|---|
| 总 indexed 页面数 | Year 1 末 50+ | 月 |
| 月自然搜索 PV | Year 1 末 5,000+ | 月 |
| 头部关键词 Top 3 排名占比 | 40%+ | 月 |
| 平均停留时间 | > 2 分钟 | 月 |
| 内部链接平均跳转 | > 1.5 次 | 月 |
| 移动友好度（PageSpeed） | > 85 | 季 |

---

## 12. 工程要求

- Website 必须 SSR（Next.js / Nuxt / Astro），不能纯 SPA
- 图片优化（WebP + lazy load + CDN）
- 移动端 Core Web Vitals 达标
- 结构化数据（schema.org）
- sitemap.xml 自动生成
- robots.txt 排除 admin / API

→ 详见 [part_13_engineering_aware.md](./part_13_engineering_aware.md)。

---

→ 下一篇：[part_12_design_system.md](./part_12_design_system.md) 详解视觉系统集成。
