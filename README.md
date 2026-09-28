# Arabic Subtitling and Captioning Guidelines
### دليل معايير وقواعد الترجمة المرئية والتفريغ النصي باللغة العربية

Comprehensive guidelines, stylistic rules, and quality control standards for Arabic subtitling, closed captioning, and SDH (Subtitles for the Deaf and Hard of Hearing).

This guide adapts industry-grade specifications—primarily the **Netflix Timed Text Style Guide (TTSG) for Arabic**—tailored for professional streaming delivery, educational media, social platforms (YouTube, TikTok), and automated subtitling workflows.

---

## Table of Contents / جدول المحتويات

- [Overview & Subtitling Modes](#overview--subtitling-modes)
- [Workflow](#workflow)
- [Core Guidelines & Cheat Sheet](#core-guidelines--cheat-sheet)
  - [1. Language & Register (اللغة والأسلوب)](#1-language--register-اللغة-والأسلوب)
  - [2. Layout & Line Breaking (تنسيق الأسطر وكسر العبارات)](#2-layout--line-breaking-تنسيق-الأسطر-وكسر-العبارات)
  - [3. Timing & Reading Speed (التوقيت وسرعة القراءة)](#3-timing--reading-speed-التوقيت-وسرعة-القراءة)
  - [4. Punctuation & Typography (علامات الترقيم والطباعة)](#4-punctuation--typography-علامات-الترقيم-والطباعة)
  - [5. Numbers & Dates (الأرقام والتواريخ)](#5-numbers--dates-الأرقام-والتواريخ)
  - [6. Diacritics (التشكيل وضبط الكلمات)](#6-diacritics-التشكيل-وضبط-الكلمات)
  - [7. Forced Narratives & Foreign Speech (النصوص الظاهرة واللغات الأجنبية)](#7-forced-narratives--foreign-speech-النصوص-الظاهرة-واللغات-الأجنبية)
  - [8. SDH & Sound Descriptions (تسميات الصم وضعاف السمع)](#8-sdh--sound-descriptions-تسميات-الصم-وضعاف-السمع)
- [RTL & Technical Considerations (الجوانب التقنية واتجاه النص)](#rtl--technical-considerations-الجوانب-التقنية-واتجاه-النص)
- [Quality Control (QC) Checklist](#quality-control-qc-checklist)
- [References & Credits](#references--credits)

---

## Overview & Subtitling Modes

Determine the project mode before starting work:

| Mode | Input &rarr; Output | Primary Objective & Considerations |
| :--- | :--- | :--- |
| **A. Arabic Captions (تفريغ وتسميات)** | Arabic audio &rarr; Arabic text | Faithful transcription, Modern Standard Arabic (MSA) consistency, optional SDH sound cues. |
| **B. Translated Subtitles (ترجمة مرئية)** | Foreign audio &rarr; Arabic text | Accurate translation into MSA, cultural reference adaptation, condensation to fit reading speed limits. |
| **C. Review & QC (مراجعة وضبط جودة)** | Existing SRT / VTT / TTML | Validation against line length, timing rules, shot changes, and linguistic accuracy. |

---

## Workflow

1. **Obtain Timed Source**: Start from a timed transcript or generate word/phrase-level timestamps.
2. **Translate / Transcribe into Modern Standard Arabic (MSA)**:
   - Establish a glossary for character names, locations, and recurring terminology.
   - Avoid colloquialisms unless explicitly authorized.
3. **Segment & Break Lines**:
   - Break according to natural grammatical and semantic units (never mid-phrase).
   - Aim for 1 line where possible; use bottom-heavy 2-line structures when necessary.
4. **Apply Style & Typography Rules**:
   - Check character limits (max 42 chars/line), punctuation, quotation marks, and number rules.
5. **Time & Synchronize**:
   - Align in-time with speech onset; respect shot cuts and minimum gap rules (2 frames).
6. **QC Pass**:
   - Check reading speed (CPS / WPM) and perform visual review for RTL formatting anomalies.

---

## Core Guidelines & Cheat Sheet

### 1. Language & Register (اللغة والأسلوب)
- **Modern Standard Arabic (الفصحى)**: Use MSA across all subtitles. Do not use dialectal phrases or colloquial words (e.g., avoid `برجاء`, `يا خبر`, `يا ستّار`). Use the closest MSA equivalent.
- **Geographical Names & Currencies**: Translate into established Arabic forms (e.g., `المكسيك`, `أثينا`, `اليورو`, `البيزو`). Never convert monetary values mathematically.
- **Names & Transliteration**:
  - Transliterate proper names (First Name then Last Name).
  - Transliterate nicknames unless the literal meaning directly influences the plot.
- **Onomatopoeia & Fillers**:
  - Do not translate non-verbal interjections (`wow`, `ouch`).
  - Drop filler words (`really`, `you know`, `just`) unless they add semantic weight or character intent.
- **Profanity & Tone**:
  - Never censor or sanitize speech arbitrarily.
  - Translate the tone and intent faithfully without adding gratuitous obscenity.
- **No Italics**: Italics are not used in Arabic typography. Never apply `<i>` tags to Arabic subtitles.

---

### 2. Layout & Line Breaking (تنسيق الأسطر وكسر العبارات)
- **Line Length**: Maximum **42 characters per line** (including spaces).
- **Line Count**: Maximum **2 lines** per subtitle event.
- **Visual Balance**: Prefer bottom-heavy two-liners (Line 2 longer than Line 1). Avoid leaving a single orphaned word on the second line.
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
  - One speaker per line (maximum 2 speakers).
  - Each line must be a self-contained sentence.

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
  - At 24 fps, gaps of 3–11 frames should be closed to 2 frames (chaining), or left as $\ge$ 1/2 second (12+ frames) to prevent perceptual flashing.
- **Audio Alignment**:
  - In-time: within 1–2 frames of speech onset.
  - Out-time: approx. 1/2 second after speech ends (if not immediately followed by another subtitle).
  - Respect scene/shot cuts: avoid extending a subtitle across a shot change unless dialogue continues over the cut.

---

### 4. Punctuation & Typography (علامات الترقيم والطباعة)
- **Ellipsis (علامة الحذف)**:
  - Always use the single Unicode character `…` (`U+2026`), never three individual periods (`...`).
  - Use for trailing off speech, significant pauses ($\ge$ 2 seconds), or interrupted sentences.
  - Do **not** place ellipses or hyphens across subtitle splits if a sentence simply continues naturally.
- **Punctuation Attachment**:
  - No space before commas (،), question marks (؟), exclamation marks (!), or colons (:).
  - Never combine question and exclamation marks (`؟!` or `!?`).
  - In Arabic lists, repeat the conjunction `و` instead of using serial commas (e.g., `المدونون والمترجمون والمحررون`).
- **Quotation Marks (علامات التنصيص)**:
  - Use straight double quotes (`"..."`).
  - Open at the start of the quotation and close at the end (do not repeat per subtitle event).
  - When prefixed with the definite article `ال`, join with a kashida: `الـ"برونكس"`.
  - Use quotes for book/movie titles, song titles, quoted text read aloud, and transliterated names in SDH tags.
- **URLs, Emails & Hashtags**:
  - Avoid raw Latin scripts. Transliterate or describe (e.g., use `وسم#` or `هاشتاغ`).
  - On-screen links can be referenced as: `على الموقع الظاهر على الشاشة`.

---

### 5. Numbers & Dates (الأرقام والتواريخ)
- **Numbers 1 to 10**: Write as words with correct Arabic gender agreement (e.g., `رجلين اثنين`, `خمس سيدات`).
- **Numbers 11 and above**: Write in Arabic-Indic or Western digits (e.g., `15`, `250`), unless part of an idiom or starting a sentence.
- **Ordinals**:
  - 1st to 9th: Write in words (`الموسم الأول`, `الحلقة الرابعة`).
  - 10th and above: Digits with kashida (`الـ21`).
- **Formatting**:
  - Thousands separator: comma (`1,234`).
  - Decimals: point with leading zero (`0.5`).
  - Percentages and currency symbols: write words out (`بالمئة`, `دولار`, `يورو`).
  - Time: 12-hour format with Arabic day-period markers (`صباحاً`, `مساءً`).
  - Calendar months: use Gregorian names standard in MSA (`يناير`, `أغسطس` rather than Levantine `آب`/`كانون`).
  - Units of measurement: convert imperial units to metric unless plot-relevant.

---

### 6. Diacritics (التشكيل وضبط الكلمات)
- Keep subtitles largely unvocalized to preserve reading speed.
- Apply diacritics **only** when ambiguity changes the meaning:
  - Shadda (e.g., `شابّ` vs `شابَ`).
  - Passive verb forms (بناء الفعل للمجهول) where context does not clarify it immediately.
  - Feminine plural nun (نون النسوة) or speaker's ya (ياء المتكلم).
- **Tanween Fatha (تنوين الفتح)**: Place the tanween on the letter preceding the alif (e.g., `كتابًا` rather than `كتاباً`) to ensure proper rendering across subtitle renderers and players.

---

### 7. Forced Narratives & Foreign Speech (النصوص الظاهرة واللغات الأجنبية)
- **On-Screen Text (Forced Narratives - FN)**:
  - Subtitle on-screen signs, letters, or inserts only if plot-relevant and not covered by dialogue.
  - Enclose in straight quotes: `"ممنوع الدخول"`.
  - Never combine dialogue and FN in the same subtitle event.
  - Time the subtitle to match the appearance and disappearance of the on-screen graphic.
- **Foreign Speech in Audio**:
  - Subtitle foreign dialogue only if the original viewer was intended to understand it.
  - In Arabic original productions, full foreign sentences receive subtitles; isolated greetings (`Hello`, `Merci`) do not.

---

### 8. SDH & Sound Descriptions (تسميات الصم وضعاف السمع)
- Enclose sound effects, ambient cues, and speaker tags in square brackets: `[زقزقة عصافير]`, `[صوت محرك سيارة]`.
- Use the indefinite grammatical form for sound descriptions.
- Keep SDH labels in Modern Standard Arabic, even when transcribing colloquial dialogue.
- Music / singing: place a musical note with surrounding spaces at the start and end of lyrics: `♪ ... ♪`.

---

## RTL & Technical Considerations (الجوانب التقنية واتجاه النص)

Arabic is a Right-to-Left (RTL) script. Keep the following technical aspects in mind:

- **Encoding**: Always save files in **UTF-8** (with or without BOM depending on player requirements; standard UTF-8 without BOM is preferred).
- **BiDi (Bidirectional) Punctuation Glitches**:
  - Trailing punctuation (like full stops, exclamation marks, or brackets) may mistakenly display on the wrong side in LTR-configured subtitle players.
  - Use the Unicode **Right-to-Left Mark (RLM)** (`U+200F`) before or after punctuation if your target video player experiences BiDi rendering bugs.
- **Font Rendering**:
  - When burning subtitles into video (hardsubbing), choose modern OpenType fonts that support standard Arabic ligatures and kerning (e.g., *Noto Sans Arabic*, *Arial*, *Geeza Pro*).
  - Ensure vertical line spacing is sufficient so that diacritics (harakat) do not overlap with the line above or below.

---

## Quality Control (QC) Checklist

Before exporting or delivering subtitles, verify:

- [ ] **Character limits**: No line exceeds 42 characters.
- [ ] **Line limits**: No event exceeds 2 lines.
- [ ] **Grammatical breaks**: Line splits do not break noun-adjective, verb-subject, or genitive pairings.
- [ ] **Reading speed**: CPS does not exceed 20 characters/sec for general dialogue.
- [ ] **Punctuation**: Unicode ellipsis `…` used; no standalone triple dots; no double punctuation (`؟!`).
- [ ] **Quotes & Kashida**: Quotes use straight double quotation marks; `الـ"..."` formatting verified.
- [ ] **Language consistency**: Modern Standard Arabic maintained throughout; no accidental dialect vocabulary.
- [ ] **Terminology**: Character names and technical terms spelled consistently.
- [ ] **Timing**: Minimum duration $\ge$ 5/6s, maximum duration $\le$ 7s, minimum gap $\ge$ 2 frames.
- [ ] **Dual speakers**: Hyphen-space format (`- `) applied to each speaker's line.

---

## References & Credits

- [Netflix Timed Text Style Guide: Arabic](https://partnerhelp.netflixstudios.com/hc/en-us/articles/215644587-Arabic-Timed-Text-Style-Guide)
- [Netflix General Timed Text Requirements](https://partnerhelp.netflixstudios.com/hc/en-us/articles/215758617)
- FAR Subtitling Quality Assessment Model (Functional, Acceptable, Readable)
