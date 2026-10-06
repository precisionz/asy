# Asy — Bilingual Writing Skill

Asy 是双语技术写作 skill：长段落遵循 yomiyasu 式自然散文规则；短总结与非句子结构（schema、表格、列表）遵循 ASD-STE100 受控语言规则。支持中文 / 英文输出（未指定语言时会弹出选择，默认英文）。

## 结构

| 文件 | 作用 |
|---|---|
| `SKILL.md` | skill 入口：三层分工（Prose / Summary / Schema）、语言选择、共享不变量、输出格式 |
| `references/prose-rules.md` | Prose 层规则（yomiyasu 式自然散文） |
| `references/ste100-rules.md` | Summary / Schema 层规则（ASD-STE100 式受控语言） |
| `references/examples.md` | EN / ZH 三层 before-after 示例 |

## 安装

本仓库即 skill 文件夹本身。克隆或复制到任一 skills 目录，文件夹名为 `asy`：

| 环境 | 安装位置 |
|---|---|
| Zed（全局） | `~/.agents/skills/asy/` |
| Zed / Claude Code（项目级） | `<project>/.agents/skills/asy/` |
| Claude Code（全局） | `~/.claude/skills/asy/` |

```bash
# bash：安装到 Zed 全局目录
git clone https://github.com/precisionz/asy ~/.agents/skills/asy
```

## 使用

对 agent 说"按 Asy 规范写 / write in Asy style"，或直接描述写作任务即可触发。未指定输出语言时会先询问：

```
请选择输出语言 / Please choose the output language:
1. English（默认）
2. 中文
```

## 来源

- Prose 层规则改编自 [nanaism/yomiyasu](https://github.com/nanaism/yomiyasu)（MIT）。
- Summary / Schema 层规则派生自 ASD-STE100 Issue 9（2025-01）结构规则，经 [danyuchn/asd-ste100-skill](https://github.com/danyuchn/asd-ste100-skill)（MIT）摘要；官方站点：[asd-ste100.org](https://asd-ste100.org)。官方词典不分发。
