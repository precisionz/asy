# Asy: Functional Document Writing Skill

"The limits of my language mean the limits of my world." -- Ludwig Wittgenstein

Asy is a functional document writing skill for prose, summaries, and schemas. It applies Yomiyasu-style rules to prose and ASD-STE100 structure rules to summaries and schemas.

Asy currently supports English and Chinese. Each language has its own reference set, which allows the skill to add languages over time.

## Structure

| File | Purpose |
|---|---|
| `SKILL.md` | Entry point, language selection, writing rules, and reference routing |
| `references/en/` | English writing rules and examples |
| `references/zh/` | Chinese writing rules and examples |
| `asy.skill` | Offline package created from a snapshot of the skill directory |

Each language directory contains `prose-rules.md`, `ste100-rules.md`, and `examples.md`.

## Install

This repository is the skill directory. Clone or copy it to a skills directory named `asy`.

```bash
git clone https://github.com/precisionz/asy ~/.agents/skills/asy
```

## Offline Package

The `asy.skill` file is a ZIP archive. It contains a top-level `asy/` directory. Extract it to a skills directory to install the skill.

```bash
unzip asy.skill -d ~/.agents/skills/
```

On Windows, `Expand-Archive` requires a `.zip` extension:

```powershell
Copy-Item asy.skill asy.zip
Expand-Archive asy.zip -DestinationPath "$env:USERPROFILE\.agents\skills"
Remove-Item asy.zip
```

The package is a snapshot. Rebuild it after you update the skill directory.

## Use

Ask an agent to write in Asy style or describe the writing task. Before every writing task, Asy must ask the user to choose an output language. This requirement applies even when the request already names a language.

```text
Choose the output language:
1. English (en)
2. Chinese (zh)
```

Asy must wait for the user's selection. It does not use a default language.

## Sources

- The prose rules are adapted from [nanaism/yomiyasu](https://github.com/nanaism/yomiyasu) (MIT).
- The summary and schema rules derive from ASD-STE100 Issue 9 (January 2025). They are summarized by [danyuchn/asd-ste100-skill](https://github.com/danyuchn/asd-ste100-skill) (MIT).
- The official site is [asd-ste100.org](https://asd-ste100.org). This repository does not distribute the official dictionary.
