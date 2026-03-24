# Touch typing trainer

<div align="center">

**One file · Offline · No install**

Interface & word sets: **Russian · English · Spanish · Italian**

[English](README.md) · [Русский](README.ru.md)

</div>

---

## What it is

`index.html` is a **single-page** touch-typing (blind typing) trainer. Open it in a modern browser and practice immediately—no server and no extra assets.

Each round shows a phrase of **10–15 words** (space-separated) in one language. Optionally enable **digits and punctuation** to mix in 1–3 symbol-only chunks. You type character by character. The word list is **aligned across languages** (same meanings in RU, EN, ES, IT), so you can train in one language and peek at translations in the others. The on-screen keyboard matches the layout (**QWERTY** for EN/ES/IT, **JCUKEN / ЙЦУКЕН** for Russian) and highlights keys as you press them.

---

## Features

### Languages

| | |
| --- | --- |
| **Interface** | Full UI (labels, buttons, messages, table headers) in **Русский**, **English**, **Español**, **Italiano**. |
| **Word language** | Each round uses words in exactly one of the four languages. |
| **Sync** | Changing the interface language also sets the word language to match; you can override with the word-language controls. |
| **Persistence** | UI language is saved in `localStorage` (`bk_ui_lang`). On first visit, the app picks a sensible default from the browser language when possible. |

### Layouts

| Language group | Layout | Home-row bumps |
| --- | --- | --- |
| Russian | JCUKEN (ЙЦУКЕН) | **А** and **О** |
| English, Spanish, Italian | QWERTY (shared key map for ES/IT) | **F** and **J** |

### Hints while typing

| Action | What you get |
| --- | --- |
| **Desktop** | Hover a word → tooltip with translations in the *other* three languages. |
| **Touch** | Long-press (~0.5 s) on a word → same tooltip. |

Phrases are built from the shared dictionary: one semantic row → four translations.

### Statistics

| Area | Contents |
| --- | --- |
| **Session** (under practice) | Word count, character counts, correct / wrong keys, elapsed time. |
| **Global** (four cards) | Per language: attempts, total correct/wrong keystrokes, perfect vs flawed phrases. |
| **History** | Last **100** completed phrases: snippet, language, time, errors, result. |

All stats and history live in `localStorage` (`bk_typing_stats_v1`).

### Typing flow

- **Practice strip** — *done* (dimmed) · *current* (highlight) · *to do* (soft).
- **Focus** — If focus drifts away, the **first printable key** refocuses the practice area and counts as input.
- **Paste** — Pasting without focus moves focus to the practice area (paste is not applied as typed text).
- **New phrase** — Picks a new random phrase in the current word language.
- **Errors** — Short red flash; on-screen keys follow **keydown / keyup** globally.

---

## Technical notes

| Topic | Detail |
| --- | --- |
| **Bundle** | All HTML, CSS, JavaScript, and vocabulary are in **`index.html`**. |
| **Offline** | Works without network once the file is local. |
| **Storage** | `bk_ui_lang`, `bk_typing_stats_v1`; history capped at 100 rows. |
| **A11y** | Semantic markup, `aria-*`, `role="application"`, `aria-live` where appropriate. |

---

## Quick reference

| | |
| --- | --- |
| **Languages** | RU / EN / ES / IT — UI + training words |
| **Layouts** | JCUKEN (RU), QWERTY (EN·ES·IT) |
| **Phrase length** | 10–15 words (optional 1–3 symbol-only chunks) |
| **Translations** | Hover (desktop) or long-press (touch) on a word |
| **Run** | Open **`index.html`** in this folder (or serve the **`blind-keyboard/`** directory) in your browser |

---

*Play-A-Tool · Blind keyboard simulator*
