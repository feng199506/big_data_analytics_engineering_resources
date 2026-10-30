# 大数据分析与数据工程资料库

独立目录：`/root/big_data_analytics_engineering_resources/`。检索日 2026-10-30。五年论文窗口：2021-10-30 至 2026-10-30。经典论文单列。

本轮**只收集整理**：不安装依赖、不启动集群、不运行项目、不部署、不上传 GitHub、不删除资料。完成后停止，不进入 MDP、Monte Carlo 或 EM 类别。

## 本轮核验数量（只计本地完整资料）

| 类型 | 目标 | 已核验 | 说明 |
|---|---|---|---|
| 完整教材/参考书 | 10–20 | 14 | 13 本 PDF/分章包 + 1 套 HTML 在线教材 |
| 大学官方课程/讲义 | 8–12 | 8 | 完整讲义包或官方课程页离线集，各计 1 |
| 论文/综述/教程 | ~50 | 58 | 主会/Workshop/综述分列；近五年与经典混编 |
| 官方工具文档 | 10–15 | 12 | HTML 离线子集，覆盖范围见各 `PAGES_en.txt` |
| 完整参考项目 | 10–15 | 14 | git 快照；L1 静态核对；未运行 |

全库去重后编目 106 条（`catalog_cn.csv`）。本轮新下载 106，已有资料库复用 0。失败与缺口 25 条见 `download_failures_cn.csv`。

## 目录

```
01_foundations/ … 10_practical_applications/
guides/          学习与工程指南
scripts/         检索下载脚本与种子、状态（可续跑）
catalog_cn.csv
progress_cn.csv
search_log_cn.md
download_failures_cn.csv
project_readiness_cn.csv
README_cn.md
```

独立创建的索引与指南带 `_cn` 或 `_en` 后缀。上游源码与官方 HTML 内部文件名保持原样，外层目录加 `_en`。

## 指南

- `guides/learning_path_cn.md` — 基础 → 存储与 SQL → 批 → 流 → 分析 → 治理 → 部署
- `guides/tools_map_cn.md` — 工具兼容（文档已写明 vs 尚待运行验证）
- `guides/batch_pipeline_cn.md`
- `guides/streaming_pipeline_cn.md`
- `guides/analytics_practice_cn.md`
- `guides/deployment_operations_cn.md`
- `guides/core_reading_list_cn.md`

## 可运行性

代码与项目：**L0** 已下载，**L1** 已静态核对 README/许可证/入口路径/compose 是否存在。本轮不运行，不声称复现通过。外部服务、数据、凭据、硬件需求见 `project_readiness_cn.csv`。配置视为占位符。

不得把组件 exactly-once 当成端到端保证。不得把 notebook 演示当成已验证生产平台。

## 续跑

状态在 `scripts/state/`。种子在 `scripts/seeds/`。

```bash
cd /root/big_data_analytics_engineering_resources
python3 -I scripts/materials_en.py status
python3 -I scripts/papers_en.py status
python3 -I scripts/materials_en.py fetch software --retry-failed
python3 -I scripts/papers_en.py download NN --target 12 --retry-failed
python3 -I scripts/build_catalog_en.py
```

`NN` 为 `01`–`10`。已 `verified`/`ok` 的条目会跳过。不要用本脚本绕过付费墙。不要下载大型数据集、镜像或安装包。

论文错链（CIDR 编号对不上正文）必须 `reject`，禁止把错误 PDF 计为完整成果。
