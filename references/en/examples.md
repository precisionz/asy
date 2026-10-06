# Examples (Before and After)

This file shows English examples for all three layers. See `prose-rules.md` for prose rules and `ste100-rules.md` for summary and schema rules.

## 1. Prose (Yomiyasu Style)

**Before**

> The biggest pitfall of async processing is network blips. Dependency graphs are not splittable - you can't roll back while running. Simply firing messages is not enough, because the data quietly rots behind the scenes. That's where the three principles below really quietly kick in:
> - **Ensuring idempotency**: duplicate processing is silently skipped.
> - **Safe retry**: exponential backoff lets the DB load escape.
> - **DLQ escape**: broken messages are isolated, and the cause is crushed one by one.
> Don't waste a whole day debugging - design with this boundary in mind!

**After**

> In an async message pipeline, a dropped connection or a server restart can interrupt processing mid-message. A duplicate delivery must not corrupt state, so the receiver records each message ID and skips an ID it has already processed.
>
> When a call to an external API fails, the pipeline retries with a growing delay. A message that fails past the retry limit moves to a dead-letter queue for manual inspection. A documented recovery procedure shortens the time to find the cause when a failure occurs.

**Changes**

| Rule | Fix |
|---|---|
| Metaphors | Replace "quietly rots," "crushed," and "waste a day" with direct statements. |
| Personification | Remove "lets the DB load escape." |
| Long dash | Use a hyphen (-) or split the sentence. |
| Empty preview and bold list | Move the principles into the prose and remove the list. |
| Call to action | Remove "Don't waste ...!" |
| Multiple topics in one paragraph | Split the paragraph into two topic-focused paragraphs. |

## 2. Summary (ASD-STE100 Style)

**Before**

> This tool will attempt to synchronize state across the various backends that have been configured, and if a conflict is detected it may resolve it automatically depending on the strategy that has been set, or otherwise it will surface the conflict for manual review.

**After**

> The tool syncs state across the configured backends. If it finds a conflict, it reads the configured strategy. If the strategy allows automatic resolution, the tool resolves the conflict. If it does not resolve the conflict, it reports the conflict for manual review.

**Changes**

| Rule violated | Fix |
|---|---|
| One idea per sentence | Split four ideas into four sentences. |
| Passive voice | Change "a conflict is detected" to "it finds a conflict." |
| Present perfect | Change "that have been configured" to "configured." |
| Phrasal verb | Change "surface the conflict" to "reports the conflict." |
| Length | Replace 33 words with four sentences of no more than 20 words each. |
| Hedge | Preserve the condition with "If the strategy allows automatic resolution." |

## 3. Schema (ASD-STE100 Style)

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
| One term per concept | Use `user` consistently instead of `user_info`. |
| Hedge in description | Replace "might be null?" with `Optional`. |
| One meaning per enum | Replace `"In-Progress!"` with `active` to distinguish it from `pending`. |
| Undefined abbreviation | Replace `cfg` with `retry_backoff`. |
| Description length | Use one sentence of no more than 15 words in each comment. |
