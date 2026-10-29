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
