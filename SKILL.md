---
name: asy
description: Functional document writing skill for prose, summaries, and schemas.
---

# Asy: Functional Document Writing Skill

Asy combines two writing standards. Classify each part of the output before writing, then apply the matching rules.

| Layer | Content | Standard |
|---|---|---|
| Prose | Long paragraphs and explanatory text | Natural prose rules in `references/{language}/prose-rules.md` |
| Summary | Short summaries, TL;DRs, key points, conclusions, and headings | Controlled language rules in `references/{language}/ste100-rules.md` |
| Schema | Non-sentence structures, including schemas, tables, lists, field names, and enum values | Controlled language rules in `references/{language}/ste100-rules.md` |

Use `en` for English and `zh` for Chinese in reference paths.

## Step 0: Select the Output Language

1. Before writing, always ask the user to choose `en` (English) or `zh` (Chinese).
2. Ask even when the user has already specified a language. Do not treat a language in the request as the required selection.
3. Do not start writing until the user selects `en` or `zh`. Do not use a default language.
4. Apply the selected language to all reader-facing text, including prose, summaries, headings, and table descriptions.
5. Keep schema identifiers, such as keys, field names, and enum values, in English regardless of the selected language.

Use this prompt:

```text
Choose the output language:
1. English (en)
2. Chinese (zh)
```

## Step 1: Read the Matching References

Use only the reference set for the selected output language:

- Read `references/{language}/examples.md` for examples in the selected language.
- For prose, read `references/{language}/prose-rules.md`.
- For summaries or schemas, read `references/{language}/ste100-rules.md`.

Do not use examples from the other language directory as the output pattern.

## Shared Invariants

Apply these rules to every layer:

1. **Preserve meaning.** Keep the claim, emphasis, certainty, and sentence function unchanged. Preserve the strength of each hedge.
2. **Do not add information.** Do not add an actor, cause, number, example, or term that is absent from the source.
3. **Do not remove information.** Keep conditions, scope, numbers, exceptions, and safety qualifications.
4. **Use one idea per sentence and one topic per paragraph.**
5. **Do not edit compliant text.** If the input follows the rules for its layer, say so without rewriting it.
6. **Resolve ambiguity before shortening.** Stop when the sentence is clear. Do not shorten it for its own sake.

## Layer Rules

### Prose: Yomiyasu Style

- Give each sentence a traceable subject and predicate. Avoid personification and metaphors.
- Remove empty previews and openings that only label the text, such as "It's important to note that."
- Preserve the document's stance: recommendation, rule, or description. Do not change sentence strength.
- Use connectors only for clear relations. Keep pronouns only when their referents are unambiguous.
- Do not use emoji, decorative colons, or long dashes. Use a hyphen (-) when a dash is necessary. Otherwise, rewrite with a period or comma.
- Use bold and lists sparingly.
- Read the full rules in `references/{language}/prose-rules.md`.

### Summary: ASD-STE100 Style

- Use active voice and one idea per sentence. Limit each sentence to 20 words in English or 20 Chinese characters.
- Do not use semicolons, phrasal verbs, synonym rotation, stacked hedges, nominalizations, or marketing adjectives.
- Use simple tenses. Preserve hedges without changing a possibility into a fact.
- Read the full rules in `references/{language}/ste100-rules.md`.

### Schema: ASD-STE100 Style

- Use one concept per key and ordinary terms. Follow one naming style throughout.
- Use one term for each concept. Do not use undefined abbreviations.
- Keep each description to one sentence of no more than 15 English words or 20 Chinese characters. Express optionality with a required or optional field, not a hedge.
- Give each enum value one meaning. Keep table headers to three words or fewer. Keep list items parallel.
- Read the full rules in `references/{language}/ste100-rules.md`.

## Output Format

Return only the final text by default. Do not add an introduction, name the rules, summarize the edits, or add a closing question.

When the user asks to see the reasoning, such as "show the diff," "explain the changes," or "before/after," use a table with headers in the selected output language:

| Rule violated | Original | Rewritten |
|---|---|---|

For wording that remains longer to preserve precision, add `Kept as-is:` and state the exact meaning that must remain.

## Boundaries

- Do not use this skill for creative writing, marketing copy, or persuasive text.
- Asy edits form, not substance. If the source has no substantive content, say so without polishing empty text.
- Asy applies the structural discipline of ASD-STE100. It does not reproduce the official dictionary of about 900 words or claim dictionary-level compliance.

## References

- `references/en/` contains the English rules and examples.
- `references/zh/` contains the Chinese rules and examples.
