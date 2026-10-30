# 流处理管线：传感器/日志 → 消息 → 流作业 → 存储与可视化

对照本库资料阅读，不运行。覆盖实践 2、3。事件时间与处理时间必须分开写。

## 参考实现（L1，未执行）

| 项目 | 路径 | 批或流 | 事件时间 vs 处理时间 | 顺序/重复/失败 |
|---|---|---|---|---|
| Flink training | `04_stream_processing/projects/flink_training_en/` | 流练习 | README 与练习覆盖事件时间窗口 | 练习环境；作业失败后从 checkpoint 恢复是 Flink 语义，不是业务端到端 |
| Debezium examples | `05_ingestion_orchestration/projects/debezium_examples_en/` | CDC → 消息 | 源库日志时间 vs Connect 处理时间 | 快照+增量；重复投递需汇侧去重 |
| Zoomcamp 流章节 | `10_practical_applications/projects/data_engineering_zoomcamp_en/` | 课程流示例 | 以该章笔记为准 | notebook/教学 |
| Docker ELK | `09_systems_operations/projects/docker_elk_stack_en/` | 近实时日志 | 处理时间摄入；事件时间取决于日志字段 | compose 参考，不启动 |
| ClickHouse examples | `06_analytics_statistics/projects/ClickHouse_examples_en/` | 部分接 Kafka | 引擎与物化视图定义 | 示例 |

## 必读论文（主会 / Workshop 分列）

**主会**

- Dataflow Model（PVLDB 2015）：事件时间、水位线、触发器、乱序
- MillWheel（PVLDB 2013）：低水位、持久状态
- Discretized Streams（SOSP 2013）：微批 RDD、并行恢复
- Naiad（SOSP 2013）：timely dataflow
- Samza（PVLDB 2017）：本地状态 + Kafka 日志

**Workshop**

- Kafka（NetDB 2011）：commit log、分区、消费者组。**不是** SIGMOD/VLDB 主会。

路径：`04_stream_processing/papers/`。Flink 状态管理 PVLDB 长文因官方 PDF 返回 HTML 未计入完整论文；概念以 Flink 1.20 文档子集为准。

## 文档中的语义边界

摘自已保存文档的**常见条件**（未在本机验证）：

| 声明 | 通常前提 | 不能推广到 |
|---|---|---|
| Kafka 提交日志持久 | `acks`、ISR、磁盘 fsync 配置 | 消费者至少一次处理后的业务表 |
| Flink exactly-once sink | checkpoint 完成、对齐 barrier、汇支持事务或幂等写 | 源 CDC 快照窗口、人工重放、旁路脚本 |
| Spark Structured Streaming 精确一次 | 源可重放 + 汇幂等/事务 | 任意 Kafka 主题 + 任意 JDBC 汇 |
| Debezium 快照+流 | 源库保留 WAL/binlog；gtid 或 LSN 不丢 | 无主键表、无序广播、跨库事务 |

## CDC → 增量更新 → 去重（实践 3）

阅读顺序：

1. Debezium 架构与连接器页
2. F1 在线 schema 变更论文（`05_ingestion_orchestration/papers/2013_Rae_OnlineAsynchronousSchemaChange_en.pdf`）
3. Iceberg/Delta/Hudi 的 upsert 与 schema 演化页
4. `debezium_examples_en` 中对应数据库目录的 README 与 compose（占位符凭据，不启动）

乱序：以事件时间 + watermark 延迟为准，不以处理时间墙钟为准。迟到事件是**数据正确性**问题，不是只调并行度能消掉的性能问题。

## 背压、检查点、状态

Flink 文档子集：`docs/ops/monitoring/back_pressure/`、`docs/ops/state/checkpoints/`、`docs/concepts/stateful-stream-processing/`（1.20）。状态过大、反压和 checkpoint 超时会互相放大。本轮无集群指标。

## 可视化

ELK compose 与 Zoomcamp 仪表章节只提供**文件级**说明。本轮不部署 Kibana/Grafana，不声称可观测性已打通。
