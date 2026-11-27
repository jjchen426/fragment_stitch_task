# 命题与数据溯源说明（Organizer Only）

- **文档版本**：Benchmark Task & Rubric v1.0（2026-11-27）
- **环境配置**：评测镜像部署脚本由运维/命题方单独维护，禁止放入 `/workspace/`，仅通过脱敏后的 `workspace/input/environment_manifest.yaml` 向被测模型暴露软件版本与路径。
- **肽键几何参考表**：建议由命题方按标准肽键几何（C–N 键长、trans/cis $\mathrm{C_\alpha\text{–}C_\alpha}$ 间距、键角 $\alpha/\beta$、$\omega/\tau_C$ 二面角及非键防碰撞距离）在 `organizer/` 下维护机读配置（例如 `organizer/geometry_thresholds.csv`）。

## 单受体结构制备溯源

| 靶点文件 | 原始晶体 PDB | 提取链 | 残基区间（作者编号） | 清洗操作 |
| :--- | :---: | :---: | :---: | :--- |
| `workspace/input/targets/IL7Ra.pdb` | `3DI3` | `B` | `17–209`（193 aa） | 移除 IL-7 链 A、水/杂原子、氢原子与源 PDB 头信息；仅保留主构象重原子 |
| `workspace/input/targets/TrkA.pdb` | `1WWW` | `X` | `282–382`（101 aa） | 移除 β-NGF 链 V/W、链 Y、水/杂原子、氢原子与源 PDB 头信息；仅保留主构象重原子 |
| `workspace/input/targets/PD_L1.pdb` | `4ZQK` | `A` | `18–132`（115 aa） | 移除 PD-1 链 B、水/杂原子、氢原子与源 PDB 头信息；仅保留主构象重原子 |
