# 批处理管线：文件/库 → 清洗转换 → 分析表 → 查询报告

对照本库资料阅读，不运行。模式对应收集规格中的实践 1、4、6。

## 参考实现（均 L1，未执行）

| 项目 | 路径 | 批或流 | 规模/硬件 | 说明 |
|---|---|---|---|---|
| dbt Jaffle Shop | `05_ingestion_orchestration/projects/dbt_jaffle_shop_en/` | 批/ELT | 小型种子；需 dbt Cloud 或适配器 | README 以 Cloud 为主；根目录无 LICENSE |
| dbt Jaffle Shop DuckDB | `05_ingestion_orchestration/projects/jaffle_shop_duckdb_en/` | 本地批/ELT | 种子 CSV；单机 DuckDB | 有 LICENSE、`requirements.txt`、模型测试 |
| Learning Spark V2 | `03_batch_processing/projects/LearningSparkV2_code_en/` | 批为主 | 章节示例；需 Spark 发行版 | 大型 parquet 已按种子丢弃 |
| LHBench | `02_data_modeling_storage/projects/lhbench_en/` | 批、格式对比 | 基准需自备数据 | **不下载大型数据集** |
| Delta examples | `02_data_modeling_storage/projects/delta_examples_en/` | 批/增量 | 示例级 | 表级事务 ≠ 管线 exactly-once |
| Spark+Iceberg compose | `02_data_modeling_storage/projects/docker_spark_iceberg_en/` | 批 SQL | 本地 compose | 不拉镜像、不启动 |
| Zoomcamp | `10_practical_applications/projects/data_engineering_zoomcamp_en/` | 批+编排教学 | 课程数据需另取 | 含 notebook；非生产验证 |
| ClickHouse examples | `06_analytics_statistics/projects/ClickHouse_examples_en/` | 分析查询 | 示例含 compose | 不拉镜像 |

入口命令以各 README 为准（常见：`dbt seed && dbt run && dbt test`；Spark 示例的 `spark-submit`）。本轮不执行。

## 与论文/文档的对应

1. **存储层**：Parquet/Arrow 文档；C-Store、Dremel、列存评测、BtrBlocks。分区与压缩决定后续 Shuffle 体积。
2. **表格式**：Iceberg/Delta/Hudi 文档。增量更新用 copy-on-write 或 merge-on-read（Iceberg 行级操作论文 PVLDB 2024）。
3. **执行**：RDD 血缘与宽依赖；Spark SQL Catalyst；Photon 向量化；Trino 优化器与 HBO。
4. **调度**：Airflow DAG（若 S-12 已保存）只保证任务重试与依赖，不保证数据一次写入。

## 失败、重复、回填

- 批作业重跑必须**幂等**：覆盖分区、merge 主键、或可重建的物化表。dbt 增量模型的 unique key 只在该模型边界内有效。
- 回填：按分区日期重跑；文档中的 `backfill`/`rerun` 依赖调度器与表格式快照，需同时读编排文档和表格式演化页。
- Shuffle 失败：Spark 文档 `tuning.html` 的推测执行与本地磁盘。本轮未做性能对比实验。

## 交付语义

批处理通常是「作业成功则输出完整、失败则不发布」。这仍取决于：

- 写入是覆盖还是追加；
- 是否有成功标记/分区提交；
- 下游是否会读到半成品。

**不要**把 Spark 作业成功或 Iceberg commit 成功说成「整条公司报表管线 exactly-once」。

## 性能测试与成本（规格 6）

LHBench 与 ClickHouse VLDB 2024、列存评测论文提供方法，但本轮：

- 未跑基准；
- 未记录本机硬件数字；
- 成本比较只能引用论文表格，不能当作本库复现结果。
