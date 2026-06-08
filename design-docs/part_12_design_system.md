# Part 12 · Design System Integration · 视觉系统集成

> 不重新定义视觉。引用 `brand_design/` 作为 SoT · 只解决 theme 分配 + interaction 衔接 + 缺口补足

---

## 0. 关键声明

> **本文档不重复 `brand_design/` 已定义的内容。**

如果你需要查：
- 色彩 hex 值 → `brand_design/directions/shared-tokens.jsx`
- 字体家族 / type scale → `brand_design/directions/01c-type-system.jsx`
- spacing / radius / shadow / motion → `brand_design/directions/01d-foundations.jsx`
- Logo system → `brand_design/directions/01a-logo-system.jsx`
- 组件示例 → `brand_design/directions/02-components.jsx`
- Mobile mockup → `brand_design/directions/03-mobile.jsx`
- 编辑 / 海报设计 → `brand_design/directions/04-editorial.jsx` / `05-social.jsx`
- Web 长页 → `brand_design/directions/06-web-longpage.jsx`
- 徽章插画 → `brand_design/assets/badges-real.html` + `badges-data.json`

**本文档只解决**：
1. ★ Theme Allocation 策略（3 theme pack 如何分配）
2. Interaction 设计与 token 的衔接规则
3. 既有 system 没覆盖的 5 个缺口

---

## 1. 既有 system 核心引用表

| 维度 | 决策（来自 `brand_design/`） |
|---|---|
| **3 个 theme pack** | Sunset · Pine · Indigo |
| **字体家族** | Geist · Source Han Sans CN · Geist Mono |
| **Type scale** | 11 阶（display-2xl 64 → micro 10），ratio ≈ 1.2 |
| **Spacing** | 4px 节奏，12 阶 |
| **Radius** | 7 阶，平台感优先小圆角（4-6px） |
| **Shadow** | 5 阶 warm-tinted |
| **Motion** | 4 duration × 4 easing |
| **Grid** | 12 列 · 16 gutter · 1280 max · 4 断点 |
| **Icon** | 24px / 1.5px stroke / Lucide outline |
| **雪道难度色** | 国际标准绿/蓝/黑/红，不参与 theme |
| **Categorical** | 7 色（亲子/社交/进阶/入门/赛事/深度/已满） |
| **数字** | 全部 Geist Mono + tabular-nums |

---

## 2. ★ Theme Allocation Strategy（已在 master 锁定）

### 2.1 决策表

| 表面 | Theme | 锁定 |
|---|---|---|
| 小程序主体 UI | **Sunset** 默认 + 用户切 Pine | ✓ |
| 小程序 dark mode | Sunset.dark / Pine.dark | ✓ |
| Website 公开内容 | **Pine** | ✓ |
| Website 商业页面 | **Indigo** | ✓ |
| 海报 / UGC | **Sunset** + 真实雪山照片 | ✓ |
| 徽章插画 | 独立色票，跨 theme | ✓ |
| Pitch deck | Sunset 主 / Indigo 辅 | ✓ |

### 2.2 论证

**为什么不"一套到底"？**
- 3 个 theme 反映三种不同人群的心智：
  - **Sunset 暖陶土**：阿尔卑斯壁炉 + 雪场夕阳 → 本地华人雪友 + UGC 物料
  - **Pine 松绿**：户外正统 + 不像电商 → 国内游客查攻略
  - **Indigo 靛蓝**：Linear/Vercel 平台感 → 教练 / 地接 / 品牌方 B2B
- 同一品牌下不同表面用不同 theme = "对不同人群说不同语言"
- Brand 一致性靠 Logo + 字体 + 数字呈现 + 徽章保持

### 2.3 切换规则

#### 小程序 Sunset / Pine 切换
- 用户在 "我的 → 设置 → 外观" 切换
- 默认 Sunset
- 切换后立即生效（< 200ms 过渡动画）

#### 小程序 dark mode
- 跟随系统（iOS / Android dark mode）
- 用户可在"我的 → 设置 → 外观" 强制 light / dark

#### Website 内部
- 公开内容（攻略 / 活动 / 教练 / 地接 / 用户主页）= Pine
- 商业页面（招商入驻 / 后台 / 品牌方合作）= Indigo
- 在 URL 路径自动切换 theme（`/about/become-coach/` → Indigo）

---

## 3. Interaction 与 Token 的衔接规则

子文档每页都应遵守。汇总：

### 3.1 数字与 Mono 字体

