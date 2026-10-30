# 工具对照图（仅文档已支持的关系）

本图只记录本库**已保存的官方文档或源码说明**里写明的组合。未在本轮运行验证的组合一律标为「尚待运行验证」。不得把单个组件的 exactly-once 声明写成整条业务管线保证。

维护状态以抓取时官方站点为准（2026-10-30 前后）。许可证见各快照 LICENSE 或文档页。

## 已保存的官方文档子集

| 编号 | 工具 | 本地路径 | 本轮覆盖（见各目录 `PAGES_en.txt`） |
|---|---|---|---|
| S-01 | Apache Spark | `03_batch_processing/software_docs/ApacheSpark_official_docs_subset_html_en/` | SQL、RDD、Structured Streaming、调优、配置、监控、standalone、K8s |
| S-02 | Apache Flink 1.20 | `04_stream_processing/software_docs/ApacheFlink_official_docs_subset_html_en/` | Learn Flink、时间、有状态流、checkpoints、savepoints、背压 |
| S-03 | Apache Kafka | `04_stream_processing/software_docs/ApacheKafka_official_docs_subset_html_en/` | 单页文档；入门/设计/API/语义为页内锚点 |
| S-04 | Debezium | `05_ingestion_orchestration/software_docs/Debezium_official_docs_subset_html_en/` | 架构、特性、连接器、SMT、Server、日志 |
| S-05 | Apache Iceberg | `02_data_modeling_storage/software_docs/ApacheIceberg_official_docs_subset_html_en/` | spec、Spark 入门、分区、演化、可靠性、读写 |
| S-06 | Delta Lake | `02_data_modeling_storage/software_docs/DeltaLake_official_docs_subset_html_en/` | 批、流、更新、并发、最佳实践 |
| S-07 | Apache Hudi | `02_data_modeling_storage/software_docs/ApacheHudi_official_docs_subset_html_en/` | 概念、写操作、表类型、并发、流摄入、查询 |
| S-08 | Arrow + Parquet | `02_data_modeling_storage/software_docs/ArrowParquet_official_docs_subset_html_en/` | 列式格式、Python、Flight、Parquet 文件格式 |
| S-09 | Trino | `03_batch_processing/software_docs/Trino_official_docs_subset_html_en/` | 概念、优化器、配置、Hive/Iceberg 连接器、安全 |
| S-10 | ClickHouse | `06_analytics_statistics/software_docs/ClickHouse_official_docs_subset_html_en/` | 介绍、MergeTree、优化、监控、Kafka、安装 |
| S-12 | Airflow + dbt | `05_ingestion_orchestration/software_docs/Airflow_dbt_official_docs_subset_html_en/` | DAG/任务/调度；dbt 简介与增量模型 |
| S-14 | Polars | `06_analytics_statistics/software_docs/Polars_official_docs_subset_html_en/` | 入门、类型、Parquet、惰性优化与并行（6 页子集） |

DuckDB 官方 HTML 因页面正文过短（站点偏脚本渲染）未计完整文档集，改以 CIDR 论文与 `jaffle_shop_duckdb_en` 源码为准。Kubernetes / Dagster 子集若尚未出现在 `catalog_cn.csv`，记为缺口，见 `download_failures_cn.csv`。

## 本地与并行分析代码

| 项目 | 路径 | 角色 | 运行声明 |
|---|---|---|---|
| pandas | 未单独抓全站文档；Zoomcamp 与 dbt 项目依赖说明中出现 | 单机表分析 | 未运行 |
| Polars | `06_analytics_statistics/software_docs/Polars_official_docs_subset_html_en/` | 本地并行 DataFrame | 未运行 |
| Dask | `06_analytics_statistics/projects/dask_tutorial_en/` | 并行 DataFrame 教程 | L1 静态；notebook ≠ 生产平台 |
| DuckDB | CIDR 论文 + `jaffle_shop_duckdb_en` | 嵌入式 OLAP | 未运行 |

