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

## Resume Writing Rules

- **Achievements, not duties**: Describe what you accomplished, not what you were responsible for
- **Quantify**: Use numbers (%, $, team size, scale) when the user provides them
- **Strong verbs**: Designed, Led, Architected, Delivered—not Helped, Assisted, Worked on
- **No fluff**: Cut buzzwords, passive voice, vague claims
- **Bullet formula**: `[Verb] + [What] + [How] + [Result]`

## Build

```bash
cd resume_postdoc && xelatex resume_postdoc.tex
```

## LaTeX Notes

- Requires XeLaTeX (for fontspec)
- Class: `moderncv` with `banking` style
- Font: Times New Roman
- Fix gray first name: `\name{\textcolor{black}{Saeyoung}}{Kim}`
- Bold job titles: `\cventry{dates}{\textbf{Title}}{Employer}{Location}{}{}`
- Use state abbreviations (MA, not Massachusetts)
