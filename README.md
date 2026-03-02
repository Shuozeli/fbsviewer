# FlatBuffers Binary Visualizer

An interactive browser-based tool for inspecting
[FlatBuffers](https://flatbuffers.dev/) binary encodings. Paste a `.fbs`
schema and hex-encoded binary data to see exactly how the bytes map to
tables, structs, strings, vectors, and unions.

**Try it now: [fbsviewer.shuozeli.com](https://fbsviewer.shuozeli.com/)**

**Source code: [Shuozeli/fbsviewer-lib](https://github.com/Shuozeli/fbsviewer-lib)**

## Features

**Schema compilation in the browser** -- The full FlatBuffers schema compiler
runs client-side as WebAssembly. Paste any `.fbs` schema and it compiles
instantly. No server round-trips.

**Color-coded hex view** -- Every byte in the binary is color-coded by the
region it belongs to (vtable, table fields, strings, vectors, structs, etc.).
Hover over any byte to see which field it corresponds to.

**Structure tree** -- A collapsible tree on the right shows the decoded
structure: root table, nested tables, structs, vectors, strings, unions, and
enums. Hover over a tree node to highlight the corresponding bytes in the hex
view.

**Click-to-lock highlighting** -- Click on any region in the hex view or
structure tree to lock the highlight. Click again to unlock. Locked
highlights persist while you hover over other regions.

**Decoded JSON** -- Toggle the JSON view to see the fully decoded output
of the binary data, reconstructed from the raw bytes using the schema.

**Compiled schema JSON** -- View the intermediate compiled schema
representation to understand how the compiler interpreted your `.fbs` input.

**Built-in examples** -- Choose from built-in templates to explore different
FlatBuffers features:

| Template | Features covered |
|---|---|
| Monster | struct, enum, string, vector of scalars |
| Simple Scalars | bool, int, float fields |
| Nested Structs | struct-in-struct, string, float |
| String Fields | multiple string fields, int |

**File upload** -- Upload `.fbs` schema files and binary data files directly
from disk (both native and WASM).

**Fully offline** -- Runs entirely client-side. No network requests, no
cookies, no local storage. Everything happens in the browser.

## Usage

1. Enter (or upload) a `.fbs` schema in the left panel
2. Enter hex-encoded binary data in the data panel, or select a built-in
   example from the dropdown
3. The hex view and structure tree update automatically
4. Hover over bytes or tree nodes to see cross-highlighted regions
5. Click to lock a highlight, click again to unlock
6. Toggle "Schema JSON" or "Decoded JSON" for additional views

## Self-hosting

This repository contains pre-built static files:

```
index.html                      HTML entry point
flatbuf-visualizer.js           JS glue (wasm-bindgen)
flatbuf-visualizer_bg.wasm      Compiled WASM binary (~3.5 MB)
```

Upload all three files to any static hosting provider, or preview locally:

```bash
python3 -m http.server 8080
# Open http://localhost:8080
```

No build step required. No server-side logic.

## Source

Built from [Shuozeli/fbsviewer-lib](https://github.com/Shuozeli/fbsviewer-lib).
Compiler: [Shuozeli/flatbuffers-rs](https://github.com/Shuozeli/flatbuffers-rs).

## License

[MIT](LICENSE)
