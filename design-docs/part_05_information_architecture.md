# Part 5 · 信息架构 · Information Architecture

> 三套 IA：小程序 5 tab、Website 6 主导航、Mobile Web 折叠抽屉。同一份数据，不同导航。

---

## 1. Mini Program IA · 5 tab 底部导航

### 1.1 顶层结构

```
┌────────────────────────────────────────┐
│            状态栏 + 自定义 header        │
├────────────────────────────────────────┤
│                                        │
│                                        │
│            主内容区                     │
│                                        │
│                                        │
├────────────────────────────────────────┤
│  首页    出行    探索    消息    我的   │ ← 5 tab
└────────────────────────────────────────┘
```

| Tab | 图标 | 标签 | 角色 |
|---|---|---|---|
| 1 | `home` | 首页 | 动态流 + 我的进行中 + 本周末 |
| 2 | `pin` | 出行 | 拼车 + 我发布的 + 关注的人 |
| 3 | `compass` | 探索 | 雪场 / 教练 / 活动 / 地接（顶部切换） |
| 4 | `bell` | 消息 | 系统通知 + wave + 教练对话 + RSVP |
| 5 | `user` | 我的 | 徽章墙 + 资料 + 我的订单 + 设置 |

**关键决策回顾**：
- 与 BP V7 原 IA（7 板块）冲突：合并雪场/教练/活动/地接 → "探索"
- 与既有 mockup（`03-mobile.jsx` 的 `首页/雪场/活动/消息/我的`）冲突：拼车独立成 tab
- 这两条冲突已在 master.md § 5 锁定，子文档统一遵守

### 1.2 子结构 · 每个 tab 的二级 IA

#### Tab 1 · 首页
```
首页
├── Hero 区（动态）
│   ├─ 雪场内（5km 内）→ "📍 你在 X，要打卡？"
│   ├─ 行程内（已报名活动 / 占位中）→ "📅 距离 X 还有 N 天"
│   └─ 默认 → "本周末 5 人计划去 Spitzingsee"
├── 我的进行中（卡片列表）
│   ├─ 拼车中（已申请 / 已成行）
│   ├─ 报名中（占位 / 已付款）
│   ├─ 徽章离 N 步
│   └─ 待回复的 wave
├── 关注的人动态（V1.1）
│   └─ X 解锁徽章 / Y 打卡 / Z 发拼车
├── 一个垂直推荐位（按状态动态）
│   ├─ 新手 → 雪场入门动线
│   ├─ Hardcore → 本周雪况
│   └─ 国内游客 → 离线 PDF 攻略
└── 底部 5 tab
```

#### Tab 2 · 出行
```
出行
├── 顶部切换（segmented control）
│   ├─ [本周末]    ← 默认
│   ├─ [所有出行]
│   └─ [我发布的]
├── 列表（按雪场 / 日期分组）
│   ├─ 出行计划卡片（发起人 / 雪场 / 日期 / 已加入 X 人 / 还差 Y 人）
│   └─ 每张卡片右下角 [申请加入]
├── 右下浮动 FAB · [+ 发布出行计划]
└── 底部 5 tab
```

#### Tab 3 · 探索
```
探索
├── 顶部切换（pill tabs）
│   ├─ [雪场]  ← 默认
│   ├─ [教练]
│   ├─ [活动]
│   ├─ [地接]
│   └─ [市集]（V1.2）
├── 各 tab 独立内容（详见对应 page UX）
└── 底部 5 tab
```

#### Tab 4 · 消息
```
消息
├── 顶部分组 tab
│   ├─ [全部]
│   ├─ [系统]
│   ├─ [Wave & 申请]
│   └─ [对话]
├── 列表（时间倒序）
└── 底部 5 tab
```

