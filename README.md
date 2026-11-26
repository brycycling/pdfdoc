# PDF Doc

Fill any PDF right in your browser. One self-contained HTML file: no server, no login, no build step, no AI. PDFs never leave the device.

The earlier React + Supabase version now lives in [brycycling/pdfformfill](https://github.com/brycycling/pdfformfill).

## Features

- **Fillable forms**: AcroForm fields are detected and you type straight onto the page (text, multi-line, checkboxes, radio buttons, dropdowns). Cryptic field names like `Text7` get their label from the words printed beside them.
- **Flat and scanned PDFs**: Text, Date, Check, Cross and Sign tools, in black or blue ink. Drag, resize, delete, undo and redo.
- **Profiles**: reusable details (name, MSP number, clinic address, phone, fax…) and a saved signature, either drawn or uploaded as an image. Uploads from a scan or phone photo get the paper background removed (with adjustable sensitivity) and can be recoloured to black or blue ink. *Apply profile* matches each detail to the right field by label, keeping patient fields separate. `{today}` expands to the current date in your chosen format.
- **Paste values**: paste `Label: value` lines and each is matched to the closest field. You review the matches before anything is applied. A blank template for the current form can be copied out.
- **Library**: save forms in the browser (IndexedDB), with entries or as blank templates.
- **Download**: saves the filled PDF, optionally flattened so answers can no longer be edited.

## Running it

Open `index.html` in a browser, or host it anywhere static (for example GitHub Pages). It loads two libraries from jsDelivr:

- [pdf.js](https://github.com/mozilla/pdf.js) 3.11.174 for rendering and field detection
- [pdf-lib](https://pdf-lib.js.org) 1.17.1 for writing the filled PDF

## Privacy

Everything runs locally: profiles and signature in localStorage, the library in IndexedDB. Nothing is uploaded; the only network requests load the two libraries above.

## Limitations

- Encrypted PDFs (common for government forms such as Service Canada's) are filled through pdf.js, which keeps the original encryption, fields and XFA data. If you also add text, marks or a signature, or choose Flatten, the download is a flattened copy: each page becomes an image with your entries drawn on top.
- Pure XFA (Adobe LiveCycle) forms with no regular form fields can't be filled as forms; write on them with the tools instead.
- Text and marks added on pages stored rotated inside the PDF may not line up.
- Added text uses Helvetica, so characters outside Western European sets are replaced.
