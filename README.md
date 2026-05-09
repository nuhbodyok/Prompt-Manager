# Prompt Collection Tool

A self-contained, browser-based application for managing, organizing, and exporting AI prompt libraries. No backend, no installation — just save the HTML file and open it in any modern browser.

**[→ Live Demo](https://nuhbodyok.github.io/Prompt-Manager/)**
---

## Features

| Feature | Description |
|---------|-------------|
| **Create & Edit** | Add new prompts or edit existing ones with a dedicated modal editor |
| **Import** | Paste CSV or plain text, with auto-detection for common delimiters (`,`, `\|`, `;`, `	`) |
| **File Drop** | Drag-and-drop `.txt` or `.csv` files directly onto the drop zone |
| **Export** | Download your entire collection as a properly formatted CSV file |
| **Search** | Real-time, case-insensitive filtering by title or content |
| **Sort** | Alphabetical (A-Z / Z-A) or by import date |
| **Batch Operations** | Multi-select prompts via checkboxes and delete in bulk |
| **Duplicate Handling** | Smart conflict resolution — skip, overwrite, or auto-rename duplicates |
| **Format** | One-click cleanup that normalizes escape sequences (`\n` → newline, etc.) |
| **Deduplicate** | Remove prompts with identical titles (case-insensitive) |
| **Dark Mode** | Manual toggle + automatic system preference detection |
| **Keyboard Shortcuts** | `Ctrl+N` (new prompt), `Ctrl+F` (search), `Escape` (close modals) |
| **Persistent Storage** | All data saved to browser `localStorage` |
| **Accessibility** | ARIA roles, labels, and live regions for screen reader support |

---

## Quick Start

1. **Download** the HTML file to your computer.
2. **Open** it in any modern browser (Chrome, Firefox, Edge, Safari).
3. **Start collecting** — create prompts manually, paste CSV text, or drop files.

No server, no build step, no dependencies to install.

---

## Import Formats

### CSV
```csv
Title,Content
My Prompt,This is the prompt content
Another,"Content with ""quotes"" and commas, too"
```

### Pipe-delimited
```
Title|Content
My Prompt|This is the prompt content
```

### Plain Text (single file = single prompt)
When dropping a `.txt` file, the filename becomes the title and the file body becomes the content.

---

## CSV Export Format

Exported files follow standard CSV conventions:
- Fields containing delimiters, quotes, or newlines are wrapped in double quotes
- Internal quotes are doubled (`"` → `""`)
- Default delimiter: comma (configurable)

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + N` | Create new prompt |
| `Ctrl + F` | Focus search box |
| `Escape` | Close any open modal/dialog |

---

## Data Storage

All prompts are stored in your browser's `localStorage` under the key `promptCollectionData`.

- **Limit**: Approximately 5–10 MB total (browser-dependent).
- **Privacy**: Data never leaves your device — no cloud sync, no external API calls.
- **Backup**: Use the **Export** button regularly to create CSV backups.

---

## Browser Compatibility

| Browser | Version | Notes |
|---------|---------|-------|
| Chrome | 90+ | Full support |
| Firefox | 88+ | Full support |
| Edge | 90+ | Full support |
| Safari | 14+ | Full support |

Requires JavaScript enabled. No IE support.

---

## File Structure

```
prompt_collection_tool.html    ← Single self-contained file
├── Tailwind CSS (CDN)
├── Font Awesome icons (CDN)
├── All application logic (inline JS)
└── All styles (inline CSS)
```

---

## Technical Details

### Built With
- **Tailwind CSS** — utility-first styling
- **Font Awesome 6** — iconography
- **Vanilla JavaScript** — no frameworks, no build tools

### Key Design Decisions
- **No build step** — edit the HTML directly; changes are immediate.
- **No external state** — everything lives in `localStorage` for simplicity.
- **Inline everything** — works offline once loaded.

### Security Considerations
- All user-generated content is HTML-escaped before DOM insertion (XSS prevention).
- File uploads are processed client-side only; no server interaction.
- Regex patterns are sanitized to prevent ReDoS from malicious delimiter input.

---

## Limitations

- **No cloud sync** — data is local to one browser on one device.
- **No collaborative editing** — single-user only.
- **Large files** — individual prompts and uploaded files are capped at ~100 KB to prevent storage overflow.
- **CSV parsing** — extremely complex quoted CSV edge cases (nested quotes, multi-line fields with mixed quoting) may require manual cleanup.

---

## License

This is a standalone utility tool. Use, modify, and distribute freely.

---

## Changelog

### v1.1 (Fixed)
- Fixed critical syntax error in HTML entity escaping
- Added regex delimiter sanitization for CSV parsing
- Improved CSV quote handling (`""` → `"`)
- Added manual dark mode toggle
- Added ARIA roles and labels for accessibility
- Fixed file `accept` attribute MIME types
- Added Escape-key dismissal for duplicate conflict dialog
- Added `sr-only` utility class for screen-reader labels

### v1.0 (Original)
- Initial release with core CRUD, import/export, and sorting features.
