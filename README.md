# term

Olive `term` package — raw-mode terminal, keyboard/mouse input, buffered output, and TUI primitives.

Exposes `olive_term_*` C-ABI symbols loaded by `pit` at runtime.

## Install

```
pit add term
```

## Symbols

| Symbol | Description |
|--------|-------------|
| `olive_term_enable_raw` / `olive_term_disable_raw` | Raw mode on/off |
| `olive_term_enter_alt_screen` / `olive_term_leave_alt_screen` | Alternate screen |
| `olive_term_clear` | Clear screen |
| `olive_term_cursor_hide` / `olive_term_cursor_show` | Cursor visibility |
| `olive_term_cursor_move(x, y)` | Move cursor |
| `olive_term_write(s)` | Write string without newline |
| `olive_term_flush` | Flush output buffer |
| `olive_term_begin_sync` / `olive_term_end_sync` | Synchronized output bracket (DECSET 2026) |
| `olive_term_cols` / `olive_term_rows` | Terminal dimensions |
| `olive_term_is_tty` | Is stdout a TTY? |
| `olive_term_enable_mouse` / `olive_term_disable_mouse` | SGR mouse tracking |
| `olive_term_enable_key_enhancement` / `olive_term_disable_key_enhancement` | Kitty keyboard protocol |
| `olive_term_read_key` | Block for next key/mouse/resize event |
| `olive_term_read_key_timeout(ms)` | Same with idle timeout |
| `olive_term_clipboard_write(s)` | Write to clipboard via OSC 52 |

## Building

```
cargo build --release
```
