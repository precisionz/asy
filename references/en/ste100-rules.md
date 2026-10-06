# Controlled Language Rules (ASD-STE100 Style)

Applies to short summaries (TL;DRs, key points, conclusions, and headings) and non-sentence structures (schemas, tables, lists, field names, and enum values).

These rules derive from the structural discipline in ASD-STE100 Issue 9 (January 2025). This document does not reproduce the official dictionary of about 900 words. It applies only the structural rules.

## A. Summary Rules (Short Sentences)

| Rule | Do | Don't |
|---|---|---|
| Voice | "The agent deletes the file." | "The file is deleted." Exception: the actor is unknown or irrelevant. |
| One idea per sentence | "Open the file. Read line 3." | "Open the file and read line 3, then check the match." |
| Length | Use no more than 20 words in English or 20 Chinese characters. | Use compound sentences or multiple subordinate clauses. |
| Punctuation | Separate sentences with periods. | Do not use semicolons. |
| Noun clusters | "fuel pump valve" (3 words) | "high pressure fuel pump inlet valve assembly" (5 words) |
| Complete sentences | Write the subject, verb, and article when needed. | "Files not backed up are lost" when the omission creates ambiguity. |
| Hedges | Keep "may have failed" as "may have failed." | Change it to "failed" and remove the hedge. |
| Phrasal verbs | "Remove the panel. Start the job." | "Take off the panel. Spin up the job." |
| Tense | Use imperative, simple present, simple past, or simple future. | Change "We have received" to "We received." Exception: keep and mark the present perfect when it expresses current relevance that simple tenses cannot express. |
| Synonym consistency | Use one term for one concept, such as "user." | Alternate among "user," "client," and "customer" for the same entity. |
| Stacked hedges | State the condition directly. | "It is important to note that this may potentially help to improve." |
| Nominalization | "Analyze the log." | "Perform an analysis of the log." |
| Marketing adjectives | Give a measurable fact, such as "completes in 200 ms." | Use "seamless," "robust," or "powerful." |
| Paragraphs | Keep one topic and no more than six sentences per paragraph. | Mix several topics in one paragraph. |
| Sequences | Use a numbered list for three or more steps. | Hide the steps inside prose. |
| Headings | Use a short noun phrase that names the topic. Keep a conclusion or warning in the heading when it carries meaning. | Replace a meaningful conclusion with a generic heading such as "Details" or "Overview." |

### Chinese Summary Adaptation

- Use active voice. Put the actor before the action and limit passive constructions.
- Put one idea in each sentence. Use no more than 20 Chinese characters per sentence.
- Do not use semicolons or colloquial verb phrases. Replace expressions such as 搞一下 or 弄一下 with precise verbs such as 处理 or 配置.
- Use one term for one concept. Do not alternate among 用户, 客户端, and 客户 for the same entity.
- Preserve hedges. Do not change 可能失败 to 失败.
- Do not use marketing terms such as 无缝, 强大, 极致, 完美, or 丝滑.
- Use a numbered list for three or more steps.

## B. Schema Rules (Non-Sentence Structures)

Applies to JSON, YAML, and TOML keys; database columns; API fields; table headers; enum values; and list items.

1. **Use one concept per key.** A key must identify exactly one item.
   - Good: `retry_count`, `owner_id`
   - Bad: `user_customer_client` (three concepts), `misc` or `data` (no defined concept)
2. **Use ordinary words.** Do not use phrasal verbs or invent compound words.
   - Good: `start_time`
   - Bad: `kick_off_ts`, `spinup_at`
3. **Use one term for each concept throughout the document.**
   - Good: use `user_id` everywhere.
   - Bad: use `user_id` in one place and `client_id` in another for the same entity.
4. **Do not use undefined abbreviations.** Use an abbreviation only when it is defined or established by the project.
   - Bad: `cfg`, `ctx`, unless the project defines them.
5. **Use a consistent style.** Follow the project's convention. If none exists, use snake_case for keys, lowerCamelCase for code identifiers, and lowercase enum values.
6. **Write concise descriptions for table cells and field comments.**
   - Use one sentence with no more than 15 English words or 20 Chinese characters. Do not use semicolons.
   - Use active voice and simple tenses.
   - Do not use hedges. Express optionality with `required: false` or `nullable: true`, not "may be set."
   - Do not use marketing adjectives.
7. **Give each enum value one meaning.** Use ordinary lowercase words with no spaces.
   - Good: `pending`, `active`, `closed`
   - Bad: `In-Progress!`, `maybe_active`
8. **Keep table headers short.** Use consistent capitalization and noun phrases with no more than three words.
   - Good: `Field`, `Type`, `Required`
   - Bad: "The name of the field that identifies the entity"
9. **Keep list items parallel.** Use the same part of speech and voice within a list.
   - Good: "Read the config. Parse the input. Validate the schema."
   - Bad: "Reading config, to parse the input, validation of schema"
10. **State whether a field is required or optional.** Do not use "may," "sometimes," or "usually" in field descriptions.
11. **Keep domain terms.** Do not rename required domain terms. Define each term once at first use.

## C. Safety and Instructions

- Put safety-critical instructions at the start of a sentence. Do not bury them in a sentence.
- Put one instruction in each sentence.

## D. Boundaries

- This document does not validate compliance with the official dictionary. The dictionary is not distributed here.
- Do not change meaning. If shortening removes precision, such as a safety condition, scope, or number, keep the longer wording and mark it with `Kept as-is:`.

## E. Sources

- Structural rules are summarized from `writing-rules.md` in danyuchn/asd-ste100-skill v0.4.0. They correspond to ASD-STE100 Issue 9 (January 2025).
- Official specification: asd-ste100.org.
