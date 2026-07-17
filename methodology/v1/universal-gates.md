# 通用闸门 v1（对所有项目生效）

> 核心：**评级不是 yield 排序。先闸门一票否决，幸存者再打分。**
> 实现：`lib/grade.mjs`（规格测试 `test/grade.test.mjs`）。

## 0. 口径规范（先于一切判断）

- **三层拆穿**：毛手续费（多归 LP）≠ 协议收入 ≠ 真到 token。全行业只有 ~6.3% 毛费到 token（2026-07 基线）——媒体口径默认放大一个数量级，见数放大先做除法。
- **Realized-only**：只认已上链兑现。announced / 提案 / 路线图 / "全面铺开后 $X" = 叙事。
- **多窗口**：7d/30d/90d/1y 同算;发散 >2x = 脉冲，亮「勿年化」旗，yield 取窗口中位（v1 引擎暂用 30d + 趋势旗，P1 升级）。
- **双分母**：mcap 与 FDV 双口径;低流通高 FDV 时 mcap 口径 yield 是系统性谎言。
- **双受益人**：被动持有人 vs 锁仓/质押者分开报（AERO 12% 是锁仓者的，被动 ≈2-4%）。

## 1. Payout 去向分类（"holders revenue" 这个词混装了它们）

| 代号 | 去向 | 到手性 |
|---|---|---|
| `burn-all` / `dividend-all` | 销毁 / 现金分红给全体 | ✅ 真到手，无需锁 |
| `staker` | 给质押者 | 要质押；被动 ≈0 |
| `ve-locker` | 给锁仓投票者 | 要锁 1-4 年+主动投票；被动 ≈0 |
| `treasury` / `trust-hold` | 回购进金库/信托 | ❌ 不到手（可再部署/可逆） |
| `none` | 不分 | ❌ 零捕获 |

## 2. 不可逆性分级

`immutable-auto`（合约强制自动，Firepit/Aavenomics3.0 式）> `governance-set-auto`（自动但比例可改，HYPE）> `governance-gated-inlet`（引擎不可逆但进料口逐票开，UNI 式单点故障）> `discretionary`（随时可停，Fluid 被关停已证）> `none`。

## 3. 硬闸门（按序，一票否决）

| # | 闸门 | 命中 → | 实例 |
|---|---|---|---|
| G1 | 无 token / payout=none / 捕获被书面否认 | **F** | Polymarket、Morpho、LDO(假9.7%)、SLX |
| G2 | trust-gate fail（判据=**要不要防坑**，非数字真假；口径失真同向、承诺删除史、审计声明查无实据） | **F** | ASTER、USUAL、BELIEVE |
| G3 | verdict=trap（已证伪） | **F** | HUMA($90实烧) |
| G4 | narrative（纸面未兑现）或链上零兑现 | **封顶 D** | ENA(sENA 22月+1.86%) |
| G5 | 回购进金库/信托 | **封顶 C** | Maple、Jupiter、deBridge、Spark |
| G6 | 须锁/质押（被动≈0） | **封顶 B** | AERO、Pendle、GMX |
| G7 | 补贴幻觉（回购 > 1.2× 协议收入） | **封顶 C + 旗** | edgeX(2.8x) |
| G8 | 价值陷阱 / 净稀释抵消 / 微市值 | **封顶 C + 旗** | GMX、PUMP、OVER |

地板：`verdict=confirmed`（链上大规模在跑）→ 至少 B；过全部闸门但弱捕获 → D（F 只留给结构性零/骗/背信）。

## 4. 幸存者打分（0-100 → A/B/C/D）

`35×realized yield(稳健口径) + 25×不可逆权重 + 15×run-rate 趋势(在涨=稀缺信号) + 15×估值(P/holders-rev) + 10×被动可得`

## 5. 回购断言五点证伪（见数先跑一遍）

①在不在自家产品 ②合约 enforce 还是口头 ③链上有无真回购 tx（dev 自买≠营收回购）④**费用在哪个法人/哪条链产生沉淀**（链下 BVI = 没有费用池可开关，SLX 教训——这问比"有没有开关"更先）⑤当前营收量级数学成立否。

## 6. 证据规范

每个判断字段附来源；引用的文档**当时存快照**（项目方会删——SLX「删正文留尸体」）；链上断言必须给地址/tx；拿不出收据 = 没发生。
