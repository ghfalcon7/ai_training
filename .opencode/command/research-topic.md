---
description: Thoroughly research an agenda topic and fill its Markdown source file without overlapping other topics.
agent: build
---

Research and complete the topic source file specified in `$ARGUMENTS`.

Requirements:

- Treat `$ARGUMENTS` as the path to exactly one Markdown file under `Agenda/Module X - <name>/`. If it is missing, ambiguous, or does not identify exactly one file, ask for the file path before proceeding.
- Read `Agenda/Agenda.md`, the target file, and the other topic files under `Agenda/` before researching. Use them to establish the target topic's scope and avoid duplicating material assigned to another agenda topic.
- Conduct thorough research using authoritative, current primary sources whenever possible. Cross-check important claims rather than relying on a single source.
- Fill the target Markdown file with accurate, developer-focused source content suitable for preparing an AI training presentation. Cover the topic comprehensively within its agenda boundary.
- Preserve useful existing content, improving and integrating it instead of replacing it blindly.
- Include practical examples, risks, tradeoffs, and actionable guidance where relevant.
- Cite sources with direct links and finish with a concise references section.
- Do not modify `Agenda/Agenda.md`, any other topic Markdown file, or `ai-training-presentation.html`.
- Before finishing, compare the result against every topic in `Agenda/Agenda.md` and remove or narrow content that materially overlaps another topic. Brief cross-references are acceptable when needed for context, but leave detailed treatment to the corresponding topic.
- Proofread the completed file for factual consistency, clear structure, and duplicate content.

Make the edit directly and report the updated file path plus a concise summary of the research coverage.
