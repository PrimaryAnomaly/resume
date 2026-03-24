# CLAUDE.md

Personal CV/resume repository for Saeyoung Kim. LaTeX resume targeting postdoctoral and systems engineering positions.

## Critical Rule

**NEVER fabricate details.** If the user doesn't provide specific numbers, metrics, technologies, or accomplishments—ASK. Do not invent:
- Percentages or metrics
- Team sizes or budgets
- Technologies or tools
- Dates or timelines
- Project outcomes

Always ask: "What was the measurable impact?" or "Can you provide specific numbers?"

## Writing Style

- **Sound human**: Write like a real person, not an AI. Cover letters and prose must read naturally and conversationally. Avoid formulaic structures, overly polished phrasing, and dead giveaway AI phrases like "I am eager to apply," "I would welcome the opportunity," "This experience maps directly to," "I bring direct experience," "I thrive in," etc. Write the way someone would actually talk about their work.
- **No em dashes**: Do not use em dashes (---) in any document. Use periods, commas, or restructure sentences instead.

## Resume Writing Rules

- **Achievements, not duties**: Describe what you accomplished, not what you were responsible for
- **Quantify**: Use numbers (%, $, team size, scale) when the user provides them
- **Strong verbs**: Designed, Led, Architected, Delivered—not Helped, Assisted, Worked on
- **No fluff**: Cut buzzwords, passive voice, vague claims
- **Bullet formula**: `[Verb] + [What] + [How] + [Result]`

## Build

XeLaTeX is installed via MiKTeX on Windows, not in WSL. Compile using `cmd.exe`:

```bash
cmd.exe /c "cd /d D:\GitHubRepos\resume\<subfolder> && xelatex.exe <filename>.tex"
```

Do NOT use `xelatex` directly in bash — it will fail with "command not found".

## LaTeX Notes

- Requires XeLaTeX (for fontspec)
- Class: `moderncv` with `banking` style
- Font: Times New Roman
- Fix gray first name: `\name{\textcolor{black}{Saeyoung}}{Kim}`
- Bold job titles: `\cventry{dates}{\textbf{Title}}{Employer}{Location}{}{}`
- Use state abbreviations (MA, not Massachusetts)
