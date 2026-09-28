# Arabic Subtitling and Captioning Guidelines
### دليل معايير وقواعد الترجمة المرئية والتفريغ النصي باللغة العربية

Comprehensive guidelines, stylistic rules, quality control standards, and automated QC tooling for Arabic subtitling, closed captioning, and SDH (Subtitles for the Deaf and Hard of Hearing).

This repository adheres to industry-grade specifications—primarily the **Netflix Timed Text Style Guide (TTSG) for Arabic** (incorporating the **December 2025 updates**)—tailored for professional streaming delivery, educational media, social platforms (YouTube, TikTok), and automated AI subtitling workflows.

It is packaged as both a **Universal Agent Skill** (installable via `npx skills add`) and a **Claude Code Plugin** (with custom slash commands).

---

## Installation & Setup

### Option 1: Install as a Universal Agent Skill (`npx skills`)
Install into AI coding agents (Claude Code, Cursor, Windsurf, GitHub Copilot) with one command:

```bash
# Add to current project
npx skills add EngDawood/arabic-video-subtite-skill

# Add globally to user configuration (~/.agents/skills/)
npx skills add EngDawood/arabic-video-subtite-skill -g

# Target specific agents
npx skills add EngDawood/arabic-video-subtite-skill -a claude-code -a cursor -g
```

---

### Option 2: Use as a Claude Code Plugin

#### A. Run Directly in Current Session (Local Development)
Load the plugin directly from the project directory:
```bash
claude --plugin-dir /path/to/arabic-subtitling-guidelines
```

#### B. Permanent Installation via Marketplace
```bash
# Add repository as a marketplace source
claude plugin marketplace add EngDawood/arabic-video-subtite-skill

# Install the plugin
claude plugin install arabic-subtitling@EngDawood/arabic-video-subtite-skill
```

#### Available Slash Commands in Claude Code:
- `/check-subtitles <file.srt>`: Runs automated QC verification and linguistic audits on your subtitle file.
- `/translate-subtitles <dialogue>`: Translates and adapts dialogue into Modern Standard Arabic compliant with the 42 CPR limit and ECR translation strategies.

---

## Repository Structure / بنية المستودع

```text
arabic-subtitling-guidelines/
├── .claude-plugin/
│   └── plugin.json                       # Claude Code plugin manifest
├── commands/                             # Claude Code slash commands
│   ├── check-subtitles.md                # /check-subtitles command
│   └── translate-subtitles.md            # /translate-subtitles command
├── skills/
│   └── arabic-subtitling-guidelines/     # Universal Agent Skill bundle
│       ├── SKILL.md                      # Agent instructions & prompt triggers
│       ├── references/
│       │   ├── netflix-arabic-rules.md   # Full Netflix Arabic TTSG (Dec 2025 updates)
│       │   └── translation-strategies.md # ECR strategies, condensation & FAR Model
│       └── scripts/
│           └── check_subtitles.py        # Automated Python QC & autofix script
└── README.md                             # Documentation & reference manual
```

---

## Table of Contents / جدول المحتويات

