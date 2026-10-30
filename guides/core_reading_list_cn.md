# 核心阅读清单

只列入本库已核验完整资料。难度：入门 / 中级 / 高级。论文优先近五年（检索日 2026-10-30，窗口 2021-10-30 起）；经典单列。完整元数据以 `catalog_cn.csv` 为准。

## 入门（本科）

| 编号 | 读什么 | 路径 |
|---|---|---|
| B-10 | Watt《Database Design》2e | `02_data_modeling_storage/books/Watt_DatabaseDesign_2e_en.pdf` |
| B-05 | Morin《Open Data Structures》Python | `01_foundations/books/Morin_OpenDataStructures_Python_en.pdf` |
| B-06 | Downey《Think Stats》2e | `06_analytics_statistics/books/Downey_ThinkStats_2e_en.pdf` |
| B-14 | OSTEP 分章 | `01_foundations/books/ArpaciDusseau_OSTEP_en/` |
| B-17 | Computer Networks: A Systems Approach 在线版 | `01_foundations/books/PetersonDavie_ComputerNetworksASystemsApproach_html_en/` |
| C-05 | MIT Missing Semester | `01_foundations/courses/MIT_MissingSemester_html_en/` |
| C-06 | Berkeley CS186 Sp25 课程页 | `01_foundations/courses/Berkeley_CS186_Spring2025_html_en/` |
| C-01 | CMU 15-445 Fall 2025 讲义 | `01_foundations/courses/CMU_15445_DatabaseSystems_Fall2025_en/` |
| P-09 | dbt Jaffle Shop on DuckDB | `05_ingestion_orchestration/projects/jaffle_shop_duckdb_en/` |

## 中级（存储、SQL、批处理）

| 编号 | 读什么 | 路径 |
|---|---|---|
| B-02 | Foundations of Databases | `01_foundations/books/AbiteboulHullVianu_FoundationsOfDatabases_en.pdf` |
| B-12 | PostgreSQL 14 Internals | `02_data_modeling_storage/books/Rogov_PostgreSQL14Internals_en.pdf` |
| B-01 | MMDS 3e | `03_batch_processing/books/LeskovecRajaramanUllman_MiningOfMassiveDatasets_3e_en.pdf` |
| B-07 | MapReduce 书 | `03_batch_processing/books/LinDyer_DataIntensiveTextProcessingWithMapReduce_en.pdf` |
| C-03 | CMU 15-721 Spring 2024 | `03_batch_processing/courses/CMU_15721_AdvancedDatabaseSystems_Spring2024_en/` |
| S-01 | Spark 官方文档子集 | `03_batch_processing/software_docs/ApacheSpark_official_docs_subset_html_en/` |
| S-05–S-08 | Iceberg / Delta / Hudi / Arrow+Parquet | `02_data_modeling_storage/software_docs/` |
| S-09 | Trino 子集 | `03_batch_processing/software_docs/Trino_official_docs_subset_html_en/` |
| P-02 | Learning Spark V2 代码 | `03_batch_processing/projects/LearningSparkV2_code_en/` |

经典论文：C-Store、Dremel、RDD、Spark SQL、Hive、Impala。近五年：Delta Lake、Lakehouse、LHBench、列存评测、BtrBlocks、Velox、Photon、ClickHouse、Presto HBO、Iceberg 行级操作、MotherDuck。

## 中级（流、CDC、编排）

| 编号 | 读什么 | 路径 |
|---|---|---|
| B-08 | Kafka: The Definitive Guide | `04_stream_processing/books/NarkhedeShapiraPalino_KafkaTheDefinitiveGuide_en.pdf` |
| B-09 | Designing Event-Driven Systems | `04_stream_processing/books/Stopford_DesigningEventDrivenSystems_en.pdf` |
| S-02 | Flink 1.20 文档子集 | `04_stream_processing/software_docs/ApacheFlink_official_docs_subset_html_en/` |
| S-03 | Kafka 官方文档页 | `04_stream_processing/software_docs/ApacheKafka_official_docs_subset_html_en/` |
| S-04 | Debezium 文档子集 | `05_ingestion_orchestration/software_docs/Debezium_official_docs_subset_html_en/` |
| P-03 | Flink training | `04_stream_processing/projects/flink_training_en/` |
| P-04 | Debezium examples | `05_ingestion_orchestration/projects/debezium_examples_en/` |

经典论文：Dataflow Model、MillWheel、Naiad、Discretized Streams、Samza；Kafka 为 Workshop。F1 schema / F1 SQL 在 `05_ingestion_orchestration/papers/`。

## 分析、ML 与治理

| 编号 | 读什么 | 路径 |
|---|---|---|
| B-13 | ISLR 2e | `06_analytics_statistics/books/JamesWittenHastieTibshirani_ISLR_2e_en.pdf` |
| B-03 | Foundations of Data Science | `06_analytics_statistics/books/BlumHopcroftKannan_FoundationsOfDataScience_en.pdf` |
| C-08 | Stanford CS246 课程页 | `06_analytics_statistics/courses/Stanford_CS246_MMDS_course_site_html_en/` |
| P-10 | Great Expectations 教程 | `08_quality_governance/projects/great_expectations_tutorial_en/` |
| P-12 | Feast workshop | `07_large_scale_machine_learning/projects/feast_workshop_en/` |
| P-14 | Dask tutorial | `06_analytics_statistics/projects/dask_tutorial_en/` |

论文：BlinkDB、MacroBase、KLL、DuckPGQ；MLlib、Parameter Server、TFX、Ray、TensorFlow、Hidden Technical Debt；Deequ、Ground。

## 系统、案例与运维

| 编号 | 读什么 | 路径 |
|---|---|---|
| C-04 | MIT 6.824 课程页 | `01_foundations/courses/MIT_6824_DistributedSystems_html_en/` |
| P-11 | Spark+Iceberg compose | `02_data_modeling_storage/projects/docker_spark_iceberg_en/` |
| P-15 | Docker ELK | `09_systems_operations/projects/docker_elk_stack_en/` |
| P-05 | Data Engineering Zoomcamp | `10_practical_applications/projects/data_engineering_zoomcamp_en/` |
| P-08 | ClickHouse examples | `06_analytics_statistics/projects/ClickHouse_examples_en/` |

经典：MapReduce、GFS、Bigtable、Dynamo、Spanner、Mesos、YARN、Borg/K8s、Raft。近五年/工业：Snowflake 弹性引擎（NSDI 2020，窗口外经典补充）、Napa（2021）、Redshift Re-invented（SIGMOD 2022）、ClickHouse（2024）、Procella、Druid、GraphX、Pregel。

## 近五年论文（窗口内，已核验）

文件名见各 `NN_*/papers/`，主要包括：Lakehouse（2021）、Napa（2021）、Photon（2022）、Redshift Re-invented（2022）、Velox（2022）、LHBench（2023）、列存评测（2023/24）、BtrBlocks（2023）、Composable manifesto（2023）、DuckPGQ（2023）、ClickHouse（2024）、Presto HBO（2024）、MotherDuck（2024）、Iceberg 行级操作（2024）。Snowflake NSDI 2020 记为经典补充。完整日期与会议轨道见 `catalog_cn.csv` 的「资料角色」「时间窗口」列。
