---
name: "deckless-study-kit"
description: "Turn a subject's lecture slides and past papers into a complete Learn Notes page plus a separate Active Recall page, so you can study without opening the slides."
---

# Deckless Study Kit

Use when Desmond asks to learn/revise a subject from its slides, prep for an exam, or says "deckless" / "learn + recall pages".

## Inputs (ask only for what is missing)
- SUBJECT: code and name
- FOLDER: folder with slides and past papers
- EXCLUDE: default = labs, tutorials, anything not examinable
- EXAM: date, format, chapters in scope

## Goal
He learns by understanding a topic first, then doing active recall later. The Learn page must be complete enough that he never opens the slides. It is for reading, not interactive quizzes. Recall is a separate page.

## Step 1 - Extract everything (never skip slides)
- Extract text per slide with a "=== <deck> slide N" header (pdftotext per page).
- Find slides with little or no text (figures, image tables). Render them (pdftoppm, montage) and read them. Their content must appear in the notes.
- Scanned PDFs (past papers): render pages and read them.
- Keep a coverage log: slide count per deck.

## Step 2 - Topic map
- Group slides into topics of 1-8 slides. Stable id per topic: <deck-prefix>-<short-name> (e.g. c1-delay, dl-crc) plus slide range.
- Every slide of every deck must fall in some topic's range. Prove it with a script before publishing.

## Step 3 - Learn Notes page (Artifact)
- One collapsible <details> per chapter, one collapsible card per topic, collapsed by default, Expand all / Collapse all buttons.
- Top, always open: concept map (inline SVG) placing every topic in the subject's main framework, boxes linking to topics; then 4-6 cross-chapter "threads".
- Each topic card, in order: Core idea (1-2 sentences); From the slides (every definition, list, table, number, standard, figure; tables stay tables; figures redrawn as simple SVG using theme tokens); Formula/steps in monospace; Worked example with real numbers, recomputed; Exam angle (how past papers ask it, what earns marks); Connects to (2-4 topic links).
- Show slide numbers on each topic (e.g. s35-42). Mark additions beyond the slides as "general knowledge" / "not on slide".
- Clicking an internal link opens the target topic and its parent chapter (small JS on click + hashchange).

## Step 4 - Active Recall page (separate Artifact)
- ~15 questions per chapter (about 1 per topic) plus a "Connections across chapters" section of 5-8.
- Each question is a collapsed card, answer hidden. Tags: Recall / Apply / Connect; past-paper questions tagged with paper and year (only if certain of the source).
- Every answer ends with a link to <learn-url>#<topic-id>.
- Include every in-scope past-paper question; recompute every calculation.
- Generate the page from a Python list of (topic_id, kind, question, answer, source) to keep it consistent.

## Step 5 - Checks before publishing
- Script: every href="#id" exists; every Recall link points to a real Learn id; 100% slide coverage; HTML tags balance.
- One render at 390px dark and 1280px light: no page-level sideways scroll; wide tables inside overflow-x containers.

## Step 6 - Deliver
- Publish both Artifacts (Learn first, so Recall can link to its URL; then add a Recall link to the Learn page).
- Save local copies into FOLDER using its naming convention (for Desmond's Masters folders: flat, "NN. <CODE> <Title>", next free number).
- Reply with both links, coverage numbers, and any slide that could not be read. Save both URLs to project memory.

## Style
Plain, direct English. Tables for comparisons. No filler. Light and dark mode both readable.

## Adapting
- Maths-heavy subjects: 2 worked examples per topic plus derivation steps.
- Design/project subjects: a decision table per topic (option, when to use, trade-off) instead of formulas.
- Only some chapters examined: Learn covers all, Recall prioritises in-scope questions.
