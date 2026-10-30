# 学习路径：基础 → 存储与 SQL → 批处理 → 流处理 → 分析建模 → 治理 → 部署维护

只关联本库已核验、已落地的资料。检索日 2026-10-30。本轮不安装依赖、不启动集群、不运行项目。

难度：入门（本科） / 中级（本科高年级或硕士课） / 高级（研究生方法与生产系统论文）。

## 1. 基础（数据库、SQL、算法、概率、Linux、网络、分布式）

**入门**

- Watt《Database Design》2e：`02_data_modeling_storage/books/Watt_DatabaseDesign_2e_en.pdf`
- Morin《Open Data Structures》(Python)：`01_foundations/books/Morin_OpenDataStructures_Python_en.pdf`
- Downey《Think Stats》2e：`06_analytics_statistics/books/Downey_ThinkStats_2e_en.pdf`
- MIT Missing Semester 离线页：`01_foundations/courses/MIT_MissingSemester_html_en/`
- Berkeley CS186 Spring 2025 课程页：`01_foundations/courses/Berkeley_CS186_Spring2025_html_en/`

**中级**

- CMU 15-445/645 Fall 2025 讲义包（24 个 PDF，131 页）：`01_foundations/courses/CMU_15445_DatabaseSystems_Fall2025_en/`
- Abiteboul, Hull, Vianu《Foundations of Databases》：`01_foundations/books/AbiteboulHullVianu_FoundationsOfDatabases_en.pdf`
- Erickson《Algorithms》：`01_foundations/books/Erickson_Algorithms_en.pdf`
- OSTEP 分章 PDF：`01_foundations/books/ArpaciDusseau_OSTEP_en/`
- MIT 6.824/6.5840 课程页：`01_foundations/courses/MIT_6824_DistributedSystems_html_en/`
- Peterson & Davie《Computer Networks: A Systems Approach》在线版：`01_foundations/books/PetersonDavie_ComputerNetworksASystemsApproach_html_en/`

**经典系统论文（五年前，单列）**

- MapReduce、GFS、Bigtable、Dynamo、Spanner：`01_foundations/papers/`
- Raft（ATC 2014）：`09_systems_operations/papers/2014_Ongaro_SearchUnderstandableConsensusAlgorithm_en.pdf`

## 2. 存储与 SQL（建模、文件格式、列存、分区、湖仓）

**教材与课**

- Rogov《PostgreSQL 14 Internals》：`02_data_modeling_storage/books/Rogov_PostgreSQL14Internals_en.pdf`
- CMU 15-721 Spring 2024 幻灯（23 个 PDF，1366 页）：`03_batch_processing/courses/CMU_15721_AdvancedDatabaseSystems_Spring2024_en/`

**格式与表格式（官方文档子集）**

- Iceberg 规范/分区/演化/Spark：`02_data_modeling_storage/software_docs/ApacheIceberg_official_docs_subset_html_en/`
- Delta Lake 批/流/并发：`02_data_modeling_storage/software_docs/DeltaLake_official_docs_subset_html_en/`
- Hudi 表类型与写入：`02_data_modeling_storage/software_docs/ApacheHudi_official_docs_subset_html_en/`
- Arrow 列式 + Parquet 文件格式：`02_data_modeling_storage/software_docs/ArrowParquet_official_docs_subset_html_en/`

**论文顺序**

1. C-Store（VLDB 2005）、Dremel（PVLDB 2010）
2. Delta Lake（PVLDB 2020）、Lakehouse（CIDR 2021）
3. 近五年：LHBench、列存评测（PVLDB 2024）、BtrBlocks、Velox、Composable manifesto、Iceberg 行级操作（PVLDB 2024）

路径：`02_data_modeling_storage/papers/`

**项目（L1 静态核对，未运行）**

- Spark+Iceberg compose 参考：`02_data_modeling_storage/projects/docker_spark_iceberg_en/`（含 `docker-compose.yml`；不拉镜像）
- Delta examples：`02_data_modeling_storage/projects/delta_examples_en/`
- LHBench：`02_data_modeling_storage/projects/lhbench_en/`

## 3. 批处理（执行计划、连接、聚合、Shuffle、容错、增量）

**教材**

- MMDS 3e：`03_batch_processing/books/LeskovecRajaramanUllman_MiningOfMassiveDatasets_3e_en.pdf`
- Lin & Dyer MapReduce 书：`03_batch_processing/books/LinDyer_DataIntensiveTextProcessingWithMapReduce_en.pdf`

**文档与论文**

- Spark 官方文档子集（SQL/RDD/Structured Streaming/调优/K8s）：`03_batch_processing/software_docs/ApacheSpark_official_docs_subset_html_en/`
- Trino 概念/优化器/Hive 与 Iceberg 连接器：`03_batch_processing/software_docs/Trino_official_docs_subset_html_en/`
- RDD（NSDI 2012）、Spark SQL（SIGMOD 2015）、DryadLINQ（OSDI 2008）、Photon（SIGMOD 2022）、ClickHouse（PVLDB 2024）、Presto HBO（PVLDB 2024）、DuckDB/MotherDuck（CIDR）：`03_batch_processing/papers/`

**项目**

