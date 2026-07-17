# 赛道标准：借贷 v1-draft

## 1. 钱流本质
借款人付息 → 大部分归存款人 → 协议抽 reserve factor → 到 token 的是抽成的再分配。**三层漏斗天生比永续陡**，赛道 yield 上限低（最好的 Aave 也只 ~1-2%）——在本赛道见到高 yield 先怀疑口径。

## 2. 冠军基线
Aave：唯一「便宜(P/F~4x) + immutable-auto + 全员无需锁」，但 realized ~1% 且新引擎链上 tx 待坐实（announced≠realized 的活教材）。挑战者基线：Maple（真机构现金流+47% YoY 在涨——全表稀缺，但回购进基金）。反面锚：Morpho/Kamino（毛费巨大、到 token $0、开关卡法律税务）。

## 3. 赛道特有指标
- **息差真实性**：利率是市场化还是激励补贴出来的。
- **坏账史与回购联动**：出险后回购是否被关（Fluid $21M 坏账 → 回购暂停 = discretionary 的不可逆性当场证伪）。
- **reserve factor → token 的路径长度**：几跳、每跳谁裁量。
- **数据滞后**：新回购机制上线后 DeFiLlama 适配器普遍滞后（Aave 3.0 = $0），**必须链上直核**（Collector/executor 地址的真实 tx）。
- **回购目的地**：销毁/安全模块/国库三选时按最弱档评（destination 裁量 = 不算 immutable）。

## 4. 赛道特有闸门
- 「immutable」宣称但 destination 治理三选 → 不可逆性降档评。
- 机构信贷类：借款人集中度/违约史披露缺失 → 降档;有违约史但透明重组的不扣 trust（Maple 先例）。

## 5. 高发失败模式
#5 回购进金库、#10 纸面开关、#12 范式站位（Morpho 教科书）。

## 6. 口径注意
媒体最爱把「协议路由的收入总量」当回购额（Aave 头条 $402M vs 真 ~$30M = 1/13）——本赛道见数先除以十再核。
