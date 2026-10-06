---
name: asy
description: "Bilingual (English / Chinese) writing skill. Long paragraphs follow yomiyasu-style natural prose rules; short summaries and non-sentence structures (schema, tables, lists, field names) follow ASD-STE100-style controlled language rules."
---

# Asy — Bilingual Writing Skill

Asy 把两种书写规范组合在一起。输出前先判断每个部分属于哪一层，再套用对应规则：

| 层 | 内容 | 规则 |
|---|---|---|
| Prose | 长段落、解释性正文 | yomiyasu 式自然散文规则 — `references/prose-rules.md` |
| Summary | 短总结、TL;DR、要点、结论、标题 | ASD-STE100 受控语言规则 — `references/ste100-rules.md` |
| Schema | 非句子结构：schema、表格、列表、字段名、枚举值 | ASD-STE100 受控语言规则 — `references/ste100-rules.md` |

写之前先读取对应层的参考文档。

## Step 0: 语言选择（写作前必须先做）

1. 用户已明确指定语言（"用中文写"、"in English"、"English only"）→ 直接使用，跳到 Step 1。
2. 用户未指定语言 → 先弹出选择，再开始写作：

   > 请选择输出语言 / Please choose the output language:
   > 1. English（默认）
   > 2. 中文

   用户未回答时，默认使用 English。
3. 选定的语言应用于所有人可读文本：正文、总结、标题、表格说明。
4. Schema 标识符（键名、字段名、枚举值）无论选定哪种语言，一律使用英文。

## 共享不变量（所有层都适用）

1. **保持含义。** 主张、轻重、断言强度（保留 hedge 的强度）、每句的功用（说明 / 建议 / 规则 / 计划 / 评价）在改写前后必须一致。
2. **不添加。** 不添加源文没有的主体、原因、数值、例子、术语。
3. **不删除。** 不删除条件、范围限定、数值、例外、安全限定。
4. **一句话一个意思，一段话一个话题。**
5. **不修已合规的文本。** 输入已符合对应层规范时直接说明，不强行改写。
6. **消除歧义优先于缩短。** 句子无歧义即停，不追求最短。

## 分层规则（速览）

### Prose — yomiyasu 风格
- 每句有可追溯的主语和谓语；不拟人、无比喻。
- 无自我标注式开头（"重要的是"、"It's important to note that"）、无空预告句。
- 保持文档立场（建议 / 规则 / 说明），不改变句子强度。
- 连接词必须指向可追溯的关系；代词只在指代明确时保留。
- 无 emoji、无装饰性冒号、无 em dash；加粗和列表克制使用。
- 完整规则：`references/prose-rules.md`

### Summary — ASD-STE100 风格
- 主动语态，一句一个意思，≤20 词（EN）/ ≤20 字（ZH）。
- 无分号、无短语动词、无同义词轮换、无 hedge 堆叠、无名词化、无营销形容词。
- 简单时态；保留 hedge，不升级为事实。
- 完整规则：`references/ste100-rules.md`

### Schema — ASD-STE100 风格
- 一个键一个概念，用最平常的词，风格一致。
- 全文一个概念一个术语；无未定义缩写。
- 描述：一句话，≤15 词，不用 hedge（用 required/optional 表达）。
- 枚举值一个值一个含义；表头 ≤3 词名词短语；列表项结构平行。
- 完整规则：`references/ste100-rules.md`

## 输出格式

**默认：只输出最终文本。** 不加前言、不报规则名、不总结改动、不附加收尾询问。

用户要求看推理（"show the diff"、"explain the changes"、"before/after"、"解释改动"）时，改为输出表格：

| Rule violated | Original | Rewritten |
|---|---|---|

对刻意保留的较长表达，追加一行 `Kept as-is:`，说明保留的精确含义。

## 边界

- 不用于创意写作、营销文案、说服性文本。
- Asy 修形式，不修内容。源文没有实质内容时，直接说明，不润色空洞。
- 本 skill 应用 ASD-STE100 的结构纪律，不复制官方约 900 词词典，不宣称词典级合规。

## References

- `references/prose-rules.md` — 长段落自然散文规则（yomiyasu 风格）
- `references/ste100-rules.md` — 总结与非句子结构的受控语言规则（ASD-STE100 风格）
- `references/examples.md` — EN / ZH 三层 before-after 示例
