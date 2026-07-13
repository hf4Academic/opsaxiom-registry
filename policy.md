# 收录政策（Policy）

进入本 registry 的每个 Skill 必须同时满足：

1. **校验全绿**：`python tools/validate.py <skill>` 通过（结构 + 语义 S1–S13 +
   命令语法树）。CI 在每个 PR 上强制执行，不绿不合。
2. **成熟度 ≥ 🔵 sim_verified**：⚪draft 一律拒收。仿真证据（tests/ 场景）随包提交。
3. **签名有效**：attestations/ 内实地验证记录须 Ed25519 验签通过；
   签名者进入 `keyring/trusted.pub` 需维护者双人复核（PR 形式）。
4. **可回滚**：action 节点的 rollback 为必填且经过仿真（黄金准则 R1）——
   这由校验器强制，列在这里是提醒评审人抽查语义。

维护者合入 = 对以上四条背书。发现问题走 git revert，留痕不删档。

## 治理与投诉（thumbs-down 流程）

任何人可对任何已收录 Skill 提出投诉：网站详情页的 **👎 投诉此 Skill** 按钮，
或直接开一个带 `report` 标签的 Issue（有模板）。流程：

1. **核实**：维护者按 Issue 复现；必要时在仿真环境重跑该 Skill 的 tests。
2. **处置**（按严重度三选一，全部是 git 提交、可追溯）：
   - 修正：提 PR 修复后保留；
   - 降级：撤销徽章（如 🟢field_verified → 🔵sim_verified）；
   - 下架：`git revert` 移出 registry——留痕不删档。
3. **公示**：处置结论回帖在原 Issue；负面 attestation 照常入库（宝贵信号）。
