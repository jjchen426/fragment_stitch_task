# `/workspace/input/` 输入说明

本目录提供任务所需的阶段二单受体结构、统一配额配置及环境清单。完整任务要求请阅读 `/workspace/TASK.md`。

## 目录内容

- `targets/`：阶段二三个测试靶点的单受体参考结构（仅保留目标受体单链，已移除天然结合伴侣与水分子，保留原始 PDB 作者残基编号）：
  - `targets/IL7Ra.pdb`：人 IL-7Rα 胞外域（链 `B`，残基 17–209）；功能目标：阻断 IL-7Rα / IL-7 互作。
  - `targets/TrkA.pdb`：人 TrkA Ig-like d5 结构域（链 `X`，残基 282–382）；功能目标：阻断 TrkA / β-NGF 互作。
  - `targets/PD_L1.pdb`：人 PD-L1 IgV 结构域（链 `A`，残基 18–132）；功能目标：阻断 PD-L1 / PD-1 互作。
  - `targets/targets_manifest.json`：上述三靶点的结构元数据与功能目标描述。
- `budget_and_quotas.yaml`：阶段一默认片段预算（每表位默认生成 100 个短片段）、阶段二提名配额（默认每靶点每方法 200 个）、结构预测采样配额（3 seed × 5 sample）、`tmol` 两阶段弛豫力场与独立结构数下限（`nstruct`）及硬件预算说明。
- `environment_manifest.yaml`：当前计算节点已安装的 Conda 环境、软件版本与权重路径清单（注：本地未预置 627 GB 全量 `AlphaFold3` mmCIF 数据库）。

## 输出位置

所有代码、报告与可复现结果产物统一保存至 `/workspace/submission/`（目录骨架已预创建）。
