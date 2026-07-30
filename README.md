# AI Resume Parser

A browser based tool that extracts and organizes information from resumes (PDF/DOCX). Built for the Pinnacle Labs AI Internship Program.

**Live demo:** https://drive.google.com/file/d/1AUoTUcFA1RV9HCE7xjqh4UJhrTydpu5T/view?usp=sharing

## Features

- **Contact extraction:** pulls name, email, phone, LinkedIn, and GitHub straight from an uploaded resume
- **Section detection:** automatically finds and separates Summary, Skills, Education, Experience, and Certifications, even when a document has no consistent formatting
- **Skill categorization:** groups skills by category (Languages, Tools, AI & Data, etc.) when the resume uses labeled sub-sections, with a fallback to a flat list otherwise
- **Job Match Score:** paste in a job description and the tool:
  1. Scans it for known skill/requirement keywords
  2. Checks which of those requirements actually appear in the resume
  3. Returns a coverage percentage, plus a breakdown of what's covered and what's missing

## Tech stack

- Vanilla JavaScript, HTML, CSS. No backend, no build step, runs entirely in the browser
- [PDF.js](https://mozilla.github.io/pdf.js/) for PDF text extraction
- [Mammoth.js](https://github.com/mwilliamson/mammoth.js) for DOCX text extraction
- Regex-based section detection and keyword matching for job-fit scoring

## How it works

1. **Text extraction:** PDF.js or Mammoth.js pulls raw text out of the uploaded file
2. **Field extraction:** regular expressions locate email, phone, LinkedIn, and GitHub; name is inferred from the first few words of the document
3. **Section detection:** the parser scans for capitalized section headers (e.g. "SUMMARY", "Skills", "Education"), filters out false positives (like the word "skills" appearing mid-sentence), and splits the text into sections accordingly
4. **Skill parsing:** if a resume labels sub categories (e.g. "Languages: Python, SQL..."), the parser detects those labels and groups skills under them, keeping items like `Python(NumPy, Pandas)` intact rather than breaking on internal commas
5. **Job matching:** rather than just checking if a job posting happens to mention the candidate's existing skills, the tool extracts the *actual requirements* from the job description first, then checks resume coverage against those requirements. This gives a more meaningful score than a simple keyword overlap

## Known limitations

- Section and skill detection rely on pattern matching rather than a trained NLP model, so unusually formatted resumes may parse imperfectly
- The job-matching keyword vocabulary is a fixed list and won't catch every possible skill/requirement phrasing
- Name extraction is a heuristic (first few words before a separator) and can occasionally misfire on unconventional resume layouts

## Running locally

No build tools required. Just open `index.html` in a browser, or serve the folder with any static server (e.g. VS Code's Live Server extension).
