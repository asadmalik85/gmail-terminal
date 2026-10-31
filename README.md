# Gmail Terminal Client (`gmail-tui`)

A lightweight, keyboard-driven Gmail client and headless automation CLI for the terminal, built using Python's standard library with zero external dependencies.

---

## 1. Interactive Terminal UI Mode

Run `gmail` with no arguments to launch the curses interface:
```bash
gmail
```

### Keybindings

#### List View
- `Enter` / `o`: Open & read email
- `c`: Compose new email
- `r`: Reply to selected email
- `R`: Refresh mailbox
- `u`: Toggle Read / Unread
- `s`: Toggle Star / Flag
- `d`: Move email to Trash
- `f` / `Tab`: Open folders menu
- `/`: Search & filter
- `?`: Help modal
- `q` / `Esc`: Quit

#### Reader View
- `r`: Reply to current email
- `c`: Compose new email
- `j` / `k` (or `Down` / `Up`): Scroll through email
- `PgUp` / `PgDn`: Fast scroll
- `u`: Mark as unread
- `s`: Toggle star
- `d`: Move to Trash
- `q` / `Esc` / `b`: Back to mailbox list

#### Compose & Reply View
- `Tab` / `Ctrl+N`: Advance to next field (`To` -> `Subject` -> `Body`)
- `Shift+Tab` / `Ctrl+P`: Move to previous field
- `Ctrl+S` / `Ctrl+D` / `F10`: Send email
- `Ctrl+E`: Open draft in external `$EDITOR` (e.g. `nvim`)
- `Esc` / `Ctrl+Q`: Cancel / discard draft

---

## 2. Headless CLI Mode (Automation & Scripting)

You can inspect, read, send, and reply to emails headlessly from bash scripts, cron jobs, or AI agents:

### List Unread Emails
```bash
gmail --unread
gmail --unread --json
```

### List Recent Emails in a Folder
```bash
gmail --list --limit 10
gmail --list --folder "INBOX" --json
```

### Read an Email by ID
```bash
gmail --read 2
gmail --read 2 --json
```

### Reply to an Email by ID
```bash
gmail --reply 2 --body "Thanks! We will deploy on Monday."
# Read body from standard input:
cat message.txt | gmail --reply 2 --body -
# Reply without quoting original email:
gmail --reply 2 --body "Acknowledged." --no-quote
```

### Send a New Email
```bash
gmail --send --to "recipient@example.com" --subject "Status Update" --body "Everything is running smoothly."
# With JSON output:
gmail --send --to "recipient@example.com" --subject "Report" --body - --json < report.txt
```

### Mark Read / Trash
```bash
gmail --mark-read 2
gmail --trash 5
```

### Demo Mode
Test any command without live credentials:
```bash
gmail --demo --unread --json
gmail --demo --reply 2 --body "Test reply"
```
