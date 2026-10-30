# 下载与恢复说明（大数据分析与数据工程资料库，2026-10-29 发布）

## 1. 发布了什么

| 位置 | 内容 |
|---|---|
| Git 分支 `release-lite-20261029` | 说明文件、目录 `catalog_cn.csv`、指南 `guides/`、检索下载脚本 `scripts/`，以及本文件、`archive_index_cn.csv`、`windows_rename_map_cn.csv`、`release_excluded_cn.csv`。不含论文、教材、课程讲义、软件文档和参考项目全文。 |
| Release `bigdata-full-20261029` 的附件 | 1 个不压缩 tar 包 `big_data_analytics_engineering_resources_20261029_batch001_cn_en.tar`（1,030,750,208 字节，约 983 MB），内含资料库全部内容（7,799 个文件、3 个空目录），以及上面 4 个说明文件和 `upload_report_cn.md`。 |

打包内容是 2026-10-30 02:29（中欧时间）对资料库做的完整拷贝快照，资料库最后一次改动在 01:53。

**未发布 1 项**：B-14《Operating Systems: Three Easy Pieces》（64 个分章 PDF）。作者在官方页面请使用者直接链接、不要自留副本，因此不随包再分发。官方页面 https://pages.cs.wisc.edu/~remzi/OSTEP/ 可免费逐章下载，详见 `release_excluded_cn.csv`。离线首页里这一条也指向官方页面。

## 2. Windows 下载与解压

1. 在 Release 页面点击 tar 包下载，浏览器直接保存即可。
2. **解压到一个短路径的文件夹，例如 `D:\bd\`**。
   - 包内最长相对路径 201 个字符，主要是参考项目里的深层源码和测试结果。
   - 如果解压到默认的 `C:\Users\<用户名>\Downloads\<包名>\`，前缀约 90 个字符，部分文件会超过 Windows 260 字符的路径上限，出现“路径太长 / 文件名无效”错误。
   - 解压到 `D:\bd\` 时，全部路径都在 210 个字符以内。
3. 解压工具任选其一：7-Zip、WinRAR，或 Windows 11 资源管理器自带的“全部解压缩”。
4. 解压后得到 `D:\bd\01_foundations\` … `D:\bd\10_practical_applications\`、`guides\`、`scripts\` 和根目录文件。

## 3. 离线阅读

**从 `index_offline_cn.html` 开始**：双击即可用浏览器打开。它列出目录中的全部 106 条资料，“打开”链接直接指向包内的 PDF 或网页入口页。指南和 README 另有网页版（同名 `.html`），文中提到的资料路径都可点击。

为了让 Windows 下离线打开网页不报错、页面之间能离线跳转，发布包里对保存的网页做了以下处理（原资料库未改动）：

- **页面之间的链接改为本地跳转**：原来逐页保存的官方文档和课程网站中，指向已保存页面的绝对网址改成了本地相对路径，共 4,041 处。
- **本地没有保存的页面**：仍链接到原网站，需联网才能打开，不会出现“找不到文件”。
  - 另有 11 处原本指向本地不存在文件的链接（以 `/` 开头或缺失的相对路径），也改成了原网站网址。
- **补全缺失的样式、图片和公式渲染**：共下载 374 个文件（约 17.8 MB），放在各资料目录下。这些是页面引用了、原库却没保存的文件，例如：
  - Delta Lake 文档的样式表；
  - Computer Networks: A Systems Approach 网页教材的本地 MathJax（公式离线可显示）；
  - 课程网站的 Bootstrap 和 Font Awesome；
  - Missing Semester 中的 xkcd 等插图。
  - 每个文件的来源网址见 `windows_rename_map_cn.csv` 中“新增（离线补全）”行。
- **停用 27 个会出错的框架脚本**：Hudi 与 dbt（Docusaurus）、ClickHouse（Mintlify）的框架脚本从磁盘打开时会把正文换成 “Page Not Found” 或报错页，已停用。页面正文是保存下来的静态 HTML，可以正常阅读。
  - 这些页面的折叠菜单、深色模式切换等交互不可用。
  - 有标签页的地方会把所有标签内容依次显示。
- **关闭即时导航**：Polars 文档的 6 个页面关闭了“即时导航”，点击链接按普通页面跳转。

**离线时仍然不可用的部分（不影响阅读正文）**：
- 站内搜索框；
- 访问统计、聊天助手、cookie 横幅；
- GitHub 徽章、贡献者头像中未能保存的部分；
- 嵌入的 YouTube 视频。

## 4. Windows 文件名改动

所有改动逐条记在 `windows_rename_map_cn.csv`（原相对路径 → 发布包内相对路径）。

- 73 个文件名含 Windows 不允许的字符（主要是网页样式与脚本的 `?v=…` 版本后缀），改为 `_`。引用它们的网页已同步改写。
- 81 个过长的名字截短为“前 12 个字符 + 原名哈希”。其中 4 个官方文档目录改了名，导致其下 1,190 个文件路径随之变化：
  - `Airflow_dbt_official_docs_subset_html_en` → `Airflow_dbt__edc2fdf2`
  - `ApacheFlink_official_docs_subset_html_en` → `ApacheFlink__6527bb76`
  - `ApacheIceberg_official_docs_subset_html_en` → `ApacheIceber_cafd092f`
  - `ClickHouse_official_docs_subset_html_en` → `ClickHouse_o_60158788`

  `catalog_cn.csv` 的“本地路径”列仍是原名，按离线首页打开或对照改名表即可。
- 没有仅大小写不同的文件冲突。

## 5. Linux / macOS

```bash
mkdir -p ~/bd && tar -xf big_data_analytics_engineering_resources_20261029_batch001_cn_en.tar -C ~/bd
```

然后用浏览器打开 `~/bd/index_offline_cn.html`。

## 6. 状态与完整性

- 打包时校验过：tar 与写盘命令退出码为 0，包内文件列表与计划列表逐行一致，每个文件的归属见 `archive_index_cn.csv`。
- 未提供 SHA-256 校验值，上传后也未做下载回验。
- 离线效果基于对全部保存网页的静态链接检查：已保存页面之间没有指向缺失本地文件的链接。**没有在 Windows 实机浏览器里逐页打开验证。**
- 代码项目（`projects/`）按原仓库快照保存，未运行。其中示例应用自身的路由链接（如 `/admin`）不是阅读用链接，未改动。
