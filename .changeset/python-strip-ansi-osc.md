---
"@e2b/python-sdk": patch
---

fix(python-sdk): strip OSC escape sequences in build logs

`strip_ansi_escape_codes` now strips OSC sequences (`ESC ] ... ST`) while
preserving support for other ST-terminated control strings. Programs commonly
emit OSC sequences such as the set-terminal-title `\x1b]0;title\x07` and
hyperlinks `\x1b]8;;url\x07`, which previously leaked the string terminator and
payload into template build log messages on the Python side.
