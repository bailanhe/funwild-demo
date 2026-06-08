# 给杜蕊珈 ADR-000 的法律同步（提案稿 · 待评审后由她合并）

> ⚠️ 这是**提案**,**未推送**到 `DRX-1877/funwild`(尊重她"勿擅自 push"的规矩)。
> 用途:回答她 ADR-000《Deployment region and data residency》里的开放问题,并补充几条影响 runtime/数据模型的法律结论。
> 依据:我们的 `legal/risk-matrix.md`、`legal/agreements-outline.md` + 法律讨论结论。**非法律意见,须律师确认。**

---

## 1. 回答她 ADR-000 的「Open questions (before production)」

她原文列了三个待解项,我们能答前两个的法律部分:

| 她的开放问题 | 我们的结论 |
|---|---|
| **Legal entity hosting the DPA with EU users** | **德国 GmbH** 作为欧洲经营/签约主体 → 它是与 EU 用户签 DPA、承载 GDPR 责任的实体。另设**中国实体**专管微信小程序备案/ICP + 国内运营。两实体职责隔离。 |
| WeChat callbacks 是否需 CN relay | (技术问题,法律不决定;但**数据跨境**受限,见下) |
| Backup region / RPO·RTO | (纯工程,法律不决定) |

她 ADR-000 的「Review gate: 待 legal 确认实体结构」→ **现在可以填:中国实体 + 德国 GmbH。**

## 2. 给 ADR-000 加一节:数据跨境合法性(PIPL + GDPR 双合规)

混合部署(EU Postgres + 微信侧)意味着 **China↔EU 个人数据流转**,必须有合法基础:
- EU 侧:GDPR —— 跨境传输需 **SCC(标准合同条款)/ 用户单独同意 / 充分性认定**之一。
- 中国侧:PIPL —— 中国用户个人信息出境需 **单独同意 + 出境合规机制**。
- 落到 runtime:
  - [ ] 用户注册/onboarding 时取得**跨境传输的单独同意**(产品要加这个勾选)。
  - [ ] `apps/api` 实现 **GDPR 导出/删除**(她 ADR-000 已列,保留)。
  - [ ] 日志脱敏(手机/邮箱)——她已列,保留。

## 3. 给 runtime 的两条硬约束(法律驱动,影响 Sprint 0 设计)

**3.1 Year-1 不碰交易资金 → 不要建支付/托管基础设施**
- 法律结论:平台完全不碰用户↔provider 的交易资金(避开 PSD2 支付牌照、反洗钱、托管担保责任)。
- 对 runtime 的含义:**V1.0 不需要支付网关、不需要 escrow/担保交易、不需要 KYC 资金流**。`apps/api` 只记录撮合痕迹(`coach_contact_intents`、`signups`、check-ins),**不处理钱**。省一大块工程 + 牌照负担。
- ⚠️ 哪天要做抽佣/站内支付 = 重大法律决策点,需新 ADR + 律师。

**3.2 两个"法律资产"必须落进数据模型**
法律抗辩依赖这两类留证,domain-model 要持久化:
- [ ] `safety_confirmations` —— 安全确认清单的**勾选项 + 时间戳 + user_id + 场景**(野雪/高海拔)。这是知情同意(informed consent)的抗辩证据,不能只存在前端。
- [ ] `providers` 保险/资质字段 —— `identity_verified`、`credential_verified`、`insurance_source`(school/self)、`insurance_scope[]`(人身伤害/接课国家/野雪)、`insurance_valid_until`。**保单失效要能触发下架**。

## 4. 与她架构的契合点(顺带确认)

- 她 ADR-000 已坚持"EU 为主 DB + GDPR 导出删除" → ✅ 与我们的 GmbH/欧盟定位一致。
- 她 ADR-001"不碰钱"未明说,但她 modules.md 把 Marketplace/支付都放 V1.1+ → ✅ 与 3.1 一致,正好写实。
- 她的 `coach_contact_intents`(微信联系留痕)→ ✅ 正好是"中介撮合、不介入"的留痕设计,法律上友好。

---

## 建议合并方式

把第 1–3 节作为 **ADR-000 的补充 / 一条新 ADR-005「法律实体与数据合规」** 提给杜蕊珈,由她决定挂哪。第 3 节的两个数据模型项应同时进 `domain-model.md` 的 TBD 清单。
