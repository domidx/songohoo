# Songohoo 🎵

**Songohoo** is a browser-based app for creating and presenting song lyrics — designed for worship services, choir rehearsals, community singalongs, or any gathering where people sing together. It displays verses and refrains slide by slide on a big screen so everyone can follow along without printed sheets.

> *The name is a wordplay on "song" — **Songo**hoo.*

---

## 🤖 About this project

**Songohoo is fully coded by AI.** The project was developed through a conversational session with **Claude Sonnet 4.5** (Anthropic), based on a written assignment spec provided by the human author. No manual code was written — all HTML, CSS, and JavaScript was generated and iteratively refined by the model through natural language instructions.

The original assignment file is included in this repository as [`assignment.txt`](./assignment.txt) so you can see exactly what was specified and compare it to what was built.

**AI details:**
- **Model:** Claude Sonnet 4.5
- **Provider:** Anthropic
- **Interface:** claude.ai
- **Method:** Single long conversational session with iterative refinement

---

## ✨ Features

- **Single standalone file** — the entire app is one `songohoo.html` file. No installation, no internet connection, no external libraries or dependencies. Open it in any modern browser and it just works.
- **Song Editor** — create and edit songs with an arbitrary number of verses and refrains, saved as `.json` files locally.
- **Smart refrain handling** — type a refrain once; subsequent refrains can be left blank and Songohoo will automatically reuse the text when building the presentation.
- **Presentation mode** — fullscreen black/white slides with auto-fitting text, a song list slide between each song, and a coloured dot indicator showing which song is next.
- **Flexible slide layout** — configurable max lines per slide; verse and refrain are combined onto one slide when they fit, otherwise split automatically.
- **Logo support** — add a logo (JPG, PNG or SVG) displayed alongside the presentation title.
- **Export to HTML** — save the finished presentation as a fully self-contained HTML file with all lyrics and logo embedded, ready to present on any computer.
- **Keyboard navigation** — full keyboard control during presentation.
- **Persistent preferences** — divider colour and max lines per slide are remembered across sessions.
- **Help tab** — built-in usage guide, no need to refer to external documentation.

---

## 📁 Repository structure

```
songohoo.html        ← The entire application (open this in your browser)
assignment.txt       ← The original spec given to the AI
examples/
  1_AmazingGrace.json
  2_HowGreatThouArt.json
  3_BlestBeTheTie.json
  42_ShineJesusShine.json
  57_MightyToSave.json
README.md
```

---

## 🚀 Getting started

1. Download `songohoo.html` to your computer.
2. Open it in any modern web browser (Chrome, Firefox, Edge, Safari).
3. That's it — no setup required.

The example song files in the `examples/` folder can be loaded directly into the app to try it out straight away.

---

## 🎵 Song Editor

Songs are stored as `.json` files on your local filesystem, one file per song.

**Creating a song:**
1. Go to the **Song Editor** tab.
2. Enter an optional **Song Code** (e.g. a number from an existing songbook) and a **Song Title**.
3. Type each verse or refrain into the text areas. A new area appears automatically as you type.
4. Tick **Refrain** on a section to mark it as a refrain. For repeated refrains, tick the checkbox and leave the text empty — Songohoo reuses the first refrain's text automatically.
5. Click **💾 Save Song** and choose a location. The filename is generated from the code and title (e.g. `42_ShineJesusShine.json`).

**Editing a song:**
Click **📂 Open Song File**, select an existing `.json` file, make your changes, and save.

---

## 🎤 Presentation

**Setting up:**
1. Go to the **Presentation** tab.
2. Enter a **Presentation Title**.
3. Optionally select a **Logo** image.
4. Choose a **Divider Colour** and **Max Lines / Slide**.
5. Add songs using the **📂** button on each row. Optionally add a short description per song.

**Starting:**
Click **▶ Start Presentation**. The screen goes fullscreen.

**Slide structure:**
- Song List slide (dot on first song)
- Verses/refrains of Song 1
- Song List slide (dot on second song)
- Verses/refrains of Song 2
- … and so on
- Final Song List slide (no dot)

**Keyboard navigation:**

| Key | Action |
|-----|--------|
| `→` | Next slide |
| `←` | Previous slide |
| `→` *(hold)* | Jump to next Song List slide |
| `←` *(hold)* | Jump to previous Song List slide |
| `N` | Jump to next Song List slide |
| `P` | Jump to previous Song List slide |
| `Esc` / `Q` | Exit presentation |
| Click anywhere | Next slide |

**Saving:**
Click **💾 Save as HTML** to export a fully self-contained presentation file — all lyrics and the logo are embedded. Copy it to any computer and open in a browser to present.

---

## 🔧 Technical notes

- **Pure vanilla HTML/CSS/JS** — no frameworks, no build tools, no npm. The entire app is a single ~1,100 line file.
- **localStorage instead of cookies** — browser security blocks cookies for `file://` pages (i.e. locally opened HTML files). Preferences are stored using `localStorage` instead, which works reliably in this context.
- **SVG logo support** — SVG files are loaded via `FileReader.readAsDataURL()` and set on the image element via JavaScript (not injected through `innerHTML`) to avoid browser security restrictions on data URLs in HTML strings.
- **Song data format** — songs are plain JSON files with a `code`, `title`, and `sections` array, where each section has a `type` (`verse` or `refrain`) and `text`. Empty refrain text signals "repeat the first refrain".
- **Exported presentations** — the Save as HTML feature generates a minimal self-contained HTML file (separate from the editor) with all data embedded as JSON variables and a small runtime for navigation.

---

## 📄 Assignment vs. delivered

The app was built to closely follow the original [`assignment.txt`](./assignment.txt). Notable differences:

- **localStorage instead of cookies** — specified as cookies in the assignment; changed for technical reasons (see above).
- **Help tab** — not in the original spec; added during the session as an extra.
- **"Load song list" button** — was briefly implemented then removed, as browsers cannot programmatically re-open local files, making it impossible to fully restore a saved song list.

---

## 📜 Licence

This project is released as-is, free to use and modify.
