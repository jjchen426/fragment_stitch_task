# Seed Task：基于短片段生成与组装的多肽结合剂生成方法开发

本目录为大语言模型 / AI Scientist 科研能力测评任务的标准任务包。

## 目录隔离原则（发布前必读）

- **`workspace/`（唯一挂载为容器内 `/workspace` 下发给被测模型）**：
  - `workspace/TASK.md`：纯净版任务题面（仅保留科学问题、范围与配额边界、阶段一评估口径与原始证据交付接口；已移除旧版草稿、Rubric、Cao 2022 文献、参考表位清单及全部阶段二评分阈值与终点公式）。
  - `workspace/input/README.md`：输入与输出路径说明。
  - `workspace/input/budget_and_quotas.yaml`：统一配额与协议配置（阶段一默认每表位生成 **100 个短片段**及 `< 1.5 / 2.0 Å`、`5.0 Å` 阶段一口径；阶段二仅含靶点列表、默认每靶点每方法 **200 个候选**、**3 seed × 5 sample**、`tmol` `beta_nov_2016` $\ge 40$ 次 / `beta_nov_2016_cart` $\ge 200$ 次，不含任何阶段二通过阈值）。
  - `workspace/input/environment_manifest.yaml`：去泄题版可用软件环境与权重路径模板（不含“用途/操作指南”列）。
  - `workspace/input/targets/`：三个阶段二测试靶点的纯净单受体结构（`IL7Ra.pdb`、`TrkA.pdb`、`PD_L1.pdb`）与 `targets_manifest.json`（仅保留目标受体单链与原始作者残基编号，已清除天然配体链、溶剂及来源 PDB ID）。
  - `workspace/submission/`：预创建的目标提交目录骨架（`code/`、`results/stage1/`、`results/stage2/`、`results/candidates/relaxed/`、`results/candidates/predicted/`）。
- **`organizer/`（仅限命题与评测方内部使用，严禁挂载或下发给被测模型）**：
  - `organizer/rubric.md`：完整评分细则（六维评分矩阵、**阶段二官方离线统一重算阈值与终点判据**、三靶点参考表位核验口径、红线扣分项及 3 项私有自动化校验单测）。
  - `organizer/reference_epitopes.json`：机器可读的阶段二官方评分阈值与三靶点参考功能表位（均经单受体 Shrake-Rupley SASA > 0 核验，与 `workspace/input/targets/*.pdb` 的链号与残基编号严格对齐）。
  - `organizer/prompt_source_note.md`：题面来源、内嵌表格映射与环境部署前检查清单。

## 上机部署前 4 项检查

1. 在 `workspace/input/budget_and_quotas.yaml` 的 `hardware_budget_template` 中填写真实 GPU 型号/卡数、时长上限、网络策略；如因时长/磁盘限制需缩减阶段二配额，统一修改该文件并适用于所有参评模型。
2. 在 `workspace/input/environment_manifest.yaml` 中将 `<FILL_PATH>` 替换为容器内实际绝对路径（内部环境部署脚本由运维单独保管，勿放入 `/workspace/`）。
3. 在开始阅卷前，于 `organizer/rubric.md` 中填定六维分值权重、红线扣分细则，并补充/核对肽键几何参考阈值表。
4. 仅将 `workspace/` 挂载至评测容器的 `/workspace`。
