# AI Resume Parser

A browser-based tool that extracts and organizes information from résumés (PDF/DOCX) — built for the Pinnacle Labs AI Internship Program.

## Live demo
https://hanan-ai-eng.github.io/ai-resume-parser/

## Features
- Extracts name, email, phone, LinkedIn, and GitHub from uploaded résumés
- Detects and separates résumé sections (Summary, Skills, Education, Experience, Certifications)
- Groups skills by category (Languages, Tools, AI & Data, etc.)
- Job Match Score: compares résumé skills against a pasted job description and shows matched/missing skills

## Tech stack
- Vanilla JavaScript, HTML, CSS — no backend
- [PDF.js](https://mozilla.github.io/pdf.js/) for PDF text extraction
- [Mammoth.js](https://github.com/mwilliamson/mammoth.js) for DOCX text extraction
- Regex-based section detection and keyword matching for job-fit scoring

## How it works
The parser reads raw text from the uploaded file, then uses pattern matching to identify résumé sections and pull out contact info. Skills are grouped by category, and a lightweight keyword-matching algorithm compares them against a job description to generate a match score.
