# Prose Rules (Yomiyasu Style)

Applies to long paragraphs and explanatory prose. The rules are language-independent. Examples use English.

## 1. Preserve Meaning (Highest Priority)

Keep these four aspects unchanged:

1. **Claim:** What the text says. Do not shift an argument from one concept to another, such as changing "the core problem" to "the goal."
2. **Emphasis:** What matters most and what receives less emphasis. Do not weaken a negation or change the order of emphasis.
3. **Certainty:** Preserve certainty and uncertainty. Do not change "may fail" to "fails," or weaken "fails" to "may fail."
4. **Sentence function:** Preserve whether a sentence states information, a recommendation, a rule, a plan, or an evaluation. Do not turn a statement into an instruction. "The cache refreshes" does not mean "Refresh the cache." Do not turn a recommendation into a rule.

## 2. Do Not Add or Remove Information

- Do not add an actor, cause, number, example, term, or qualification that is absent from the source.
- Do not remove a condition, scope, number, exception, or safety qualification.
- If information is missing or a sentence is unclear, mark the gap explicitly, such as "(owner TBD)" or "(retry limit TBD)." List the items that need confirmation. Do not guess.

## 3. Sentence Structure

- Give each sentence a traceable subject and predicate: identify who or what does what to which object.
- Put one idea in each sentence.
- Split a long sentence only when a connector in the next sentence can preserve the relation, such as cause, sequence, or contrast. Do not split a sentence when a final purpose or reason clause would change meaning if moved.
- Use connectors such as "therefore," "but," "also," "so," "however," and "in addition" only when they express a specific, traceable relation. If the relation is unclear, do not guess. Mark it for confirmation.
- Keep a pronoun such as "this," "that," or "the former" only when it has one clear referent. Otherwise, repeat the noun.
- Remove empty previews such as "Here are three points." If the preview carries meaning, include that meaning in the relevant sentence. Otherwise, delete it.
- Editing reference for sentence length: an average of 12–25 words in English and 20–40 characters in Chinese. Do not split sentences only to meet a length target.
- Keep noun modifier chains to three nouns or fewer. "Fuel pump valve" is acceptable. Rewrite "high pressure fuel pump inlet valve assembly" as separate sentences or use prepositional phrases.

## 4. One Topic per Paragraph

- Keep each paragraph to one topic.
- Do not merge paragraphs with different topics. Split paragraphs that mix topics without changing sentence order.

## 5. Avoid Metaphors and Personification

- Replace metaphorical verbs with ordinary words of the same scope. Preserve the original meaning, including nuances such as regret, reluctance, or understatement.
  - "The data quietly rots" → "The data becomes inconsistent without a log entry."
  - "Dive into the code" → "Look at the code in detail."
- Do not assign emotions or intent to tools, code, or systems. Replace "the compiler complains" with "the compiler reports an error."
- Apply this rule only to figurative meanings. Keep literal meanings such as "the glass breaks."
- Keep natural expressions that do not sound artificial. A useful test is whether the expression was common in ordinary writing before generative AI became widespread.

## 6. Remove Self-Labeling and Filler

- Delete openings that add no meaning, such as "It's important to note that," "The key point is," and "In conclusion."
- Exception: if the opening carries an evaluation, preserve the evaluation in the predicate. For example, change "It is important that X" to "X is critical."
- For a contrast of the form "not A, but B," use a positive sentence only when removing the negation preserves the claim. Keep the negation when it corrects a likely misunderstanding.
- Do not end technical documents with calls to action such as "Hope this helps!" or "Try it today."

## 7. Formatting

- Do not use emoji.
- Do not use decorative colons in headings or at the end of sentences. Keep label-value colons, such as "Goal: portal" and "date: 10:00."
- Do not use long dashes. Use a hyphen (-) when a dash is necessary. Otherwise, use a period, comma, or separate sentence.
- Use bold sparingly: no more than one or two instances per 1,000 words, and only for terms readers must remember.
- Treat bold as formatting only. Put sentence punctuation outside the bold text. If bold markers next to CJK punctuation or quotation marks break rendering, add a space outside the markers. That space is for rendering and is not extra whitespace.
- Keep lists to 15% or less of a prose document. Use lists for actual lists, not to split sentences.
- Remove parenthetical text that only repeats nearby context.
- Preserve the source document's register, such as formal or neutral. Do not mix registers.

## 8. Preserve the Author's Stance

Identify the document's stance, then keep each sentence consistent with it:

- **Recommendation:** The reader should act, as in "you should..." or an equivalent recommendation.
- **Rule:** The reader must comply, as in "the system requires..." or "must..."
- **Description:** The text states a fact or behavior, as in "the system does..."

Preserve differences in strength within the same stance. Do not increase an obligation expressed with "should" to "must," or weaken a required step.

## 9. Language-Specific Phrases to Avoid

### English

- Verbs and phrases: "delve," "harness" in a marketing sense, "under the hood," and "at its core."
- Stock phrases: "it's worth noting," "seamless," "robust," "powerful," "cutting-edge," and "game-changer."
- Clichés: "the crux of the matter," "a deep dive," "elevate" without a factual meaning, and "streamline" without a specific object.

### Chinese

- Jargon: 赋能, 抓手, 底层逻辑, 闭环, 颗粒度 when not used technically, 心智, 拉齐, 沉淀, 打法, 组合拳, and 链路 when not used for a network link.
- Stock phrases: 至关重要 at the start of a sentence, 不言而喻, 毋庸置疑, 一劳永逸, and 悄悄, 悄然, or 静默 in figurative senses.

Keep these expressions when the document defines them as terms.

- **Inflated role names:** Replace names such as "contract" for a rule or "master copy" for a reference document with ordinary role names such as "rule," "guideline," "source text," or "comparison copy." Keep literal meanings and defined terms.
- **Vague words that sound specific:** Check words such as "essence," "feel," "vibe," or "decision OS" against the source. Keep them when they are defined terms or the topic of the document. Otherwise, mark the reference for confirmation.

## 10. Slogan Fragments and Rhythm

- Do not use slogan-like fragments in technical prose, such as "For the team. For everyone." Rewrite a source slogan as a complete sentence that preserves its meaning. Do not delete it.
- Do not split complete sentences into a series of very short sentences.
- Adjust sentence endings or patterns only when three or more consecutive sentences repeat them and the change removes an artificial tone. Do not vary natural sentences just for variety.

## Sources

Adapted from yomiyasu by nanaism, including `SKILL.md`, `references/gemini-syntax.md`, and `references/slop-catalog.md`. Adapted for English and Chinese.
