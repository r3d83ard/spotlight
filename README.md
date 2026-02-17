# G Code (Macro B) Syntax Highlighting for VS Code

This extension adds syntax highlighting for Fanuc-style G Code Macro B and registers all `.nc` files as `G Code`.

It highlights:

- Comments: `; ...` and `( ... )`
- G codes: `G0`, `G1`, `G65`, etc.
- M codes: `M3`, `M30`, `M98`, etc.
- Sub programs: `O1234` and `M98 P1234` style calls
- Sub macros: `O9xxx` and `G65/G66 Pxxxx` style calls
- Variables: `#1`, `#500`, `#<name>`, `#[expr]`
- Sequence numbers: `N10`, `N20`, etc. (separate from G/M codes)
- Conditionals/control flow: `IF`, `THEN`, `WHILE`, `DO`, `END`, `GOTO`, etc.
- Brackets: `[` and `]`
- Parentheses: `(` and `)` delimiters

The language name in VS Code is exactly: `G Code`.

## Install in VS Code

### Option 1: Run it directly in Extension Development Host

1. Open this folder in VS Code.
2. Run:

```bash
npm install
```

3. Press `F5` (Run Extension).
4. In the new VS Code window, open any `.nc` file.
5. Confirm language mode (bottom-right) is `G Code`.

### Option 2: Package and install as a `.vsix`

1. From this folder, run:

```bash
npx @vscode/vsce package
```

2. Install the generated `.vsix`:

```bash
code --install-extension g-code-macro-b-0.0.1.vsix
```

3. Reload VS Code.

## Guaranteed Distinct G/M/N Colors

To force distinct colors for G codes, M codes, N sequence numbers, and control flow keywords, select the bundled theme:

1. Open Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`)
2. Run `Preferences: Color Theme`
3. Choose `G Code Tokyo Night Pro`

## Force all `.nc` files to `G Code` (if another extension conflicts)

Add this to your VS Code `settings.json`:

```json
{
  "files.associations": {
    "*.nc": "gcode"
  }
}
```

## Troubleshooting

- If a `.nc` file opens as another language (for example `NCCode`), click the language mode in the bottom-right status bar and switch it to `G Code`.
- Keep this in `settings.json` to make it stick:

```json
{
  "files.associations": {
    "*.nc": "gcode"
  }
}
```

## Theme Notes

The grammar uses explicit G Code scopes, and the bundled `G Code Tokyo Night Pro` theme adds dedicated color rules so G, M, and N tokens are always distinct.
