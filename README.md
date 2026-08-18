# term

Terminal support for Olive. Raw mode, keyboard and mouse input, cursor control, clipboard, and flicker-free redraws.

## Install

```
pit add term
```

## Usage

```olive
import term

term.enable_raw()
term.enter_alt_screen()
term.cursor_move(0, 0)
term.write("hello")
term.flush()

let key = term.read_key()
if key == "ctrl+c":
    term.leave_alt_screen()
    term.disable_raw()
```

## Functions

| Function | Returns | What it does |
|----------|---------|--------------|
| `enable_raw()` | bool | Turn on raw mode |
| `disable_raw()` | bool | Turn off raw mode |
| `enter_alt_screen()` | bool | Switch to alternate screen |
| `leave_alt_screen()` | bool | Go back to normal screen |
| `clear()` | bool | Clear the screen |
| `cursor_hide()` | bool | Hide the cursor |
| `cursor_show()` | bool | Show the cursor |
| `cursor_move(x, y)` | bool | Move cursor to column x, row y (0-based) |
| `write(s)` | bool | Write a string with no newline |
| `flush()` | bool | Flush buffered output now |
| `begin_sync()` | bool | Start batching writes |
| `end_sync()` | bool | Stop batching and flush |
| `cols()` | int | Terminal width in columns |
| `rows()` | int | Terminal height in rows |
| `is_tty()` | bool | True if stdout is a real terminal |
| `enable_mouse()` | bool | Start receiving mouse events |
| `disable_mouse()` | bool | Stop receiving mouse events |
| `enable_key_enhancement()` | bool | Better key events (Kitty protocol) |
| `disable_key_enhancement()` | bool | Turn off enhanced key events |
| `clipboard_write(s)` | bool | Copy text to clipboard via OSC 52 |
| `read_key()` | str | Wait for the next key, mouse, or resize event |
| `read_key_timeout(ms)` | str | Same, but returns "idle" after ms milliseconds |

### Key names

`read_key` and `read_key_timeout` return strings like:

- Plain keys: `"a"`, `"enter"`, `"backspace"`, `"tab"`, `"escape"`
- Arrow keys: `"up"`, `"down"`, `"left"`, `"right"`
- With modifiers: `"ctrl+c"`, `"shift+up"`, `"ctrl+alt+delete"`
- Function keys: `"f1"` through `"f12"`
- Mouse: `"mousedown:10:3"`, `"mousedrag:10:3"`, `"mouseup:10:3"`, `"wheelup"`, `"wheeldown"`
- Special: `"resize"`, `"idle"`, `"eof"`

If you get `"eof"`, stop reading. It means input is closed and calling again will just keep returning `"eof"`.

## Building

```
cargo build --release
```

The output is `libolivetterm.so` (Linux), `libolivetterm.dylib` (macOS), or `olivetterm.dll` (Windows).