## 文档写明、本轮未运行的兼容组合

以下组合在**已保存文档或项目 README**中出现，可作为后续隔离实验的候选。全部为「尚待运行验证」。

| 组合 | 文档依据 | 常见前提（摘自文档，未实测） | 本轮状态 |
|---|---|---|---|
| Spark SQL ↔ Iceberg | Iceberg `spark-getting-started` / `spark-writes`；`docker_spark_iceberg_en` compose | 匹配的 Spark 与 Iceberg 运行时版本；catalog（REST/Hive） | 尚未运行验证 |
| Spark ↔ Delta Lake | Delta `delta-batch.html`、`delta-streaming.html`；`delta_examples_en` | 匹配的 `delta-spark` 与 Spark 版本 | 尚未运行验证 |
| Spark ↔ Hudi | Hudi `spark` 写/查询页 | Spark 与 Hudi bundle 版本矩阵 | 尚未运行验证 |
| Trino ↔ Iceberg / Hive | Trino `connector/iceberg.html`、`connector/hive.html` | catalog 配置、对象存储凭据 | 尚未运行验证 |
| Flink ↔ Kafka | Flink 连接器文档未全量抓取；Kafka 语义页 + `flink_training_en` | 主题分区、消费者组、checkpoint 对齐 | 尚未运行验证 |
| Debezium ↔ Kafka | Debezium architecture/connectors；`debezium_examples_en` | Kafka Connect 或 Debezium Server；源库 CDC 权限 | 尚未运行验证 |
| dbt ↔ DuckDB | `jaffle_shop_duckdb_en` README / `profiles.yml` 占位 | 本地 DuckDB 文件；dbt 适配器版本 | 尚未运行验证 |
| dbt ↔ 云仓 | `dbt_jaffle_shop_en` README（dbt Cloud） | 仓库凭据；本轮不配置真实密钥 | 尚未运行验证 |
| ClickHouse ↔ Kafka | ClickHouse `integrations/kafka` 页（S-10 通过后） | 引擎与消息格式 | 尚未运行验证 |
| Spark Structured Streaming ↔ 文件/Kafka 源 | Spark Structured Streaming 编程指南 | 源/汇的交付语义由连接器决定 | 尚未运行验证 |
| Feast 离线/在线存储 | `feast_workshop_en` | 时间戳字段与 store 配置 | 尚未运行验证 |

## 明确不要默认成立的关系

- Iceberg/Delta/Hudi 的**表级 ACID 或快照隔离** ≠ 整条 ETL 的 exactly-once。
- Flink checkpoint 或 Kafka `acks=all` ≠ 源库 + 消息 + 作业 + 汇的端到端一次处理。
- Trino/Spark/ClickHouse 任一引擎的幂等写入取决于主键、分区覆盖还是 merge-on-read，必须按作业配置阅读，不能互相套用。
- compose 文件中的镜像名只是记录，本轮不拉取、不启动。
- Zoomcamp 与 Dask tutorial 含 notebook：计为教学参考，不计「已验证生产平台」。

## 版本与许可证（抓取时）

- Spark / Flink / Kafka / Iceberg / Hudi / Arrow / Parquet / Airflow：Apache-2.0（以官方仓库与 NOTICE 为准）。
- Delta Lake：Linux Foundation，软件 Apache-2.0。
- Debezium：Apache-2.0。
- Trino：Apache-2.0。
- DuckDB：MIT（论文与项目各记各的）。
- Kubernetes 文档：CC BY 4.0（若 S-13 核验通过）。
- 具体 commit 见各项目 `SNAPSHOT_en.txt`。

兼容矩阵的**数字版本**以各 HTML 子集抓取时的 `docs/latest` 或 `release-1.20` 为准，升级后需重新对照官方 compatibility 页。本轮未做跨版本矩阵测试。