| 场景 | 必用 Geist Mono |
|---|---|
| 价格 | ✓ |
| 距离 / 车程 | ✓ |
| 海拔 / 温度 / 雪深 | ✓ |
| 打卡次数 / 徽章计数 | ✓ |
| 时间戳 | ✓ |
| 评分（4.9） | ✓ |
| 容量进度（28/40） | ✓ |
| 信用分 | ✓ |
| Eyebrow label（SNOW REPORT · 今日） | ✓ |

→ 配合 `font-variant-numeric: tabular-nums` 让等宽数字对齐。

### 3.2 圆角规则

| 元素 | radius |
|---|---|
| Card 默认 | `radius-md (6)` |
| 大 Card / Hero | `radius-lg (8)` 或 `radius-xl (12)` |
| Button | `radius-sm (4)` |
| Input | `radius-sm (4)` |
| Tag / Chip / Pill | `radius-full` |
| 徽章 / 头像 | `radius-full` |
| 表格 / 数据 grid | `radius-none` |

**绝对避免**：CTA 按钮用 `radius-xl (12)` ← 与平台感冲突

### 3.3 Padding 规则

| 元素 | padding |
|---|---|
| Card 内部 | `space-6 (24)` 大卡 / `space-4 (16)` 小卡 |
| Section 间距 | `space-12 (48)` 或 `space-16 (64)` |
| Button | `space-2 space-4` |
| Tag | `space-1 space-2` |
| List row | `space-3 space-4` |

### 3.4 Motion 规则

| 场景 | duration × easing |
|---|---|
| 默认 transition | `base (180ms) · standard` |
| Tap / hover 反馈 | `fast (120ms) · standard` |
| Panel / drawer | `slow (320ms) · decel` |
| Modal | `slower (480ms) · decel` |
| 徽章解锁 | `slower (480ms) · spring` |
| Tab 切换 | `base (180ms) · standard` |

### 3.5 背景 hierarchy

只允许 3 层背景：
1. `page` - 整页底色
2. `raised` - 卡片
3. `sunken` - 输入框 / 内嵌

不要造第 4 层（`raised-on-raised` 之类）。

### 3.6 图片占位 / Hero fallback

缺图时使用 `linear-gradient(135deg, accent[400], accent[700])`，已在 brand_design 03-mobile.jsx 中使用。

---

## 4. 既有 system 没覆盖、需要补足的 5 个缺口

### 缺口 1 · Dark mode 切换时机

`shared-tokens.jsx` 已定义每个 theme 的 dark 子系统。本规格补**切换时机**：

| 场景 | 行为 |
|---|---|
| 用户首次进入 | 跟随系统 |
| 用户在"我的"切换 | 立即生效 + 记忆 |
| 雪场 5km 内 | hint "你在雪场，要切 dark 让屏幕不眩光吗？" |
| 晚上 8 PM-7 AM（cron） | 不自动切，但若用户用 light → 顶部 toast "已为你切到 dark" 选项 |

### 缺口 2 · Accessibility

- **文字最小 12px**（caption 12 / micro 10 仅用于 eyebrow label）
- **对比度** WCAG AA（normal text 4.5:1，large text 3:1）
- **雪道难度色** 不只用颜色，配二次符号区分（▼ / ■ / ◆ / ◆◆）—— 色盲友好
- **键盘导航**（Website）：所有 CTA `tab` 可达
- **Screen reader**：图片 alt / aria-label 完整

### 缺口 3 · 小程序 vs Website 视觉差

| 维度 | 小程序 | Website |
|---|---|---|
| Base font size | 14px | 16px |
| Card padding | space-4 (16) | space-6 (24) |
| Grid | 自由布局 | 12 列 16 gutter |
| Section margin | space-8 (32) | space-16 (64) |
| 其他 token | 一致 | 一致 |

### 缺口 4 · 徽章 3 态视觉

既有 142 SVG 全是彩色。需要派生：

```css
/* 彩色（默认） */
.badge { filter: none; opacity: 1; }

/* 灰态（未解锁） */
.badge--locked { filter: grayscale(1); opacity: 0.4; }

/* 进度态（即将解锁） */
.badge--progress {
  filter: grayscale(1); opacity: 0.6;
  /* + SVG ring around with stroke-dasharray */
}
```

设计师不需要重做 SVG，CSS 即可派生。

### 缺口 5 · 头像降级 3 段

```
真实头像（微信 / 用户上传）
  ↓ 缺失
渐变 fallback `linear-gradient(135deg, accent[400], accent[700])` + 首字母
  ↓ 缺失
默认 AI 头像 SVG（设计师补 6-10 个 default）
```

---

## 5. 海报体系视觉规范

