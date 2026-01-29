# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal CV/resume repository for Saeyoung Kim. Contains a LaTeX resume targeting postdoctoral and systems engineering positions.

## Build Commands

Compile the resume with XeLaTeX (required for fontspec/Unicode support):

```bash
cd resume_postdoc
xelatex resume_postdoc.tex
```

## Font Requirements

- **English**: Times New Roman
- **Korean**: Noto Sans CJK KR (optional - commented out if not installed)

## File Structure

- `resume_postdoc/resume_postdoc.tex` - Main resume document using `moderncv` class (banking style)

## LaTeX Notes

- Uses `fontspec` package requiring XeLaTeX or LuaLaTeX compiler
- Document class: `moderncv` with `banking` style
- Page margins: 0.6 inches on letter paper
- Hyperlinks enabled via `hyperref` with Unicode support

## moderncv Quirks

- **First name color**: Banking style renders first name in gray by default. Fix by wrapping in `\textcolor{black}{}` inside `\name{}`:
  ```latex
  \name{\textcolor{black}{Saeyoung}}{Kim}
  ```

- **Position emphasis**: Use `\textbf{}` around job titles in cventry to make them stand out:
  ```latex
  \cventry{dates}{\textbf{Job Title} | Description}{Employer}{Location}{}{}
  ```

- **Location alignment**: Keep location text short to avoid alignment issues. Use US state abbreviations (MA, not Massachusetts)