#### Tab 5 · 我的
```
我的
├── 顶部 profile 卡（头像 / 昵称 / 主徽章 / 关注数 / 关注我数）
├── 徽章墙入口（彩色未解锁分布卡片）
├── 我的订单 / 我的活动 / 我的出行
├── 收藏 / 关注
├── 邀请码
├── 会员（占位 "即将推出"）
├── 代金券余额（占位）
├── 设置
│   ├─ 外观（Sunset / Pine / 跟随系统）
│   ├─ 通知偏好
│   ├─ 隐私
│   └─ 关于
└── 底部 5 tab
```

### 1.3 全局元素

- **顶部状态栏**：左 location pin + 当前城市；右 search icon + notification bell（未读红点）
- **底部 5 tab**：固定，浅色半透明 + backdrop-filter blur
- **全局搜索**：tab 之上、单页内的 search icon 任意页可触发
- **FAB（浮动）**：仅在"出行" + "市集"等可发布场景出现

---

## 2. Website IA · 6 主导航

### 2.1 顶层结构

```
┌───────────────────────────────────────────────────────────────┐
│  Logo  攻略  活动  教练  地接  社区  关于  │  搜索  登录/我的   │
├───────────────────────────────────────────────────────────────┤
│                                                               │
│                     主内容区                                   │
│                                                               │
├───────────────────────────────────────────────────────────────┤
│           Footer (友情链接 / 合作 / 法律 / 招商入驻)             │
└───────────────────────────────────────────────────────────────┘
```

| 导航项 | URL 路径 | 角色 |
|---|---|---|
| Logo | `/` | 回首页 |
| 攻略 | `/resort/` `/guide/` | 18 雪场 + 横向专题 |
| 活动 | `/activity/` | 列表 + 日历 |
| 教练 | `/coach/` | 列表 + 按雪场 |
| 地接 | `/outfitter/` | 列表 + "我要定制" |
| 社区 | `/community/` | 用户主页（V1.1）+ 徽章公开页 + UGC |
| 关于 | `/about/` | Funwild / N47 / B-kuh / 招商入驻 |

### 2.2 二级 IA

#### 攻略
```
/resort/                          雪场总览页
├── /resort/austria/                奥地利雪场列表
│   ├── /resort/austria/stubaier-gletscher/
│   ├── /resort/austria/kitzbuehel/
│   └── ...
├── /resort/germany/                德国雪场列表
├── /resort/switzerland/            瑞士雪场列表
├── /resort/italy/                  意大利雪场列表
└── /resort/[country]/[resort-slug]/season-N/  Programmatic SEO 长尾

/guide/                           横向专题入口
├── /guide/first-time-europe/        首次去欧洲滑雪指南
├── /guide/family-with-kids/         带娃滑雪攻略
├── /guide/snowboarder-beginner/     单板新手指南
├── /guide/budget-7-days/            性价比 7 天行程
└── /guide/season-2026/              2026 雪季总览
```

#### 教练
```
/coach/                           教练总览
├── /coach/[coach-slug]/             教练 profile
├── /coach/by-resort/stubaier/       按雪场筛选
├── /coach/by-language/chinese/      按语言筛选
└── /coach/by-discipline/snowboard/  按运动筛选
```

#### 活动
```
/activity/                        活动总览
├── /activity/[activity-slug]/       活动详情
├── /activity/calendar/              日历视图
├── /activity/by-type/camp/          按类型
└── /activity/by-resort/laax/        按雪场
```

#### 地接
```
/outfitter/                       地接总览
├── /outfitter/[outfitter-slug]/     地接详情
├── /outfitter/custom/               "我要定制" 表单
└── /outfitter/by-service/family/    按服务
```

#### 社区（V1.1）
```
/community/
├── /u/[user-slug]/                  用户公开主页
├── /b/[badge-slug]/                 徽章公开页
├── /ugc/                            用户攻略列表（V1.2）
└── /leaderboard/                    Year 1 不做
```

#### 关于
```
/about/
├── /about/                          Funwild 是什么
├── /about/n47/                      N47 介绍
├── /about/bkuh/                     B-kuh 介绍
├── /about/become-coach/             教练入驻
├── /about/become-outfitter/         地接入驻
├── /about/become-brand-partner/     品牌方合作
└── /about/legal/                    法律 / 隐私 / 条款
```

