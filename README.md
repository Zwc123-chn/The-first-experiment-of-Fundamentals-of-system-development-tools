# Fundamentals of system development tools — Experiment 1

> 
> 授课内容：课程概览 + Shell 入门；Version Control and Git; LaTeX 文档编辑

## 第 1 题 含空格文件名的批量整理

**主题**: Shell 基础与文件系统
**建议用时**: 12—15 分钟

> 
> 在当前目录新建 `q01`，并完全使用命令行完成下列任务。

**题目要求**

- 创建 `input/docs` 和 `input/tmp`；创建 `input/docs/notes one.txt`（内容为 `alpha` 和 `beta` 两行）、`input/docs/.secret.txt`（内容为 `hidden`）、`input/tmp/empty.txt`（空文件）以及 `input/run.log`（任意两行日志）。
- 显示 `q01` 的绝对路径，并以长格式列出 `input` 下全部项目，包含隐藏文件。
- 把 `input` 下所有 `.txt` 文件复制到 `work/<学号>/`，保留相对目录结构并正确处理名称中的空格。
- 将复制后的目录权限设为 `750`、普通文件权限设为 `640`；生成 `inventory.txt`，列出相对路径和字节数。

---

## 第 2 题 随机访问日志统计

**主题**: Shell 管道与文本处理
**建议用时**: 12—15 分钟

> 
> 在 `q02` 中创建 `access.csv`，并使用下方给定数据完成日志统计。

**access.csv 原始内容**

```
timestamp,user,path,status,latency_ms
09:00:01,alice,/api/users,200,120
09:00:02,bob,/api/orders,500,310
09:00:03,alice,/api/users,503,180
09:00:04,carol,/login,500,90
09:00:05,bob,/api/orders,502,260
09:00:06,dave,/health,200,20
09:00:07,alice,/api/orders,500,420
09:00:08,carol,/api/users,500,150
```

**题目要求**

- 编写 `analyze.sh`，接收一个 CSV 文件路径；文件不存在时将错误写入 `stderr` 并返回非零退出码。
- 使用 Shell 管道以及 `awk`、`sort`、`head` 等工具，输出 HTTP 5xx 数量最多的前 2 个 `path`；按次数降序，次数相同时按 `path` 字典序。
- 输出全部数据行的平均 `latency_ms`，保留两位小数；表头不得计入。
- 分别对 `access.csv` 和一个不存在的文件运行脚本；不得使用 Python、电子表格或手工统计。

---

## 第 3 题 制造、解决并解释一次合并冲突

**主题**: Version Control and Git
**建议用时**: 12—15 分钟

> 
> 在 `q03` 中从零创建一个 Git 仓库，并主动制造、解决一次合并冲突。

**题目要求**

- 初始化仓库，在 `main` 创建 `config.txt`，内容为 `mode=normal`，并完成初始提交。
- 创建 `feature‑a`，把内容改为 `mode=safe` 并提交；从初始 `main` 创建 `feature‑b`，把内容改为 `mode=fast` 并提交。
- 回到 `main`，先合并 `feature‑a`，再合并 `feature‑b`；解决冲突时保留 `mode=safe`，并另加一行 `note=reviewed`。
- 确认工作区干净，运行 `git log --all --graph --decorate --oneline` 查看历史。

---

## 第 4 题 修复并构建一页技术说明

**主题**: LaTeX 文档编辑
**建议用时**: 12—15 分钟

> 
> 将下方模板保存为 `q04/report.tex`，补全内容并从命令行构建 PDF。

**report.tex 初始模板**

```
\documentclass{article}
\usepackage{amsmath}
\begin{document}
\title{Tool Report}
\author{姓名—学号}
\maketitle

\section{Result}
% 在此加入公式、表格及正文引用

\end{document}
```

**题目要求**

- 加入一个带编号和 `label` 的公式，并在正文中使用 `\ref` 或 `\eqref` 引用。
- 加入一个 2 行 2 列表格，设置 `caption` 和 `label`，并在正文中引用该表。
- 使用 `latexmk -pdf -halt-on-error` 或 `tectonic` 生成 `report.pdf`。
- 确认 PDF 能打开，且交叉引用不显示 `??`。

如果你需要，我还可以顺带把**4 道题完整可运行的参考答案脚本**一并给你。
