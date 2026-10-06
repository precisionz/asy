# Controlled Language Rules（ASD-STE100 风格）

适用：短总结（TL;DR、要点、结论、标题）与非句子结构（schema、表格、列表、字段名、枚举值）。
规则派生自 ASD-STE100 Issue 9（2025-01）的结构纪律。本文件不复制官方约 900 词词典，只应用其结构规则。

## A. 总结规则（短句子）

| 规则 | Do | Don't |
|---|---|---|
| 语态 | "The agent deletes the file." | "The file is deleted."（施事者未知或不相关时除外） |
| 一句一意 | "Open the file. Read line 3." | "Open the file and read line 3, then check the match." |
| 长度 | ≤20 词（EN）；≤20 字（ZH） | 复合句、多层从句 |
| 标点 | 句号分隔 | 分号（禁用） |
| 名词簇 | "fuel pump valve"（3 词） | "high pressure fuel pump inlet valve assembly"（5 词） |
| 省略 | 主语、动词、冠词写全 | "Files not backed up are lost"（省略造成歧义） |
| Hedge | "may have failed" 保持 "may have failed" | "failed"（丢了 hedge，主张变了） |
| 短语动词 | "Remove the panel. Start the job." | "Take off the panel. Spin up the job." |
| 时态 | 祈使、一般现在/过去/将来 | 现在完成 "We have received" → "We received"。例外：现在完成承载现在时无法表达的当前相关性时保留并标注 |
| 同义词轮换 | 一个概念一个名字（"user"，不混 "user/client/customer"） | 同一对象多个名字轮换 |
| Hedge 堆叠 | 直接陈述 | "It is important to note that this may potentially help to improve" |
| 名词化 | "Analyze the log." | "Perform an analysis of the log." |
| 营销形容词 | "completes in 200 ms"（用数字） | "seamless"、"robust"、"powerful" |
| 段落 | 一个话题，≤6 句 | 多话题段落 |
| 序列 | 3 步以上用编号列表 | 步骤埋进一句散文 |
| 标题 | 短名词短语，命名本节话题；承载结论或警告时保留结论 | 把有结论的标题削成通用标题（"说明"、"概述"） |

### ZH 总结适配

- 主动语态：主语直接动作，少用"被"。
- 一句一意，≤20 字。
- 无分号；无口语短语动词（"搞一下"、"弄一下" → "处理"、"配置"）。
- 一个概念一个术语：不混"用户/客户端/客户"。
- 保留 hedge："可能失败"不写成"失败"。
- 无营销词：无缝、强大、极致、完美、丝滑。
- 3 步以上 → 编号列表。

## B. Schema 规则（非句子结构）

适用：JSON / YAML / TOML 键、数据库列、API 字段、表头、枚举值、列表项。

1. **一个键一个概念。** 键名恰好对应一件事。
   - Good: `retry_count`、`owner_id`
   - Bad: `user_customer_client`（三个概念）、`misc` / `data`（没有概念）
2. **用最平常的词。** 不用短语动词、不生造复合词。
   - Good: `start_time`
   - Bad: `kick_off_ts`、`spinup_at`
3. **全文一个概念一个术语。** 选定后全文一致。
   - Good: 处处 `user_id`
   - Bad: 这里 `user_id`、那里 `client_id`
4. **无未定义缩写。** 已定义或项目既有术语可用；否则写全词。
   - Bad: `cfg`、`ctx`（项目术语除外）
5. **风格一致。** 跟随项目既有约定；无约定时：键用 snake_case，代码标识符用 lowerCamelCase，枚举值用小写。
6. **描述（表格单元格、字段注释）：**
   - ≤15 词（EN）/ ≤20 字（ZH），一句话，无分号。
   - 主动语态、简单时态。
   - 不用 hedge：用 `required: false` / `nullable: true` 表达，不写 "may be set"。
   - 无营销形容词。
7. **枚举值：** 一个值一个含义；平常词、小写、无空格。
   - Good: `pending`、`active`、`closed`
   - Bad: `In-Progress!`、`maybe_active`
8. **表头：** ≤3 词名词短语，大小写一致。
   - Good: `Field`、`Type`、`Required`
   - Bad: "The name of the field that identifies the entity"
9. **列表项：** 结构平行——同一列表内同一词性、同一语态。
   - Good: "Read the config. Parse the input. Validate the schema."
   - Bad: "Reading config, to parse the input, validation of schema"
10. **必填/可选显式化。** 字段描述不出现 "may"、"sometimes"、"usually"。
11. **领域术语保留。** 必须保留的领域术语不改名；首次出现处加一行释义，后文不再解释。

## C. 安全与指令

- 安全关键指令放在句首，不埋在句中。
- 一条指令一句。

## D. 边界

- 不验证官方词典合规（词典不分发）。
- 不改变含义。缩短会丢掉精度（安全条件、范围限定、数值）时，保留较长表达，用 `Kept as-is:` 标注。

## E. 来源

- 结构规则摘要自 danyuchn/asd-ste100-skill（v0.4.0，`references/writing-rules.md`），对应 ASD-STE100 Issue 9（2025-01）。
- 官方规范：asd-ste100.org。
