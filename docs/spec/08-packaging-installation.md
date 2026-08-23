# L6：仓库、打包、兼容与安装规范

## 1. 仓库身份

- PKG-001 MUST：仓库名称为 `DaXueShenMai`。
- PKG-002 MUST：GitHub 地址为 `https://github.com/Lyn-77/DaXueShenMai`。
- PKG-003 MUST：本地 `origin` 的 fetch 与 push 均指向该仓库。
- PKG-004 MUST：仓库使用 MIT License。
- PKG-005 MUST：未经用户明确要求，不自动推送 GitHub。
- PKG-006 MUST：根 `.gitignore` 忽略 `.obsidian/`，该目录不得进入版本控制。

## 2. 目标目录结构

```text
DaXueShenMai/
├── .gitignore
├── AGENTS.md
├── README.md
├── LICENSE
├── docs/
│   ├── SPEC.md
│   ├── project/
│   │   ├── lessons.md
│   │   └── progress.md
│   └── spec/
├── skills/
│   ├── dxsm-math/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── dxsm-english/        # 后续版本
│   └── dxsm-408/            # 后续版本
└── evals/
    └── dxsm-math/
```

- PKG-010 MUST：v1 只创建 `skills/dxsm-math/`。
- PKG-011 MUST NOT：为尚未设计的英语和 408 Skill 生成虚假实现。
- PKG-012 MUST：Skill 目录名与 `SKILL.md` 的 `name` 均为 `dxsm-math`。

## 3. Skill 包内容

Skill 包必须保持最小且可移植：

```text
skills/dxsm-math/
├── SKILL.md
└── references/
    ├── syllabus-scope.md
    ├── topic-taxonomy.md
    └── reliability-rules.md
```

- PKG-020 MUST：`SKILL.md` 包含触发描述和每次激活都需要的核心流程。
- PKG-021 MUST：详细考纲、题型分类和可靠性细节按需放入 `references/`。
- PKG-022 MUST：所有引用使用相对 Skill 根目录的一层路径。
- PKG-023 MUST NOT：Skill 目录内放 README。
- PKG-024 MUST NOT：Skill 依赖仓库外绝对路径才能运行。
- PKG-025 MUST NOT：打包真题 PDF、大纲扫描件或第三方整本资料。
- PKG-026 SHOULD：`SKILL.md` 控制在 500 行和 5000 tokens 建议范围内。

## 4. Agent Skills 兼容

- COMP-001 MUST：遵循开放 Agent Skills 的 `SKILL.md` 规范。
- COMP-002 MUST：frontmatter 至少包含合法的 `name` 和明确的 `description`。
- COMP-003 MUST：`name` 只使用小写字母、数字和连字符，不含连续连字符。
- COMP-004 MUST：`description` 同时描述能力和触发时机，并包含负向边界。
- COMP-005 MUST：兼容目标是格式级兼容，不承诺所有 Agent 的模型行为完全一致。
- COMP-006 MUST：不使用客户端专有字段作为核心运行前提。
- COMP-007 MAY：使用规范允许的 `license`、`compatibility` 和 `metadata` 字段。

## 5. 根 README 职责

README 必须使用中文，且只存在于仓库根目录。

最小栏目：

1. 项目定位；
2. “大雪深埋”命名说明；
3. 三个独立 Skill 的规划和当前状态；
4. `dxsm-math` 能力与边界；
5. 零 API Key、零强制依赖说明；
6. 人类手动安装；
7. 把网址交给 Agent 安装；
8. 验证安装；
9. MIT License。

- DOC-001 MUST：README 越简洁越好，但安装步骤不能缺失。
- DOC-002 MUST：README 中不得声称尚未实现的英语或 408 Skill 已可用。
- DOC-003 MUST：README 不复制完整规范，只链接 `docs/SPEC.md`。

## 6. 人类手动安装

README 必须提供通用 Agent Skills 目录 `~/.agents/skills/`，不列 Codex、Claude Code 等客户端专用目录。

规范流程：

1. 克隆仓库：

```bash
git clone https://github.com/Lyn-77/DaXueShenMai.git
```

2. 创建通用目录：

```bash
mkdir -p ~/.agents/skills
```

3. 复制 Skill：

```bash
cp -R DaXueShenMai/skills/dxsm-math ~/.agents/skills/dxsm-math
```

4. 重新开始一个 Agent 会话或让客户端刷新 Skills。

5. 验证：

```text
请解答这道考研数学题：lim_{x→0} sin(x)/x
```

- INS-H-001 MUST：安装说明不得要求 API Key。
- INS-H-002 MUST：不得要求用户复制整个 981 MB 本地题库。
- INS-H-003 MUST：目标目录已存在时提醒用户先自行备份或确认覆盖，文档不得直接使用破坏性覆盖命令。

## 7. 把网址交给 Agent 安装

README 必须提供可复制提示词：

```text
请从 https://github.com/Lyn-77/DaXueShenMai 安装 skills/dxsm-math，
使用通用 Agent Skills 目录 ~/.agents/skills/。
不要安装其他 Skill，不要配置 API Key。
```

- INS-A-001 MUST：提示词包含仓库 URL、Skill 子路径和通用目标目录。
- INS-A-002 MUST：提示词明确只安装 `dxsm-math`。
- INS-A-003 MUST：执行安装的 Agent 应先检查目标是否已存在。
- INS-A-004 MUST：仓库本身不执行自动安装。

## 8. 依赖说明

- DEP-001 MUST：README 声明无强制第三方依赖。
- DEP-002 MUST：Python、SymPy、Matplotlib 只作为 Agent 环境可选增强。
- DEP-003 MUST：缺少可选工具不会阻止 Skill 基础解题。
- DEP-004 MUST：Skill 不自动安装可选工具。
- DEP-005 MUST：Skill 不使用 API Key 或独立云端调用。

## 9. 测试资产位置

- PKG-T-001 MUST：公开合成测试位于仓库 `evals/dxsm-math/`。
- PKG-T-002 MUST：本地真题索引可保存，但不得包含完整题目与答案解析。
- PKG-T-003 MUST：本地 PDF 路径只能作为维护者本地配置，不能成为安装者运行 Skill 的前提。

## 10. 交付边界

- RELS-001 MUST：实现完成后只保存在仓库工作区。
- RELS-002 MUST NOT：自动复制到 `~/.agents/skills/` 或其他用户目录。
- RELS-003 MUST NOT：自动提交或推送 GitHub。
- RELS-004 MUST：交付说明列出已创建文件、校验结果、测试结果和已知非阻断问题。
