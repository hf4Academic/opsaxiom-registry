# OpsAxiom Skills Registry

> 运维专家判断的社区资产库：每个 Skill 都是**可验证、可回滚、可认证**的排查/变更决策树。
> 本仓库是社区的唯一事实来源；网站是它的只读投影。

## 用（任何装了 [OpsAxiom](https://github.com/hf4Academic) 的终端）

```bash
opsaxiom hub init https://github.com/hf4Academic/opsaxiom-registry.git
opsaxiom hub sync                 # 拉索引 + 可信签名者
opsaxiom hub search 磁盘           # 离线搜索
opsaxiom hub pull <skill-id>      # 三道安全门：本地重跑校验 / 验签 / draft 拒收
```

## 发布你的 Skill（两条通道）

**终端（推荐）**：排查完 → `opsaxiom skill from-session` 生成草稿 → 补完过 lint →
`opsaxiom hub push <id>`（pi 界面里 `/publish` 上下键选）→ 得到 bundle
→ fork 本仓库，解包进 `skills/<id>/<version>/` → 提 PR。

**网页**：fork 本仓库 → GitHub 网页上传 skill 目录 → 提 PR。

PR 就是发布表单 + 评审 + CI 质检 + 留痕。收录标准见 [policy.md](policy.md)：
校验全绿 + ≥🔵 sim_verified + 签名有效。

## 徽章含义

⚪ draft（模型/人生成，未验证）→ 🔵 sim_verified（仿真验证）→
🟢 field_verified（≥3 份独立签名的实地验证）→ 🟡 certified（领域评审人签署）

## 目录结构

```
index.json                  # 全部 Skill 索引（CI 自动重建，勿手改）
skills/<id>/<version>/      # skill.yaml + tests/ + attestations/
keyring/trusted.pub         # 可信签名者公钥（进入需维护者双人复核）
policy.md                   # 收录政策
```
