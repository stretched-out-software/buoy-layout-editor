# Buoy Layout Editor

A visual, WYSIWYG layout editor for **[Buoy](https://github.com/stretched-out-software/buoy-releases)** — design native UI windows by dragging controls onto a canvas, tweak their properties, and save them out as declarative Buoy source.

> **This is a community project.** It is an independent, community-driven effort to build a layout/form designer for Buoy. It is **not** an official Buoy product or release. The Buoy compiler itself lives in a separate repository: **https://github.com/stretched-out-software/buoy-releases**.

## What is Buoy?

Buoy is a modern programming language and framework for building native graphical user interfaces — windows, buttons, text fields, list boxes, and so on. UI in Buoy can be described declaratively, which makes it a natural fit for a visual editor that reads and writes that declarative form.

To build or run anything in this repository you need the Buoy compiler. Grab it from the releases repo: https://github.com/stretched-out-software/buoy-releases

## What this editor does

The Buoy Layout Editor is a three-panel form designer:

- **Control Library** (left) — a searchable palette of the built-in control types (Label, Button, TextField, TextArea, Checkbox, Slider, ProgressBar, ComboBox, ListBox, ImageView, Canvas, View, TabView, PagePanel). Double-click a control to add it to the canvas.
- **Design Canvas** (center) — the interactive surface where you place and arrange controls:
  - Drag to move, with snapping to an 8-pixel grid
  - Arrow keys for fine-grained nudging
  - Delete / Backspace to remove the selected control
  - Selection handles and a visual alignment grid
- **Property Editor** (right) — edit the selected control's properties: Name, Kind, X, Y, Width, Height, and Caption.

Layouts are saved to and loaded from declarative Buoy `Window` blocks (`.bui`), with the serializer designed for round-trip fidelity — saving a loaded file reproduces the same source.

## Project layout

The editor is written entirely in Buoy (`.bui`), organized into three modules under `src/`:

- **`src/layout-editor.bui`** — the main application. Defines the UI classes and `CreateEditorWindow()`, which assembles the three-panel interface.
- **`src/LayoutModel.bui`** — the UI-free data model (`ControlKind`, `DesignControl`, `EditorModel`), kept separate from the UI so it can be reasoned about and tested on its own.
- **`src/LayoutDocument.bui`** — serialization: `EmitWindow()` generates declarative layout source and `ParseWindow()` reads it back, preserving round-trip fidelity.

## Getting started

1. Install the Buoy compiler from the [releases repository](https://github.com/stretched-out-software/buoy-releases).
2. Clone this repository.
3. Build and run the editor sources in `src/` with the Buoy compiler.

There is no separate build configuration in this repository yet — the project is just the Buoy source under `src/`.

## Contributing

Contributions are welcome — this is a community project and there's plenty to build. Bug reports, feature ideas, and pull requests are all appreciated. If you're adding a feature, keeping UI-free logic in `LayoutModel.bui` / `LayoutDocument.bui` (separate from the UI in `layout-editor.bui`) helps keep things testable.

## License

This project is licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**. See the [LICENSE](LICENSE) file for the full text.