- [Overview & Subtitling Modes](#overview--subtitling-modes)
- [Workflow](#workflow)
- [Core Guidelines & Cheat Sheet](#core-guidelines--cheat-sheet)
  - [1. Language & Vocabulary (Dec 2025 Updates)](#1-language--vocabulary-dec-2025-updates)
  - [2. Layout & Line Breaking (تنسيق الأسطر وكسر العبارات)](#2-layout--line-breaking-تنسيق-الأسطر-وكسر-العبارات)
  - [3. Timing & Reading Speed (التوقيت وسرعة القراءة)](#3-timing--reading-speed-التوقيت-وسرعة-القراءة)
  - [4. Punctuation & Typography (علامات الترقيم والطباعة)](#4-punctuation--typography-علامات-الترقيم-والطباعة)
  - [5. Numbers & Dates (الأرقام والتواريخ)](#5-numbers--dates-الأرقام-والتواريخ)
  - [6. Diacritics (التشكيل وضبط الكلمات)](#6-diacritics-التشكيل-وضبط-الكلمات)
  - [7. Forced Narratives & Foreign Speech (النصوص الظاهرة)](#7-forced-narratives--foreign-speech-النصوص-الظاهرة)
  - [8. SDH & Sound Descriptions (تسميات الصم وضعاف السمع)](#8-sdh--sound-descriptions-تسميات-الصم-وضعاف-السمع)
- [Automated QC Tool (`scripts/check_subtitles.py`)](#automated-qc-tool-scriptscheck_subtitlespy)
- [The FAR Quality Model (Pedersen, 2017)](#the-far-quality-model-pedersen-2017)
- [RTL & Technical Considerations](#rtl--technical-considerations)
- [Manual QC Checklist](#manual-qc-checklist)
- [References & Authoritative Sources](#references--authoritative-sources)

---

## Overview & Subtitling Modes

Determine the project mode before starting work:

| Mode | Input &rarr; Output | Primary Objective & Considerations |
| :--- | :--- | :--- |
| **A. Arabic Captions (تفريغ وتسميات)** | Arabic audio &rarr; Arabic text | Faithful transcription, Modern Standard Arabic (MSA) consistency, optional SDH sound cues in MSA. |
| **B. Translated Subtitles (ترجمة مرئية)** | Foreign audio &rarr; Arabic text | Accurate translation into MSA, cultural reference adaptation, condensation to fit reading speed limits. |
| **C. Review & QC (مراجعة وضبط جودة)** | Existing SRT / VTT / TTML | Validation against line length, timing rules, shot changes, and linguistic accuracy using `check_subtitles.py`. |

---

## Workflow

1. **Obtain Timed Source**: Start from a timed transcript or generate word/phrase-level timestamps.
2. **Translate / Transcribe into Modern Standard Arabic (MSA)**:
   - Establish a glossary for character names, locations, and recurring terminology.
   - For translated content (Mode B), apply cultural adaptation strategies from `references/translation-strategies.md`.
3. **Segment & Break Lines**:
   - Break according to natural grammatical and semantic units (never mid-phrase).
   - Aim for 1 line where possible; use bottom-heavy 2-line structures when necessary.
4. **Apply Style & Typography Rules**:
   - Verify character limits (max 42 chars/line), punctuation, quotation marks, and number rules from `references/netflix-arabic-rules.md`.
5. **Time & Synchronize**:
   - Align in-time with speech onset; respect shot cuts and minimum gap rules (2 frames).
6. **Automated Verification**:
   - Run `python skills/arabic-subtitling-guidelines/scripts/check_subtitles.py file.srt --fps 24`.
   - Optionally apply mechanical auto-fixes with `--fix output.srt`.
7. **Manual QC Pass**:
   - Score against the FAR Model and review for BiDi rendering quirks.

---

## Core Guidelines & Cheat Sheet

### 1. Language & Vocabulary (Dec 2025 Updates)
- **Modern Standard Arabic (الفصحى)**: Use MSA across all subtitles. Do not use dialectal phrases or colloquial words (e.g., avoid `برجاء`, `يا خبر`, `يا ستّار`). Use the closest MSA equivalent.
- **Translation vs. Transliteration (Updated Dec 2025)**:
  - Strive to identify established Arabic equivalents first.
  - If an Arabic equivalent is absent, ambiguous, or seldom used, provide a transliteration within double quotes: `"بودكاست"`.
  - When a transliteration is fully adopted into common usage and accepts standard Arabic plurals, omit quotes: `راديو` / `راديوهات`، `كمبيوتر` / `كمبيوترات`.
- **Acronyms & Abbreviations (Updated Dec 2025)**:
  - Translate widely known acronyms: *CIA* &rarr; `الوكالة المركزية للاستخبارات`.
  - Transliterate familiar phonetic acronyms: *OPEC* &rarr; `أوبك`، *UNICEF* &rarr; `يونيسف`.
  - Arabic abbreviations for time and metric units take a space and **no period**: `5 كغ` (not `5 كغ.`), `10 سم`, `ص` (a.m.), `م` (p.m.).
- **Proper Names & Currencies**:
  - Transliterate character names (First Name then Last Name).
  - Translate place names and currencies to standard Arabic: `المكسيك` (Mexico), `اليورو` (Euro). Never convert currency figures mathematically.
- **No Censorship**: Render dialogue faithfully to match source tone without adding gratuitous vulgarity.
- **No Italics**: Italics are strictly forbidden in Arabic subtitles under any circumstance. Never use `<i>` or `<em>` tags.

---

### 2. Layout & Line Breaking (تنسيق الأسطر وكسر العبارات)
- **Line Length**: Maximum **42 characters per line** (including spaces).
- **Line Count**: Maximum **2 lines** per subtitle event.
- **Visual Balance**: Prefer bottom-heavy two-liners. Avoid leaving a single orphaned word on the second line.
- **Grammatical Integrity (قواعد كسر السطر)**: Do **not** split a line between tightly bound grammatical structures:
  - Verb and subject (الفعل وفاعله)
  - Preposition and governed noun (حرف الجر واسم المجرور)
  - Mudaf and Mudaf Ilayh (المضاف والمضاف إليه)
  - Adjective and noun (الصفة والموصوف)
  - Conjunction / particle and verb (أدوات النصب أو الجزم وفعلها)
  - Number and counted noun (العدد والمعدود)
  - Vocative particle and vocative (حرف النداء والمنادى)
  - Exception particle and excepted word (أداة الاستثناء والمستثنى)
- **Dual Speakers (حوار شخصيتين)**:
  - Use a hyphen followed by a space (`- `) at the beginning of each speaker's line.
  - One speaker per line (maximum 2 speakers). Each line must be a self-contained sentence.

---

### 3. Timing & Reading Speed (التوقيت وسرعة القراءة)
- **Duration per Event**:
  - Minimum: **5/6 second** (approx. 20 frames at 24 fps).
  - Maximum: **7 seconds**.
- **Reading Speed**:
  - Adults: Up to **20 characters per second (CPS)**.
  - Children: Up to **17 CPS**.
  - SDH: Up to **23 CPS** (adults) / **20 CPS** (children).
- **Gaps Between Subtitles**:
  - Minimum gap: **2 frames**.
  - At 24 fps, gaps between 3 and 11 frames must be closed to 2 frames (chaining), or left as $\ge$ 1/2 second (12+ frames) to prevent perceptual flashing.
- **Shot Changes**:
  - Snap in-time to cut if dialogue starts within 1–2 frames after a cut.
  - Do not cross shot changes unless dialogue crosses them continuously.

---

### 4. Punctuation & Typography (علامات الترقيم والطباعة)
- **Ellipsis (علامة الحذف)**:
  - Always use the single Unicode character `…` (`U+2026`), never three individual periods (`...`).
  - Use for trailing off speech, pauses $\ge$ 2 seconds, or interrupted speech.
  - Do **not** place ellipses across consecutive subtitles when a sentence simply continues naturally.
- **Punctuation Spacing**:
  - No space before commas (،), question marks (؟), exclamation marks (!), or colons (:).
  - Never combine question and exclamation marks (`؟!` or `!?`).
  - Repeat the conjunction `و` instead of using serial commas in lists (e.g., `المدونون والمترجمون والمحررون`).
- **Quotation Marks (علامات التنصيص)**:
  - Use straight double quotes (`"..."`).
  - When prefixed with the definite article `ال`, join with a kashida: `الـ"برونكس"`.
- **URLs & Hashtags**:
  - Avoid Latin scripts. Transliterate or describe (e.g., `وسم#` or `على الموقع الظاهر على الشاشة`).

---

### 5. Numbers & Dates (الأرقام والتواريخ)
- **Numbers 1 to 10**: Write as words with correct Arabic gender agreement (e.g., `رجلين اثنين`, `خمس سيدات`).
- **Numbers 11 and above**: Write in digits (e.g., `15`, `250`).
- **Ordinals**:
  - 1st to 9th: Write in words (`الموسم الأول`).
  - 10th and above: Digits with kashida (`الـ21`).
- **Formatting**:
  - Thousands separator: comma (`1,234`).
  - Decimals: point with leading zero (`0.5`).
  - Percentages: write the word out (`25 بالمئة`).
  - Calendar months: use Gregorian names standard in MSA (`يناير`, `أغسطس`).
  - Units: metric system unless plot-relevant.

---

### 6. Diacritics (التشكيل وضبط الكلمات)
- Apply diacritics **only** when ambiguity changes the meaning:
  - Shadda (e.g., `شابّ` vs `شابَ`).
  - Passive verbs (بناء الفعل للمجهول) where context does not clarify it immediately.
  - Feminine plural nun or speaker's ya.
- **Tanween Fatha (تنوين الفتح)**: Place the tanween on the letter preceding the alif (`كتابًا` rather than `كتاباً`) for font rendering compatibility.

---

### 7. Forced Narratives & Foreign Speech (النصوص الظاهرة)
- Subtitle on-screen signs, inserts, or foreign dialogue only if plot-relevant and not covered by spoken audio.
- Enclose translations of on-screen text in straight quotes: `"ممنوع الدخول"`.
- Never combine on-screen text and dialogue in the same event.
- Time the subtitle to match the graphic display exactly.

---

### 8. SDH & Sound Descriptions (تسميات الصم وضعاف السمع)
- All sound descriptions and speaker tags must be enclosed in square brackets: `[زقزقة عصافير]`, `[صوت محرك سيارة]`.
- Use the **indefinite grammatical form** for sounds.
- **Strict MSA Requirement (Dec 2025)**: All SDH descriptors must be written in MSA, even when transcribing colloquial dialogue.
- Music / singing: place musical notes with spaces around lyrics: `♪ ... ♪`.

---

## Automated QC Tool (`scripts/check_subtitles.py`)

This repository provides an automated Python CLI tool to validate `.srt` and `.vtt` files against all timing and layout rules.

### Usage:

```bash
# Check subtitle file against standard Netflix parameters (24 FPS, 42 CPR, 20 CPS)
python skills/arabic-subtitling-guidelines/scripts/check_subtitles.py subtitles.srt --fps 24

# Check WebVTT file with custom reading speed and line length
python skills/arabic-subtitling-guidelines/scripts/check_subtitles.py subtitles.vtt --max-cpr 40 --max-cps 17

# Automatically fix mechanical errors (ellipses, Arabic punctuation, strip italics)
python skills/arabic-subtitling-guidelines/scripts/check_subtitles.py subtitles.srt --fix fixed_subtitles.srt
```

### Checks Performed:
- Line length (> 42 characters per row).
- Line count (> 2 lines).
- Event duration (< 5/6s or > 7.0s).
- Reading speed (> 20.0 CPS for adults).
- Overlapping timestamps and gaps < 2 frames.
- Chaining gap warnings (gaps between 3 and 11 frames).
- Banned italics HTML tags (`<i>`, `<em>`).
- Western commas `,` or question marks `?` in Arabic text.
- Spaces before punctuation marks.
- Double punctuation (`؟!` / `!?`).
- ASCII triple dots `...` instead of Unicode `…`.
- Orphan words on second lines.

---

## The FAR Quality Model (Pedersen, 2017)

For academic grading or professional vendor evaluation, subtitles are assessed across three pillars:

1. **Functional Equivalence (F)**:
   - **Semantic Errors**: Minor (0.5 pt), Standard (1.0 pt), Serious (2.0 pts).
   - **Stylistic Errors**: Minor (0.5 pt), Standard (1.0 pt).
2. **Acceptability (A)**:
   - **Grammar Errors**: Minor (0.25 pt), Standard (0.5 pt), Serious (1.0 pt).
   - **Spelling / Hamza**: Minor (0.25 pt), Standard (0.5 pt).
   - **Idiomaticity / Calques**: Minor (0.25 pt), Standard (0.5 pt).
3. **Readability (R)**:
   - **Line Length (>42 CPR)**: Minor (0.25 pt), Standard (0.5 pt).
   - **Reading Speed (>20 CPS)**: Standard (0.5 pt), Serious (1.0 pt).
   - **Line Breaks & Orphan Words**: Minor (0.25 pt), Standard (0.5 pt).
   - **Punctuation & BiDi Alignment**: Minor (0.25 pt), Standard (0.5 pt).
   - **Spotting & Shot Cuts**: Minor (0.25 pt), Standard (0.5 pt).

### Quality Benchmark Formula:
$$\text{Error Score per 100 Subtitles} = \left( \frac{\text{Total Penalty Points}}{\text{Total Subtitle Events}} \right) \times 100$$

- **$\le 5.0$**: Broadcast Quality (Pass)
- **$5.1 - 10.0$**: Minor Revisions Required
- **$> 15.0$**: Unacceptable (Fail / Re-translate)

*See [references/translation-strategies.md](skills/arabic-subtitling-guidelines/references/translation-strategies.md) for full details and examples.*

---

## RTL & Technical Considerations

- **UTF-8 Encoding**: Always save files in UTF-8 without BOM.
- **BiDi Punctuation Bugs**: If a video player incorrectly places trailing punctuation on the right side of an RTL sentence, prepend or append the Unicode **Right-to-Left Mark (RLM)** (`U+200F`).
- **Font Rendering**: For burned-in subtitles, use fonts with comprehensive Arabic shaping support (e.g. *Noto Sans Arabic*, *Geeza Pro*, *Arial*), ensuring sufficient line height so harakat do not overlap.

---

## Manual QC Checklist

- [ ] **Meaning & Nuance**: Conveys audio accurately without omitting plot-critical details.
- [ ] **Register**: Pure Modern Standard Arabic; zero colloquial slips.
- [ ] **Line Breaks**: Clean syntactic boundaries; no orphan words on line 2.
- [ ] **Typography**: Unicode `…` used; straight quotes; kashida attached (`الـ"..."`).
- [ ] **Dual Speakers**: Hyphen-space format (`- `) on each line.
- [ ] **Measurements**: Spaces before units; no periods after SI symbols (`5 كغ`).
- [ ] **Pacing**: Subtitle reading feels natural when played alongside video.

---

## References & Authoritative Sources

1. [TTSG Updates - December 2025](https://partnerhelp.netflixstudios.com/hc/en-us/articles/47550553159187-TTSG-Updates-December-2025)
2. [Timed Text Style Guide: General Requirements](https://partnerhelp.netflixstudios.com/hc/en-us/articles/215758617-Timed-Text-Style-Guide-General-Requirements)
3. [Timed Text Style Guide: Subtitle Timing Guidelines](https://partnerhelp.netflixstudios.com/hc/en-us/articles/360051554394-Timed-Text-Style-Guide-Subtitle-Timing-Guidelines)
4. [Timed Text Style Guide: Subtitle Templates](https://partnerhelp.netflixstudios.com/hc/en-us/articles/219375728-Timed-Text-Style-Guide-Subtitle-Templates)
5. [Timed Text Style Guide: Product Supplemental & Marketing Assets](https://partnerhelp.netflixstudios.com/hc/en-us/articles/115000239632-Timed-Text-Style-Guide-Product-Supplemental-Marketing-Assets)
6. [Arabic Timed Text Style Guide](https://partnerhelp.netflixstudios.com/hc/en-us/articles/215517947-Arabic-Timed-Text-Style-Guide)
7. Pedersen, J. (2017). *The FAR model: assessing quality in interlingual subtitling*. The Journal of Specialised Translation, (28), 210–229. [https://doi.org/10.26034/cm.jostrans.2017.239](https://doi.org/10.26034/cm.jostrans.2017.239)
