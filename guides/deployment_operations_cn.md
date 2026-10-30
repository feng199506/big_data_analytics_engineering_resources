# 部署与运维：集群、容器、存算分离、监控、成本、恢复、升级回滚

本轮**不安装、不启动集群、不部署、不拉镜像**。下列只连接已保存文档、论文和 compose 文件。

## 已保存的运维向资料

**论文**（`09_systems_operations/papers/`）

| 文件 | 会议 | 主题 |
|---|---|---|
| `2011_Hindman_Mesos_en.pdf` | NSDI 2011 主会 | 细粒度共享 |
| `2013_Vavilapalli_ApacheHadoopYARN_en.pdf` | SoCC 2013 主会 | 资源与编程模型解耦 |
| `2016_Burns_BorgOmegaKubernetes_en.pdf` | 综述/系统介绍 | Borg → Omega → Kubernetes |
| `2020_Vuppalapati_BuildingElasticQueryEngine_en.pdf` | NSDI 2020 主会 | Snowflake 存算分离弹性引擎 |
| `2021_Agiwal_Napa_en.pdf` | PVLDB 2021 主会 | Google 数仓稳健查询 |
| `2014_Ongaro_SearchUnderstandableConsensusAlgorithm_en.pdf` | ATC 2014 主会 | Raft；控制面与元数据 |

**项目**

- `09_systems_operations/projects/docker_elk_stack_en/`：Elasticsearch/Logstash/Kibana compose。镜像名仅记录。
- `02_data_modeling_storage/projects/docker_spark_iceberg_en/`：Spark + REST catalog + MinIO compose。
- Spark 文档 `running-on-kubernetes.html`、`spark-standalone.html`、`monitoring.html`。
- Flink `checkpoints` / `savepoints` / `back_pressure`。
- Kubernetes 文档子集若 S-13 核验通过：Job/CronJob、配置、指标、日志。

## 存算分离

Snowflake NSDI 2020 与 Redshift Re-invented、Delta/Iceberg 把**表数据放在对象存储、计算弹性拉起**。本库文档支持的阅读关系：

- 计算：Spark/Trino/Flink 作业
- 存储：S3 兼容（compose 里是 MinIO 镜像名）+ 表格式日志
- 元数据：Iceberg REST/Hive catalog、Kafka 集群、数据库 CDC 位点

故障域不同：计算可以丢，表格式 commit 必须完整。回滚通常是表快照 time travel，而不是「整集群撤销」。

## 监控、容量、成本

文档中出现但**未接入本机**的信号：

- Spark UI / 指标页
- Flink 背压
- Kafka 文档运维锚点
- ClickHouse monitoring 页（S-10 通过后）
- ELK 栈

容量规划数字只存在于 ClickHouse/Snowflake/Napa 论文与厂商文档，本轮无本机对照实验，不能填写「本库测得的成本」。

## 恢复、升级、回滚

| 层 | 已有说明 | 本轮未做 |
|---|---|---|
| 流作业 | Flink savepoint 文档 | 未做版本间 savepoint 兼容试验 |
| 表 | Iceberg/Delta 快照、time travel | 未做生产规模回填 |
| 消息 | Kafka 日志保留与消费者位移 | 未做集群滚动升级 |
| CDC | Debezium 快照重启 | 未对接真实源库 |
| 容器 | compose `restart` 字段 | 未启动 |

升级前应阅读对应 `PAGES_en.txt` 覆盖范围内的版本说明。跨大版本的 Flink/Spark/Iceberg 组合标为「尚待运行验证」，见 `tools_map_cn.md`。

## 安全与凭据

所有示例配置把主机、账号、密钥视为**占位符**。不要把仓库里的默认密码当成可暴露的真实凭据，也不要在本轮填写真实密钥。