### 2.3 全局元素

- **顶部固定 navbar**：浅色 + backdrop-filter blur + 滚动时缩小
- **搜索框**：navbar 右侧，hover 展开
- **登录 / 我的**：navbar 最右
- **Footer**：4 列（产品 / 合作 / 法律 / 关注我们）+ 微信二维码 + 小红书 link
- **右下浮动**："在小程序打开"按钮 + 二维码 popup

---

## 3. Mobile Web IA · 折叠抽屉

### 3.1 顶层结构

```
┌──────────────────────────────┐
│  ☰  Funwild       搜索  我的  │ ← top bar
├──────────────────────────────┤
│                              │
│        主内容区               │
│                              │
├──────────────────────────────┤
│  在小程序打开 [扫码 popup]    │ ← 浮动按钮
└──────────────────────────────┘
```

- ☰ 点击 → 抽屉打开 → 6 主导航 + 登录 + 设置
- 顶部 logo + 搜索 + 我的 三件套
- 浮动"在小程序打开"按钮固定右下，是 mobile web 的主 conversion CTA

### 3.2 关键决策

- **不做 PWA**：不诱导 install。Mobile web 的角色是 SEO + 分享落地页，不替代 app。
- **不做"下载 app"引导**：用户已经在浏览器里，引导他们扫码进微信小程序更直接。
- **不做 mobile-only 内容**：mobile web 是 desktop web 的 responsive，内容与 desktop 一致。

---

## 4. 同一搜索框的双端不同行为

```
用户输入："Stubaier"
```

**小程序搜索结果排序**：
1. 雪场：Stubaier Gletscher
2. 我的：我在 Stubaier 打卡 12 次
3. 拼车：本周有 5 个 Stubaier 出行计划
4. 教练：3 个在 Stubaier 教学的教练
5. 活动：2 个 Stubaier 活动
6. 用户：3 个昵称含 Stubaier 的用户

**Website 搜索结果排序**：
1. 雪场攻略：Stubaier Gletscher 中文攻略（高 SEO 权重）
2. 横向专题：包含 Stubaier 的"首次去欧洲滑雪指南"
3. 教练：3 个在 Stubaier 教学的教练
4. 活动：2 个 Stubaier 活动
5. 用户公开主页（V1.1）

→ 同一关键词 → 不同排序 → 反映两端用户心理。

---

## 5. 导航深度规则

- **小程序**：任何页面 ≤ 3 步到 home（back / tab / 全局 search）
- **Website**：任何页面 ≤ 4 步到 home（back / nav / footer / search）
- **breadcrumb**：Website 必须有；小程序不需要（用 back 替代）

---

## 6. URL Slug 规则

| 类型 | 规则 | 例 |
|---|---|---|
| 雪场 slug | 全小写 + 连字符 + 不含 umlaut（ü→ue） | `stubaier-gletscher`, `sankt-anton` |
| 国家 slug | 英文全名小写 | `austria`, `germany` |
| 教练 slug | 拼音连字符（中文） / 英文名小写 | `zhang-lei`, `michael-meyer` |
| 活动 slug | 英文 + 年份 | `camp-good-times-2026` |
| 地接 slug | 简称 + 英文 | `n47-official`, `alps-china-tour` |
| 徽章 slug | 英文翻译 | `first-checkin`, `glacier-master` |
| 用户 slug | 微信昵称拼音 + 数字 后缀 | `xiaomei-zhang-7` |

---

## 7. 404 / 500 / 离线 fallback

| 错误 | 小程序 | Website |
|---|---|---|
| 404 | "页面不存在" + 返回首页 | 友好 404 页 + 推荐相关攻略 |
| 500 | "服务出错，请重试" + 重试按钮 | 友好 500 页 + 邮件客服 |
| 离线 | "请连接网络" + 已缓存的雪场列表 | 浏览器原生 |

---

→ 下一篇：[part_06_page_ux/](./part_06_page_ux/) 进入 17 个页面的 wireframe 级文字稿。
