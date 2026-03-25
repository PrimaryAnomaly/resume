# CLAUDE.md

Personal CV/resume repository for Saeyoung Kim. LaTeX resumes targeting manufacturing test, systems integration, and hardware engineering positions.

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

## Resume Content Rules

- **Always include publications section.** Do not strip publications from any resume, regardless of role level.
- When combining cover letter + resume in one file (single-upload applications), use `\makelettertitle`/`\makeletterclosing`, then `\newpage`, then `\makecvtitle`.

## Cover Letters

- Use `\makelettertitle` / `\makeletterclosing` with `\recipient`, `\date`, `\opening`, `\closing`. Do NOT use `\makecvtitle` for cover letters (causes header/content overlap).
- Do NOT claim security clearance eligibility. User is not a US citizen.
- If a role requires clearance (not just ITAR), flag it and confirm before writing. Security clearance requires US citizenship; ITAR requires green card or citizenship.
- **Always disclose green card pending status** in cover letters for ITAR roles. User's green card is pending (as of March 2025).

## Build

XeLaTeX is installed via MiKTeX on Windows, not in WSL. Compile using `cmd.exe` with the Windows path equivalent of the current working directory:

```bash
cmd.exe /c "cd /d <windows-path-to-subfolder> && xelatex.exe <filename>.tex"
```

Do NOT use `xelatex` directly in bash — it will fail with "command not found".
Run twice for cross-references to resolve cleanly.

## LaTeX Notes

- Requires XeLaTeX (for fontspec)
- Class: `moderncv` with `banking` style
- Font: Times New Roman
- Fix gray first name: `\name{\textcolor{black}{Saeyoung}}{Kim}`
- Bold job titles: `\cventry{dates}{\textbf{Title}}{Employer}{Location}{}{}`
- Use state abbreviations (MA, not Massachusetts)
- Use Unicode characters directly (e.g., σ) instead of `\textsigma` which is undefined in XeLaTeX with Times New Roman
- When chaining two xelatex passes with `&&`, the second pass may fail if the PDF is open in a viewer (file lock). Run separately if needed.
