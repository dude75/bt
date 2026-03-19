# Touch Typing Trainer (Blind Keyboard)

A **single-file** touch typing (blind typing) trainer that runs entirely in the browser. No installation, no server: open the HTML file and start practicing. Supports **Russian**, **English**, **Spanish**, and **Italian** for both the interface and the word sets.

---

## Overview

The trainer shows a phrase of **5–10 words** in one language. You type the phrase character by character. The same words are available in all four languages as **aligned translations** (same meanings), so you can train in one language and see translations into the others. The on-screen keyboard reflects the chosen layout (QWERTY for EN/ES/IT, JCUKEN for Russian) and highlights keys as you press them.

---

## Functional Capabilities

### Multi-language support

- **Interface language**  
  The whole UI (labels, buttons, messages, table headers) can be switched between:
  - **Russian** (Русский)
  - **English**
  - **Spanish** (Español)
  - **Italian** (Italiano)

  The choice is stored in the browser (localStorage) so it persists across visits. On first load, the trainer tries to use the browser’s preferred language if it is one of the four above.

- **Word set (training language)**  
  Each round uses words in exactly one of the four languages:
  - **Russian** (Русские слова)
  - **English** (English words)
  - **Spanish** (Español)
  - **Italian** (Italiano)

  When you change the **interface language**, the **word language** is automatically set to the same one (e.g. switch to Spanish UI → Spanish words and Spanish keyboard layout). You can still change the word language manually with the “Word language” buttons.

- **Keyboard layouts**  
  - **Russian**: JCUKEN (ЙЦУКЕН).  
  - **English / Spanish / Italian**: QWERTY (same layout; ES/IT use the same key map).  
  The on-screen keyboard updates to match the selected word language. Home row bumps are shown on **F** and **J** (Russian: **А** and **О**).

---

### Translations while typing

- **Same meanings in all languages**  
  The word list is one aligned dictionary: each “row” is one meaning with translations in RU, EN, ES, IT. A phrase is built from 5–10 such words in the language you chose.

- **Word hints (translations)**  
  For every word in the current phrase you can see its translations into the other three languages:
  - **Desktop**: hover the mouse over the word. A tooltip appears with RU, EN, ES, IT (excluding the current training language).
  - **Touch**: long-press on the word (about 0.5 s). The same tooltip appears. Moving or releasing the finger cancels the long-press.

  So while you type, you can check the meaning in any of the four languages without leaving the page.

---

### Statistics

- **Session stats (during the round)**  
  Shown under the practice area:
  - Number of words in the phrase (5–10)
  - Total characters
  - Correct characters so far
  - Wrong key presses
  - Elapsed time (updates during typing; after finishing, shows the final time for that phrase)

- **Global statistics (per language)**  
  Below the keyboard, four cards (RU, EN, ES, IT) show aggregated data for completed phrases in that language:
  - Completed phrases (attempts)
  - Correct keystrokes (total)
  - Wrong keystrokes (total)
  - Phrases with no errors
  - Phrases with at least one error

- **History (last 100 attempts)**  
  A table lists the most recent completed phrases:
  - Phrase text (truncated if long; full text in tooltip)
  - Language (RU / EN / ES / IT)
  - Time taken
  - Number of errors
  - Result: “no errors” or “with errors”

  All statistics and history are stored in the browser (localStorage) and persist between sessions.

---

### Typing experience

- **Practice area**  
  A focusable block shows the current phrase. Characters are shown as:
  - **Done** (typed correctly, dimmed)
  - **Current** (next character, highlighted)
  - **To type** (upcoming, slightly faded)

- **Focus and input**  
  - If you click elsewhere and the practice area loses focus, **any keypress** (printable character) refocuses it and that key is applied to the phrase. So you can start typing immediately without clicking back.
  - **Paste**: if the practice area is not focused when you paste, it receives focus so the next action is in the right place (paste content is not processed as typed text).

- **New phrase**  
  “New phrase (5–10 words)” picks a new random phrase in the current word language and resets the round.

- **Feedback**  
  - Wrong key: short red flash on the practice area.  
  - On-screen keys highlight on keydown and clear on keyup (global), so you can see which key was pressed.

- **Completion**  
  When you type the last character, the round ends: a message shows whether the phrase was completed with or without errors and the time. Stats and history are updated; you can start a new phrase with the button.

---

## Technical details

- **Single file**  
  All HTML, CSS, JavaScript, and the word list are in one file (e.g. `blind-keyboard.html`). No external CSS, JS, or data files. Works offline.

- **Storage**  
  - Interface language: `localStorage` key `bk_ui_lang`.  
  - Statistics and history: `localStorage` key `bk_typing_stats_v1`.  
  History is limited to the last 100 entries.

- **Accessibility**  
  The practice area and controls use ARIA attributes and semantic structure (e.g. `role="application"`, `aria-label`, `aria-live`) for screen readers.

---

## Summary

| Feature | Description |
|--------|-------------|
| **Languages** | Interface and word sets: Russian, English, Spanish, Italian |
| **Layouts** | JCUKEN (RU), QWERTY (EN/ES/IT) |
| **Phrases** | 5–10 words per round, one language per round |
| **Translations** | Hover (desktop) or long-press (touch) on a word to see RU/EN/ES/IT |
| **Session stats** | Words, chars, correct, errors, time |
| **Global stats** | Per-language totals: attempts, correct/wrong keystrokes, perfect/flawed phrases |
| **History** | Last 100 completed phrases with language, time, errors |
| **Persistence** | UI language and all stats in localStorage |
| **Focus** | First keypress activates the practice area and counts as input |

Open `blind-keyboard.html` in a modern browser to use the trainer.
