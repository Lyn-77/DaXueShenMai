# dxsm-math v1 规范总索引

- 状态：需求冻结，`dxsm-math` v1.0.0 本地实现与验收完成
- 规范版本：1.0
- 最后更新：2026-08-29
- 适用仓库：`https://github.com/Lyn-77/DaXueShenMai`

## 1. 文档目的

本规范将需求访谈中已经确认的决定转化为可实现、可测试、可追踪的约束。它是 `dxsm-math` v1 的产品、运行时、可靠性、输出、测试与交付依据。

任何实现、测试或文档若与本规范冲突，必须先解决冲突，不能自行选择一个版本继续。

`AGENTS.md` 是同等生效的仓库执行规范，负责规定 Agent 的开工、修改、验证、纠错和交付方式；本文件及分层规范负责规定产品行为与验收要求。两者分工互补，均不得被排除在规范来源之外。

## 2. 阅读顺序

1. [治理与总则](spec/00-governance.md)
2. [产品范围、触发与输入](spec/01-scope-trigger-input.md)
3. [运行时职责与状态机](spec/02-runtime-responsibilities.md)
4. [解题、教学与纠错流程](spec/03-solving-teaching-correction.md)
5. [输出与排版契约](spec/04-output-contract.md)
6. [可靠性、工具与图示](spec/05-reliability-tools-visuals.md)
7. [考纲与知识边界](spec/06-syllabus-boundary.md)
8. [测试与验收](spec/07-testing-acceptance.md)
9. [仓库、兼容与安装](spec/08-packaging-installation.md)
10. [需求追踪矩阵](spec/09-traceability.md)
11. [压缩上下文胶囊](spec/99-context-capsule.md)

## 3. 规范层级

| 层级 | 解决的问题 | 文档 |
|---|---|---|
| L0 治理层 | 为什么做、优先级、术语和不可破坏原则 | 00 |
| L1 产品契约层 | 何时触发、处理什么、拒绝什么 | 01 |
| L2 运行职责层 | 各职责单元输入、输出、失败处理 | 02 |
| L3 教学执行层 | 怎样分析、求解、纠错与续题 | 03 |
| L4 表达契约层 | 用户最终看到什么以及怎样排版 | 04 |
| L5 可靠性层 | 如何避免无依据生成、如何使用工具 | 05、06 |
| L6 验证交付层 | 怎样测试、何时允许交付、怎样安装 | 07、08 |
| L7 追踪与续作层 | 每条需求落在哪里、如何恢复上下文 | 09、99 |

## 4. 变更规则

- 已编号的 MUST 要求不得由实现者静默修改。
- 新需求必须先判断是否与现有要求冲突，再分配唯一编号。
- 冲突要求必须由用户裁决；裁决前保持待确认，不得实现。
- 用户纠正、可靠性事故和测试暴露的问题必须进入 `docs/project/lessons.md`。
- 任务进度必须遵循 `AGENTS.md` 第 4.6 节的检查点协议：每完成一个可验证步骤就立即同步到 `docs/project/progress.md`，不得只在阶段结束时补记。
- 可控或可预见的上下文压缩前，必须先同步 `docs/project/progress.md` 与 `docs/spec/99-context-capsule.md`，复读确认并核对工作区后才能压缩。

## 5. 当前实施门

用户已于 2026-08-25 明确批准开工，实施门已经打开。`skills/dxsm-math/`、README、LICENSE 和测试资产已经创建，结构、合成行为、36 道固定回归与 12 道未见题验收均已通过。用户已人工审核并批准删除“验证”板块后的 `v1.0.1` Release Notes，现已授权自动完成提交、push、tag 与 GitHub Release；英语或 408 Skill 的实现及自动安装仍未获授权。
