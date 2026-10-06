# Examples（before / after）

三层各给 EN / ZH 示例。规则出处：Prose → `prose-rules.md`；Summary / Schema → `ste100-rules.md`。

## 1. Prose（yomiyasu 风格）

### EN

**Before**

> The biggest pitfall of async processing is network blips. Dependency graphs are not splittable — you can't roll back while running. Simply firing messages is not enough, because the data quietly rots behind the scenes. That's where the three principles below really quietly kick in:
> - **Ensuring idempotency**: duplicate processing is silently skipped.
> - **Safe retry**: exponential backoff lets the DB load escape.
> - **DLQ escape**: broken messages are isolated, and the cause is crushed one by one.
> Don't waste a whole day debugging — design with this boundary in mind!

**After**

> In an async message pipeline, a dropped connection or a server restart can interrupt processing mid-message. A duplicate delivery must not corrupt state, so the receiver records each message ID and skips an ID it has already processed.
>
> When a call to an external API fails, the pipeline retries with a growing delay. A message that fails past the retry limit moves to a dead-letter queue for manual inspection. A documented recovery procedure shortens the time to find the cause when a failure occurs.

**Changes**

| Rule | Fix |
|---|---|
| 比喻 | "quietly rots"、"crushed"、"waste a day" → 直接陈述 |
| 拟人 | "lets the DB load escape" → 删 |
| em dash | 拆成两句 |
| 空预告 + 加粗列表 | 原则直接写入正文，删列表 |
| 收尾号召 | "Don't waste ...!" → 删 |
| 一段多话题 | 拆成两段，各一个话题 |

### ZH

**Before**

> 异步处理**最大的坑**是网络瞬断。依赖结构不可拆分，**边跑边回滚是不可能的**。光发消息不够，数据会在背后**悄悄腐坏**。下面三个原则会**默默生效**：
> - **幂等性**：重复消息**默默跳过**；
> - **安全重试**：指数退避让 DB **喘口气**；
> - **DLQ**：坏消息隔离后逐个**锤掉**。
> 别在调试上**烧一整天**，设计时守住这条线！

**After**

> 异步消息处理中，连接中断或服务器重启可能中断处理。重复投递不能破坏状态，因此接收方记录每条消息的 ID，已处理过的 ID 直接跳过。
>
> 调用外部接口失败时，按递增的间隔重试。超过重试上限的消息进入死信队列，人工排查。预先写好恢复步骤，可以缩短故障后的定位时间。

**Changes**

| Rule | Fix |
|---|---|
| 比喻 | "悄悄腐坏"、"锤掉"、"烧一整天"、"喘口气" → 直接陈述 |
| 黑话 | "最大的坑" → 删 |
| em dash | 拆成两句 |
| 加粗列表 + 空预告 | 删列表，内容并入正文 |
| 收尾号召 | "守住这条线！" → 删 |
| 一段多话题 | 拆成两段 |

## 2. Summary（ASD-STE100 风格）

### EN

**Before**

> This tool will attempt to synchronize state across the various backends that have been configured, and if a conflict is detected it may resolve it automatically depending on the strategy that has been set, or otherwise it will surface the conflict for manual review.

**After**

> The tool syncs state across the configured backends. If it finds a conflict, it reads the configured strategy. If the strategy allows automatic resolution, the tool resolves the conflict. If it does not resolve the conflict, it reports the conflict for manual review.

**Changes**

| Rule violated | Fix |
|---|---|
| One idea per sentence | 4 个意思拆成 4 句 |
| Passive voice | "a conflict is detected" → "it finds a conflict" |
| Present perfect | "that have been configured" → "configured"（形容词） |
| Phrasal verb | "surface the conflict" → "reports the conflict" |
| Length | 33 词 → 4 句，每句 ≤20 词 |
| Hedge | "may" → 保留（"allows automatic resolution" 保留条件性） |

### ZH

**Before**

> 该工具会尝试同步各后端的状态，若检测到冲突，可能按已配置的策略自动解决，否则把冲突暴露出来供人工复核。

**After**

> 工具同步各后端的状态。发现冲突时，工具读取已配置的策略。策略允许自动解决时，工具解决冲突。否则，工具报告冲突，交人工复核。

**Changes**

| Rule violated | Fix |
|---|---|
| 一句一意 | 4 个意思拆成 4 句 |
| 长度 | 50+ 字 → 4 句，每句 ≤20 字 |
| 短语动词 | "暴露出来" → "报告" |
| Hedge | "可能" → 用"策略允许"保留条件性 |

## 3. Schema（ASD-STE100 风格）

### EN

**Before**

```yaml
user_info:            # user or client?
  full_name: string   # required?
  last_login_at: datetime  # might be null?
  status: "In-Progress!" | inactive | closed
  retry_backoff_cfg: map   # misc settings
```

**After**

```yaml
user:
  full_name: string       # The user's full name. Required.
  last_login: datetime    # Last login time. Optional.
  status: pending | active | closed
  retry_backoff: object   # Retry interval settings.
```

**Changes**

| Rule violated | Fix |
|---|---|
| One term per concept | `user_info` 与全文 `user` 不一致 → 统一 `user` |
| Hedge in description | "might be null?" → `Optional` |
| One meaning per enum | "In-Progress!" → `active`（值含义与 `pending` 区分开） |
| Undefined abbreviation | `cfg` → `retry_backoff` |
| Description length | 注释多从句 → 一句话 ≤15 词 |

### ZH 文档（正文中文，schema 标识符保持英文）

**After**

```
用户字段：

| 字段 | 类型 | 必填 | 说明 |
|---|---|---|---|
| `full_name` | string | 是 | 用户的全名 |
| `last_login` | datetime | 否 | 最近一次登录时间 |
| `status` | enum | 是 | 用户状态。取值：pending、active、closed |
| `retry_backoff` | object | 否 | 重试间隔设置 |
```

注意：键名保持英文；表头 ≤3 词；说明一句话说完，hedge 移到"必填"列。
