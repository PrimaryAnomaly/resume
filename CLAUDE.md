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

XeLaTeX is installed via MiKTeX on Windows at `F:\MiKTeX\miktex\bin\x64\xelatex.exe`. It is NOT on the Windows PATH. Compile using the full path:

```bash
cmd.exe /c "cd /d <windows-path-to-subfolder> && F:\MiKTeX\miktex\bin\x64\xelatex.exe <filename>.tex"
```

Do NOT use `xelatex` directly in bash — it will fail with "command not found".
Run twice for cross-references to resolve cleanly.

## Resume Formatting Rules

- **No word hyphenation**: Use `\hyphenpenalty=10000` to prevent words from being split across lines.
- **Keep bullets to one line**: Write concise bullets that fit on a single line where possible. Trim filler words rather than wrapping.
- **Keep headers with content**: Use `\needspace{6\baselineskip}` (or more) before section headers and `\cventry` blocks to prevent orphaned headers at page bottoms.
- **Full publications**: Always include the complete publication list (9 journals, 4 conferences, 1 seminar as of March 2026). Never truncate to "Selected Publications."
- **Page numbering**: Use `\usepackage{lastpage}` with `\rfoot{\addressfont\itshape\textcolor{gray}{\thepage/\pageref{LastPage}}}` for correct N/M page numbers. Compile twice.

## File Parsing (PPTX/DOCX)

- `liteparse` (`lit` CLI) needs LibreOffice for Office files. LibreOffice is at `F:\LibreOffice\program` but not on Windows PATH.
- Workaround: Convert directly with `cmd.exe /c "F:\LibreOffice\program\soffice.exe --headless --convert-to pdf --outdir <outdir> <infile>"`, then read the PDF.
- Google Drive is mountable in WSL: `sudo mkdir /mnt/g && sudo mount -t drvfs G: /mnt/g`
- UMass Lowell OneDrive is NOT synced locally / not accessible from WSL.

## LaTeX Notes

- Requires XeLaTeX (for fontspec)
- Class: `moderncv` with `banking` style
- Font: Times New Roman
- Fix gray first name: `\name{\textcolor{black}{Saeyoung}}{Kim}`
- Bold job titles: `\cventry{dates}{\textbf{Title}}{Employer}{Location}{}{}`
- Use state abbreviations (MA, not Massachusetts)
- Use Unicode characters directly (e.g., σ) instead of `\textsigma` which is undefined in XeLaTeX with Times New Roman
- When chaining two xelatex passes with `&&`, the second pass may fail if the PDF is open in a viewer (file lock). Run separately if needed.

## Korean Resume Notes

- For Korean resumes, use `xetexko` package (NOT `xeCJK`). xeCJK is for Chinese/Japanese and eats Korean word spaces.
- Font: Noto Sans KR (available at `C:\Windows\Fonts\NotoSansKR-Regular.ttf` and `NotoSansKR-Bold.ttf`). Use file path approach with fontspec.
- Set `\setmainhangulfont` and `\setsanshangulfont` for Korean characters, `\setmainfont`/`\setsansfont` for Latin.
- Use `\raggedright` for Korean text. Justified text causes uneven word spacing since TeX stretches spaces differently for CJK.
- Do NOT use `InterHangul` font option to add inter-character spacing. Korean characters within words should be tight; only word spaces provide separation.
- The Korean PM resume uses the Sourabh Bajaj / Hyunggi Chang article-based template (not moderncv) for cleaner spacing.
- **No transliterations**: Do not transliterate English words into Korean (e.g., 페이로드, 모니터링, 인터페이스). Either use the proper Korean word (탑재체, 공동체, 작업 흐름) or keep the English term as-is (Payload, Monitoring, Interface). The user strongly dislikes 번역투 (translation-style Korean).
- LaTeX tilde `~` is a non-breaking space, not a range character. Use `\textasciitilde` for ranges like "5~8차".
