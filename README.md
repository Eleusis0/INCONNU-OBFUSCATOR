# INCONNU Obfuscator

```
██╗███╗   ██╗ ██████╗ ██████╗ ███╗   ██╗███╗   ██╗██╗   ██╗
██║████╗  ██║██╔════╝██╔═══██╗████╗  ██║████╗  ██║██║   ██║
██║██╔██╗ ██║██║     ██║   ██║██╔██╗ ██║██╔██╗ ██║██║   ██║
██║██║╚██╗██║██║     ██║   ██║██║╚██╗██║██║╚██╗██║██║   ██║
██║██║ ╚████║╚██████╗╚██████╔╝██║ ╚████║██║ ╚████║╚██████╔╝
╚═╝╚═╝  ╚═══╝ ╚═════╝ ╚═════╝ ╚═╝  ╚═══╝╚═╝  ╚═══╝ ╚═════╝
                  O B F U S C A T O R  v1.0.0
```

> **Made by inconnu boy** | GitHub: [INCONNU-BOY](https://github.com/INCONNU-BOY)
> **Made by inconnu boy** : [SITE LIVE DÉMO](https://obfuscator-virid.vercel.app)

A powerful, zero-dependency HTML & JavaScript obfuscator built on pure Node.js. Protects your source code with multiple layers of obfuscation that are highly resistant to AI-based and online deobfuscators.

---

## Features

| Feature | Description |
|---|---|
| **Variable Renaming** | All variable and function names replaced with random hex identifiers |
| **String Array Encoding** | All strings extracted, hex-encoded, shuffled, and stored in a rotated array |
| **Number Obfuscation** | Numbers replaced with arithmetic expressions `(n+offset)-offset` |
| **Property Encoding** | Dot notation encoded to Unicode bracket notation `obj['\u0070\u0072\u006f\u0070']` |
| **Dead Code Injection** | Fake variables and junk logic injected throughout |
| **IIFE Wrapping** | Entire code wrapped in an immediately-invoked function expression |
| **Smart Comment Stripper** | Strips comments without breaking URLs like `https://` |
| **Anti-Debug** | Injects debugger traps and DevTools detection |
| **Anti-Copy** | Disables right-click, F12, Ctrl+U/S/A/C |
| **HTML Support** | Obfuscates inline `<script>` and `<style>` tags, injects junk comments |
| **Junk HTML Comments** | Random fake build metadata comments injected between tags |
| **INCONNU Signature** | Base64-encoded signature embedded in output |

---

## Requirements

- Node.js v14+ (no external dependencies)

---

## Installation

```bash
git clone https://github.com/INCONNU-BOY/inconnu-obfuscator
cd inconnu-obfuscator
```

No `npm install` needed — zero dependencies.

---

## CLI Usage

### Obfuscate a JavaScript file
```bash
node index.js script.js
# Output: script.obf.js

node index.js script.js output/script.obf.js
```

### Obfuscate an HTML file
```bash
node index.js index.html
# Output: index.obf.html

node index.js index.html output/index.obf.html
```

### Obfuscate an entire folder
```bash
node index.js ./my-project/ ./obfuscated/
```

### With protection flags
```bash
# All protections enabled
node index.js index.html output.html --anti-debug --anti-copy --wrap-body

# Minimal obfuscation (strings + rename only)
node index.js script.js --no-numbers --no-dead-code
```

---

## Options

| Flag | Description |
|---|---|
| `--anti-debug` | Inject `debugger` trap with DevTools timing detection |
| `--anti-copy` | Disable right-click, Ctrl+U/S/A/C, F12 |
| `--wrap-body` | Encode HTML body content in Base64 + `document.write` (HTML only) |
| `--no-strings` | Skip string array obfuscation |
| `--no-numbers` | Skip number obfuscation |
| `--no-rename` | Skip variable renaming |
| `--no-dead-code` | Skip dead code injection |
| `--help` / `-h` | Show help |

---

## GUI (Browser Interface)

Open `inconnu/inconnu.html` in your browser for a full visual interface:

- Paste JS or HTML code directly
- Toggle obfuscation options with checkboxes
- Upload `.js` / `.html` files via drag & drop
- Download obfuscated output with one click
- Live terminal log console

> No server required — runs entirely in the browser.

---

## Obfuscation Pipeline

```
Input Code
    │
    ▼
[1] Smart Comment Strip     (preserves URLs like https://)
    │
    ▼
[2] Whitespace Collapse     (outside strings only)
    │
    ▼
[3] Variable Rename         (hex identifiers, skips string contents)
    │
    ▼
[4] String Array Encoding   (hex encode → shuffle → rotate → decoder fn)
    │
    ▼
[5] Number Obfuscation      (42 → (343-301))
    │
    ▼
[6] Property Encoding       (.log → ['\u006c\u006f\u0067'])
    │
    ▼
[7] Dead Code Injection      (junk vars, false conditions)
    │
    ▼
[8] IIFE Wrap               (;(function(_0x...,_0x...){...})(this,...))
    │
    ▼
Output — Obfuscated Code
```

---

## Programmatic API

```js
const { obfuscateJS }   = require('./src/js-obfuscator');
const { obfuscateHTML } = require('./src/html-obfuscator');

// JavaScript
const result = obfuscateJS(sourceCode, {
  renameVars:          true,
  obfuscateStrings:    true,
  obfuscateNumbers:    true,
  obfuscateProperties: true,
  deadCode:            true,
  antiDebug:           false,
  antiCopy:            false,
});

// HTML
const result = obfuscateHTML(htmlSource, {
  obfuscateScripts:   true,
  obfuscateStyles:    true,
  insertJunkComments: true,
  antiDebug:          false,
  antiCopy:           false,
  wrapBody:           false,
});
```

---

## Project Structure

```
inconnu-obfuscator/
├── index.js              ← CLI entry point
├── src/
│   ├── js-obfuscator.js  ← JavaScript obfuscation engine
│   └── html-obfuscator.js← HTML obfuscation engine
├── inconnu/
│   └── inconnu.html        ← Browser-based GUI
├── test-files/
│   ├── test.js           ← Sample JS for testing
│   └── test.html         ← Sample HTML for testing
├── output/               ← Generated output files
├── test.js               ← Full test suite (23 tests)
├── package.json
└── README.md
```

---

## Run Tests

```bash
node test.js
```

Expected: **23/23 tests passed**

---

## License

MIT — Made by **inconnu boy** | [INCONNU-BOY](https://github.com/INCONNU-BOY)
