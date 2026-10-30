# 分析实践：探索、抽样、近似、大规模模型与质量

覆盖实践 4、5 中与统计/ML 相关的部分。本轮不拟合模型、不跑 notebook。

## 探索与本地分析

| 资料 | 路径 | 用途 |
|---|---|---|
| Think Stats 2e | `06_analytics_statistics/books/Downey_ThinkStats_2e_en.pdf` | 分布、假设检验入门 |
| ISLR 2e | `06_analytics_statistics/books/JamesWittenHastieTibshirani_ISLR_2e_en.pdf` | 回归、分类、重采样 |
| FoDS | `06_analytics_statistics/books/BlumHopcroftKannan_FoundationsOfDataScience_en.pdf` | 高维、随机投影 |
| MMDS 3e | `03_batch_processing/books/LeskovecRajaramanUllman_MiningOfMassiveDatasets_3e_en.pdf` | 流、LSH、推荐、大规模学习 |
| Dask tutorial | `06_analytics_statistics/projects/dask_tutorial_en/` | 并行 DataFrame **教学** |
| DuckDB CIDR + MotherDuck | `03_batch_processing/papers/` | 嵌入式与混合查询 |
| Polars 文档 | `S-14` 若已核验 | 惰性优化与 Parquet |

单机路径：文件 → DuckDB/Polars/pandas → 汇总表。与 Spark/Trino 的边界是数据是否仍能放进一台机器的内存与临时磁盘。本轮未测临界点。

## 抽样、近似、摘要、在线统计

| 论文 | 路径 | 类型 |
|---|---|---|
| BlinkDB | `06_analytics_statistics/papers/2013_Agarwal_BlinkDB_en.pdf` | 主会；有界误差近似查询 |
| MacroBase | `06_analytics_statistics/papers/2017_Bailis_MacroBase_en.pdf` | 主会；高速数据上的异常优先 |
| KLL quantile sketch | `06_analytics_statistics/papers/2019_Ting_DataSketchesDisaggregatedSubset_en.pdf` | ICML 2016 主会；文件名残留旧种子作者，正文为 Karnin/Lang/Liberty |
| DuckPGQ | `06_analytics_statistics/papers/2023_Wolde_DuckPGQ_en.pdf` | CIDR 2023；分析库上的图查询 |

VerdictDB 因源站证书失败未计入。近似查询的误差保证只在论文假设（独立抽样、分层、sketch 空间）内成立，不能直接写进生产 SLA。

## 大规模回归、聚类、异常、特征管线

| 资料 | 说明 |
|---|---|
| MLlib 论文 | `07_large_scale_machine_learning/papers/2016_Meng_MLlib_en.pdf` |
| Parameter Server | `.../2014_Li_ScalingDistributedMachineLearning_en.pdf`（OSDI） |
| TensorFlow OSDI 2016、Ray OSDI 2018 | 分布式运行时；不是特征正确性证明 |
| TFX KDD 2017 | 连续训练与数据验证；作者 PDF |
| Hidden Technical Debt | 数据依赖、纠缠、监测 |
| Feast workshop | `07_large_scale_machine_learning/projects/feast_workshop_en/`：点-in-time join、训练-服务偏差 |

**数据泄漏**：时间旅行特征必须用事件时间，不能用处理时间或「当前」标签。Feast README 与 Hidden Technical Debt 一起读。本轮未跑特征回溯。

## 质量、Schema、回填（实践 5）

| 资料 | 路径 |
|---|---|
| Deequ | `08_quality_governance/papers/2018_Schelter_AutomatingLargeScaleData_en.pdf` |
| Ground | `08_quality_governance/papers/2017_Hellerstein_Ground_en.pdf`（CIDR） |
| GX 教程 | `08_quality_governance/projects/great_expectations_tutorial_en/` |
| Iceberg evolution / Delta 更新页 | 对应 `software_docs` |
| F1 schema change | `05_ingestion_orchestration/papers/` |

质量检查是门禁，不是事务。Schema 演化若未同时更新下游契约，回填会写入新列空值或拆掉旧报告。血缘工具（DataHub 种子因 CIDR 编号错文被剔除）本轮仅 Ground 论文完整。

## 公开案例（离线 + 实时）

`10_practical_applications/papers/`：Hive（离线仓）、Impala（交互 SQL）、Druid（实时 OLAP）、Snowflake 与 Redshift Re-invented（云仓）、Procella（YouTube 服务+分析）、Pregel/GraphX（图）。日志与传感器端到端示例以 Zoomcamp、Flink training、ELK compose 为代码参考，均未运行。
