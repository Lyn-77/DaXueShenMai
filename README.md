# 大雪深埋（DaXueShenMai）

面向中国考研学习场景的 Agent Skills 仓库。“大雪深埋”使用统一前缀 `dxsm-`；规划中的三个独立 Skill 为数学、英语与 408，当前 v1 仅提供 `dxsm-math`。

## dxsm-math

`dxsm-math` 用于考研数学题的识别、分析、求解、理解型讲解，以及用户作答检查与纠错。它覆盖数学一、数学二、数学三官方范围的并集。

它不会处理学习规划、估分、阅卷得分点或明显超出统考考研数学范围的题目；不使用 API Key，也没有强制第三方依赖。Agent 可以在本机已经具备 Python、SymPy 或 Matplotlib 时将其用于复核和绘图，但 Skill 不会自动安装工具。

完整产品规范见 [docs/SPEC.md](docs/SPEC.md)。

## 手动安装

```bash
git clone https://github.com/Lyn-77/DaXueShenMai.git
mkdir -p ~/.agents/skills
cp -R DaXueShenMai/skills/dxsm-math ~/.agents/skills/dxsm-math
```

如果 `~/.agents/skills/dxsm-math` 已存在，请先自行备份，或确认要怎样处理旧版本，再执行复制。复制后重新开始 Agent 会话，或让客户端刷新 Skills。

## 交给 Agent 安装

把下面的提示词交给能够安装 Agent Skills 的 Agent：

```text
请从 https://github.com/Lyn-77/DaXueShenMai 安装 skills/dxsm-math，
使用通用 Agent Skills 目录 ~/.agents/skills/。
安装前先检查目标目录是否已存在；不要安装其他 Skill，不要配置 API Key。
```

仓库本身不会自动安装 Skill。

## 验证安装

开始一个新会话并输入：

```text
请解答这道考研数学题：lim_{x→0} sin(x)/x
```

若回答先复述题目，再给出题型定位、关键线索、推导与明确的最终答案，即可确认 Skill 已被发现并按核心流程工作。不同 Agent 客户端的实际行为可能存在差异；本项目承诺的是开放 Agent Skills 格式兼容。

## 许可证

[MIT License](LICENSE)
