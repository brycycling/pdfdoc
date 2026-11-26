# Form Desk

Fill any PDF right in your browser. One self-contained HTML file: no server, no login, no build step. PDFs never leave the device unless you use Smart fill.

The earlier React + Supabase version now lives in [brycycling/pdfformfill](https://github.com/brycycling/pdfformfill).

## Features

- **Fillable forms**: AcroForm fields are detected and you type straight onto the page (text, multi-line, checkboxes, radio buttons, dropdowns). Cryptic field names like `Text7` get their label from the words printed beside them.
- **Flat and scanned PDFs**: Text, Date, Check, Cross and Sign tools, in black or blue ink. Drag, resize, delete, undo and redo.
- **Profiles**: reusable details (name, MSP number, clinic address, phone, fax…) and a saved signature. *Apply profile* matches each detail to the right field by label, keeping patient fields separate. `{today}` expands to the current date in your chosen format.
- **Smart fill**: paste a referral or notes and Claude suggests values for each field. You review and edit before anything is applied. Without Claude, plain `Label: value` lines can be matched locally.
- **Library**: save forms in the browser (IndexedDB), with entries or as blank templates.
- **Download**: saves the filled PDF, optionally flattened so answers can no longer be edited.

## Running it

Open `index.html` in a browser, or host it anywhere static (for example GitHub Pages). It loads two libraries from jsDelivr:

- [pdf.js](https://github.com/mozilla/pdf.js) 3.11.174 for rendering and field detection
- [pdf-lib](https://pdf-lib.js.org) 1.17.1 for writing the filled PDF

Inside Claude (published as an artifact), Smart fill and downloads use Claude's built-in capabilities. Hosted elsewhere, Smart fill needs an Anthropic API key, entered under *Smart fill → Use Smart fill outside Claude*. The key is stored only in that browser's localStorage and sent only to `api.anthropic.com`.

## Privacy

Everything runs locally: profiles and signature in localStorage, the library in IndexedDB. Smart fill is the only feature that sends data anywhere: the pasted text and the form's field labels go to Claude. Check your organization's privacy rules before using it with identifiable patient information.

## Limitations

- XFA (Adobe LiveCycle) forms can't be filled as forms; write on them with the tools instead.
- Text and marks added on pages stored rotated inside the PDF may not line up.
- Added text uses Helvetica, so characters outside Western European sets are replaced.
