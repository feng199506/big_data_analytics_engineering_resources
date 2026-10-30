# 检索日志

检索日：2026-10-30。五年窗口：2021-10-30 至 2026-10-30。经典论文单列。本轮只收集“大数据分析与数据工程”，完成后停止，不进入 MDP、Monte Carlo 或 EM 类别。

## 已有资料库核查

| 资料库 | 路径 | 结果 |
|---|---|---|
| 信号处理文献库 | `/root/signal_processing_literature` | 存在。本轮主题弱相关，不复用正文。脚本体例复用。 |
| 近期顶会研究 | `/root/recent_top_conference_research` | 存在。以 GP/时间序列/工业监控为主；大数据系统论文按需核验后复用，不移动原件。 |
| 编程 / AI 课程 / 概率统计课程库 | `/root/programming_*`、`/root/ai_undergraduate_graduate_curriculum_literature`、`/root/probability_statistics_curriculum_literature` | 本机目录不在；仅见 `/root/.cache/*_lit` 缓存残件。本轮无法复制原件。 |
| 控制 / 机器人 / 无人机 / 高斯过程 | 兄弟库路径 | 本机不存在对应 `/root/*_literature` 目录。 |

规则：不移动原件、不重复计数；复用项在本库重新核验。

## 检索渠道

- 教材：作者站点免费全书、CC/开放教材、CUP/O'Reilly 作者或厂商赠阅完整 PDF、分章免费 PDF。
- 课程：大学官方课程页讲义包（CMU、MIT、Stanford、Berkeley 等），优先近年版。
- 论文：SIGMOD / PVLDB / VLDB / ICDE / OSDI / SOSP / NSDI / KDD / MLSys；优先 PVLDB、USENIX、CIDR、作者 PDF、arXiv 接受稿。主会、Workshop、Demo、教程、综述分列。
- 软件：官方文档站点 HTML 子集与 GitHub 官方仓库快照。
- 项目：官方 examples/training 仓库；丢弃大型数据、镜像与构建产物。

不绕过付费墙、登录或访问限制。不下载商业软件本体、容器镜像、依赖缓存或大型数据集。

## 执行记录

- 2026-10-30 建库、脚本与种子；开始教材下载。
- 教材：13 本 PDF/分章包核验通过；B-17 Peterson/Davie HTML 在线教材 78 页核验通过；B-16 Linux Command Line 失败；Learning Spark 等付费墙未绕过。
- 课程：C-01 CMU 15-445 F2025 讲义 24 PDF/131 页；C-03 CMU 15-721 S2024 幻灯 23 PDF/1366 页；C-04/C-05/C-06/C-07/C-08/C-09 为官方 HTML 离线集。OCW 两门因索引正则未命中失败，未凑数。
- 论文：优先 PVLDB/USENIX/CIDR/作者 PDF。arXiv 猜测 ID 一律先核 API 标题，错误 ID 不用。CIDR 编号错文（所谓 DBLog、DataHub、C-Store P01）已 reject。Photon 改 CIDR 官方 a100 后仍为 1 页未计，改用 CMU 15-721 课程阅读的 SIGMOD 长文。Redshift Re-invented 用同一课程阅读 PDF 并更正第一作者。KLL sketch 按正文作者 Karnin 等登记。Flink 状态 PVLDB PDF 返回 HTML 未计。共 58 篇完整。
- 软件文档：Spark、Flink 1.20、Kafka、Debezium、Iceberg、Delta、Hudi、Arrow+Parquet、Trino、ClickHouse、Airflow+dbt 共 11 套子集。DuckDB 文档页正文过短失败。Kubernetes/Polars/Dagster 未在本轮编目完成。
- 项目：14 个 git 快照（commit 见 SNAPSHOT_en.txt）。ClickHouse examples 86 MiB 归档在上限内通过。Dagster University 需登录，改公开 jaffle_shop_duckdb。Trino getting-started 归档超 40 MiB 未计。
- 已有编程/AI/统计资料库本机无完整目录可复用；本轮复用计数 0。
- 索引：`python3 -I scripts/build_catalog_en.py` → catalog/progress/failures/project_readiness。指南七份已写。
- 本轮停止。不进入 MDP / Monte Carlo / EM。

## 缺口（续跑候选）

- DuckDB 官方 HTML（脚本渲染）、Polars/Dagster/K8s 文档子集、Flink 状态管理 PVLDB 长文、Structured Streaming 作者 PDF（主机拒连）、Goods/Databus/VerdictDB 源站失败。
- 课程：MIT OCW 6.033 / 6.830 索引正则。
- 不把失败项计为完整成果。