- Learning Spark 2e 配套代码：`03_batch_processing/projects/LearningSparkV2_code_en/`
- Data Engineering Zoomcamp（跨批/流/编排，见第 7 节）

## 4. 流处理（消息、事件时间、窗口、水位线、状态、检查点、背压、交付语义）

**教材**

- Kafka Definitive Guide（Confluent 赠阅完整 PDF）：`04_stream_processing/books/NarkhedeShapiraPalino_KafkaTheDefinitiveGuide_en.pdf`
- Stopford《Designing Event-Driven Systems》：`04_stream_processing/books/Stopford_DesigningEventDrivenSystems_en.pdf`

**文档**

- Flink 1.20 子集（时间、有状态流、检查点/保存点、背压）：`04_stream_processing/software_docs/ApacheFlink_official_docs_subset_html_en/`
- Kafka 官方单页文档离线集：`04_stream_processing/software_docs/ApacheKafka_official_docs_subset_html_en/`（Kafka 文档为锚点结构，覆盖范围为该页所列章节，见 `PAGES_en.txt`）

**论文（主会与 Workshop 分列）**

- 主会：Dataflow Model、MillWheel、Naiad、Discretized Streams（SOSP）、Samza
- Workshop：Kafka 2011 NetDB
- 路径：`04_stream_processing/papers/`

**项目**

- Flink 官方训练：`04_stream_processing/projects/flink_training_en/`

组件级 checkpoint/exactly-once **不能**自动推广为端到端业务管线保证。见 `streaming_pipeline_cn.md`。

## 5. 接入与编排（CDC、ETL/ELT、调度、重试、幂等、回填）

- Debezium 官方文档子集：`05_ingestion_orchestration/software_docs/Debezium_official_docs_subset_html_en/`
- F1 在线 schema 变更与 F1 SQL：`05_ingestion_orchestration/papers/`
- dbt Jaffle Shop：`05_ingestion_orchestration/projects/dbt_jaffle_shop_en/`（Cloud 向；根目录无 LICENSE）
- dbt + DuckDB 本地 ELT：`05_ingestion_orchestration/projects/jaffle_shop_duckdb_en/`（有 LICENSE、种子数据、测试说明）
- Debezium examples：`05_ingestion_orchestration/projects/debezium_examples_en/`（多份 compose；不拉镜像）

Airflow + dbt 官方文档子集若 `S-12` 核验通过，位于 `05_ingestion_orchestration/software_docs/`。

## 6. 分析建模（探索、抽样、近似、大规模回归/聚类/异常、特征）

- FoDS、ISLR2、Think Stats：`06_analytics_statistics/books/`
- Stanford CS246 课程页：`06_analytics_statistics/courses/Stanford_CS246_MMDS_course_site_html_en/`
- MacroBase、BlinkDB、KLL sketch、DuckPGQ：`06_analytics_statistics/papers/`
- ClickHouse / DuckDB / Polars 文档：以 `software_docs/` 实际核验目录为准
- Dask tutorial：`06_analytics_statistics/projects/dask_tutorial_en/`（notebook 教学，**不是**已验证生产平台）
- ClickHouse examples：`06_analytics_statistics/projects/ClickHouse_examples_en/`
- Feast workshop：`07_large_scale_machine_learning/projects/feast_workshop_en/`（点-in-time 与泄漏防范说明；未运行）
- 分布式学习：Parameter Server、MLlib、TensorFlow、Ray、TFX、Hidden Technical Debt：`07_large_scale_machine_learning/papers/`

## 7. 治理与部署维护

- Deequ（数据质量）、Ground（数据上下文）：`08_quality_governance/papers/`
- Great Expectations 教程：`08_quality_governance/projects/great_expectations_tutorial_en/`
- Mesos、YARN、Borg/Omega/K8s、Snowflake 存算分离（NSDI）、Napa：`09_systems_operations/papers/`
- Docker ELK compose 参考：`09_systems_operations/projects/docker_elk_stack_en/`（不启动）
- Zoomcamp 综合案例：`10_practical_applications/projects/data_engineering_zoomcamp_en/`
- 工业案例论文：Hive、Impala、Druid、Snowflake、Redshift Re-invented、Procella、Pregel、GraphX：`10_practical_applications/papers/`

细节见 `deployment_operations_cn.md` 与 `analytics_practice_cn.md`。

## 建议顺序（约 12–16 周自学，不运行集群）

1. 15-445 讲义 + Database Design + Think Stats（2–3 周）
2. OSTEP 存储/并发章 + 6.824 课程页 + MapReduce/GFS/Bigtable（2 周）
3. Iceberg/Delta/Parquet 文档子集 + C-Store/Dremel/Delta Lake 论文（2 周）
4. Spark 文档 + RDD/Spark SQL + LearningSparkV2 源码阅读（2 周）
5. Kafka 书 + Dataflow/MillWheel + Flink 文档与 training 源码阅读（2 周）
6. dbt DuckDB 项目结构 + Debezium examples 阅读 + F1 schema 论文（1–2 周）
7. ISLR2 选章 + MacroBase/KLL + Feast README 中的泄漏说明（1–2 周）
8. Deequ/GX 教程结构 + Borg/K8s 论文 + ELK compose 阅读（1 周）

续跑方式见根目录 `README_cn.md`。
