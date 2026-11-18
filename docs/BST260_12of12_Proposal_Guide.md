# BST260 Final Project — 12/12: Proposal 准备与提交指南

> **截止日期：2026 年 11 月 18 日（周三）**\
> **当前状态：待确认研究主题；本步骤尚未完成。**\
> GitHub Repository：<https://github.com/AiiiiDannn/finalproject>\
> 项目网站：<https://AiiiiDannn.github.io/finalproject/>

## 目标

为 BST260 Final Project
准备并提交一份研究计划（Proposal），说明将如何基于 **两个不同的数据集**
进行公共卫生数据分析。最终项目需要提供有效的 R Package、公开的 `pkgdown`
网站，以及至少两篇分析 Vignettes。

## 1. 先确定两个分析主题（暂不必立即完成）

每个分析至少确定以下内容：

- **Dataset / Data
  source**：数据集名称及来源；来自课堂，或使用经教师批准的新数据。
- **Research question**：一句话说清 Exposure（暴露）与
  Outcome（结局）的关系。
- **Unit of analysis &
  Population**：例如个人、州-年份、疾病暴发事件；研究人群/范围。
- **Exposure**：变量定义及编码方式。
- **Outcome**：变量定义及类型（continuous / categorical）。
- **Confounders**：基于领域知识预先提出需要控制的混杂变量。
- **Missing data**：如何识别和处理缺失。
- **Planned methods**：描述性统计、可视化和拟采用的分析方法。
- **Limitations**：数据和研究设计可能有哪些限制。

### 可考虑的数据集（教授列举）

| 数据集 | 可探索方向 | 提醒 |
|----|----|----|
| NHANES / NHANESraw | BMI、睡眠、血压、健康行为 | 注意抽样设计、缺失数据及潜在混杂 |
| CDC Homicide (`cdcmurd`) | 州与年份间的凶杀死亡率变化 | 单位可能是州-年份，避免把相关误写成因果 |
| CDC Firearm Mortality (`cdcfiremort`) | 枪支相关死亡率的时空模式 | 可与其他数据联合探索，但两个 Vignettes 仍需满足不同数据集要求 |
| RAND Gun Legislation (`gunleg`) | 法律政策变化 | 政策效果推断需要谨慎 |
| CDC Waterborne Illness (`waterborne`) | 暴发事件的地区、时间及类别 | 可能涉及数据清洗和整理 |
| CDC 2025 Births | 孕期健康与出生结局 | 教授注明这是偏高级的数据工程项目 |

**待决定：**

Analysis 1 数据集：\_\_\_\_\_\_\_\_\_\_

Analysis 1 研究问题：\_\_\_\_\_\_\_\_\_\_

Analysis 2 数据集：\_\_\_\_\_\_\_\_\_\_

Analysis 2 研究问题：\_\_\_\_\_\_\_\_\_\_

确认两个分析使用 **不同的数据集**

## 2. 在 RStudio 创建 Proposal 文件

1.  打开本地 RStudio 项目 `finalproject`。
2.  选择 **File → New File → Quarto Document**，或创建纯文本文件。
3.  保存为 **`vignettes/proposal.qmd`**。
4.  使用下方模板填写内容，并将所有 `[占位内容]` 改为实际计划。

> **文件命名提醒：** 教授主要说明（Instructions）明确写的是
> `vignettes/proposal.qmd`；补充建议页（Stubs）另提到了
> `project_plan.qmd`。优先遵循有截止日期的正式 Instructions：创建
> `proposal.qmd`；提交前再核对教师是否需要额外的
> `project_plan.qmd`。这两个名称不是可以无条件互换的。

## 3. 可复制的 `proposal.qmd` 模板

将下方整个代码块复制到 `vignettes/proposal.qmd`：

``` markdown
---
title: "BST260 Final Project Proposal"
author: "Aiden Hai"
format: html
---

**To:** BST260 Teaching Team, Fall 2026

# Project Overview

[Briefly explain the overall objective and why the two analyses matter.]

# Analysis 1 — [Dataset Name]

## Research Question

[Write one sentence naming the exposure and outcome.]

## Dataset and Population

- **Data source:** [Source and provenance]
- **Unit of analysis:** [e.g., individuals or state-years]
- **Target population:** [Who/what the dataset covers]

## Variables

- **Exposure:** [Definition and coding]
- **Outcome:** [Definition; continuous or categorical]
- **Potential confounders:** [Chosen based on subject-matter reasoning]
- **Missing data:** [Expected missingness and proposed handling]

## Planned Methods

- **Descriptive statistics:** [Summaries, tables]
- **Visualizations:** [Plots]
- **Statistical analysis:** [Proposed model or comparison]

# Analysis 2 — [Different Dataset Name]

## Research Question

[Write one sentence naming the exposure and outcome.]

## Dataset and Population

- **Data source:** [Source and provenance]
- **Unit of analysis:** [Unit]
- **Target population:** [Population]

## Variables

- **Exposure:** [Definition and coding]
- **Outcome:** [Definition; continuous or categorical]
- **Potential confounders:** [Chosen before examining the findings]
- **Missing data:** [Proposed handling]

## Planned Methods

- **Descriptive statistics:** [Summaries, tables]
- **Visualizations:** [Plots]
- **Statistical analysis:** [Proposed model or comparison]

# Expected Findings and Limitations

[Explain what the analyses may clarify, key uncertainties, limitations,
and why the planned approach is feasible.]
```

## 4. 本地检查、生成网站并上传 GitHub

完成内容后，在 RStudio 的 **Console** 中运行：

``` r

getwd()                       # 应以 /finalproject 结尾
file.exists("vignettes/proposal.qmd")
pkgdown::build_site()
file.exists("docs/index.html")
```

当 `build_site()` 成功后，在 RStudio **Terminal** 中运行：

``` bash
git status
git add -A
git commit -m "Add BST260 project proposal"
git push origin main
```

> 如果 `git status`
> 显示没有任何修改，不要强行创建空提交；先确认文件是否保存。不要使用
> `git push --force`。

然后检查：

- GitHub
  文件：<https://github.com/AiiiiDannn/finalproject/tree/main/vignettes>
- 网站主页：<https://AiiiiDannn.github.io/finalproject/>
- 网站 Articles 菜单是否出现 Proposal（构建、推送与 Pages 部署后）。

## 5. 提交前核对清单

`vignettes/proposal.qmd` 已保存

计划中有 **两个不同数据集**

两个研究问题均明确 Exposure 与 Outcome

明确单位、研究人群、变量类型及编码方法

列出有理由支持的 Confounders 和 Missing Data 处理计划

说明数据来源、统计描述、可视化和分析方法

说明预期贡献、风险和限制

收件对象写为 `BST260 Teaching Team, Fall 2026`

[`pkgdown::build_site()`](https://pkgdown.r-lib.org/reference/build_site.html)
成功

已 Commit + Push 到 GitHub

已在 GitHub / 网站检查生成结果

已再次核对 `proposal.qmd` 与 `project_plan.qmd` 的教师要求

## 官方参考

- [BST260 Project
  Instructions](https://vjcitn.github.io/bst260project-template/articles/instructions.html)
- [BST260 Project Stubs / Suggested
  Approaches](https://vjcitn.github.io/bst260project-template/articles/stubs.html)
- [教授模板仓库](https://github.com/vjcitn/bst260project-template)

------------------------------------------------------------------------

**后续继续时：**
先选定两个数据集与研究问题，再把上面的模板改成可提交的正式
Proposal；不需要从 GitHub / RStudio 基础设置重新开始。