参考 `05-social.jsx`（既有海报模板）。本规格补：

### 5.1 海报尺寸

- 微信朋友圈 / 群分享：1080 × 1920（9:16）
- 小红书内嵌：1080 × 1440（3:4）

### 5.2 海报视觉层级

```
1. 背景：真实雪场照片 + 暗化 overlay 30%
2. 中层：用户头像 + 主体内容（徽章 / 数据 / 文字）
3. 底层：Logo + 二维码 + 极简文案
```

### 5.3 海报字体

- 中文：Source Han Sans CN
- 数字：Geist Mono · tabular-nums
- 标题大字：Geist Display weight 600

### 5.4 海报色彩

- Sunset accent 主色 + 真实雪山照
- 不用 Pine / Indigo（出图调性不对）

---

## 6. Logo 使用规范

引用 `01a-logo-system.jsx`。本规格补：

- 小程序：最小 24px 高
- Website navbar：32px 高
- 海报底部：60-80px 宽
- Favicon：32 × 32 px square
- 微信小程序应用图标：512 × 512 px

不变形、不彩边、不放阴影、不与其他元素重叠。

---

## 7. Empty / Loading / Error 视觉模式

### 7.1 Loading

- 骨架屏（不用 spinner）
- 颜色 `neutral[200]`，pulse 动画 1.5s loop
- Hero / Card / 列表均有骨架

### 7.2 Empty

- 文字 + 简洁插画（不要"大空状态图"）
- 必配 1 个可执行 CTA
- 例："本周末暂无拼车，[发起一个 →]"

### 7.3 Error

- 顶部 toast / banner（非阻塞）
- 文字简洁："网络不好" / "页面加载失败"
- 提供"重试"按钮
- 不要红色满屏（破坏品牌）

---

## 8. 微互动 micro-interaction 清单

| 动作 | 反馈 |
|---|---|
| 按钮按下 | scale 0.96 + 120ms ease |
| 卡片 hover | y -2px + shadow-md |
| 切换 tab | 内容 fade 180ms |
| 解锁徽章 | spring 480ms + 粒子 + haptic |
| 拼车申请发送 | spring 弹层确认 |
| 红点未读 | 呼吸 1.2s spring |
| 滑入卡片 | stagger 50ms + 80ms decel |

---

## 9. 国际化（i18n）准备

Year 1 中文 only。Year 2 加英文 / 德文。设计准备：

- 所有字符串走 i18n 函数（`t('key')`）
- 文案不写死在组件
- 长度容差：英文 + 30%，德文 + 50%（与中文比较）
- RTL 不需要（Year 1-3 不做阿拉伯文 / 希伯来文）

---

## 10. 与 brand_design/ 的"接口"

任何子文档引用 token 时必须用 token 名（如 `--text-h2`），不写 magic number（如 `22px`）。

工程实现时：
- 小程序：rpx 单位（375 设计稿）
- Website：rem / px 单位
- token 通过 CSS variable / less / sass 输出

---

## 11. 设计交付清单（设计师 / 洪玮瑢）

Year 1 必须交付的视觉资产：

| # | 资产 | 截止 |
|---|---|---|
| 1 | Logo 优化（如需） | 6 月 |
| 2 | 徽章插画 50 个（V1.0 上线） | 9 月 |
| 3 | 海报模板 4 类（雪场 / 徽章 / 拼车 / 评价） | 9 月 |
| 4 | 默认头像 6 个 | 8 月 |
| 5 | Empty 状态插画 5-8 个 | 9 月 |
| 6 | 错误页插画 2 个 | 9 月 |
| 7 | 小红书封面图模板 5 套 | 10 月 |
| 8 | onboarding 引导插画 3 个 | 9 月 |

→ 设计师产能是 Year 1 关键缺口（见 [part_14_mvp_strategy.md](./part_14_mvp_strategy.md)）。

---

## 12. 反例 · 严格避免

- ❌ 把 3 个 theme pack 当"主题切换"展示给用户
- ❌ 在同一页混用 2 个 theme
- ❌ 海报叠 12px 大圆角
- ❌ 把数字写成 Source Han Sans CN
- ❌ Card 用 `radius-xl (12)` 让"年轻感"
- ❌ 用 spinner 而不是骨架屏 loading
- ❌ Empty 状态没有 CTA
- ❌ 不用 token，硬编码颜色 / 间距
- ❌ Hero 用渐变色块当背景（不用真实雪山照）

---

→ 下一篇：[part_13_engineering_aware.md](./part_13_engineering_aware.md) 工程难度地图与边界。
