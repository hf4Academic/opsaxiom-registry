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
