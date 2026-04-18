# File-organizer

A Python CLI tool that automatically organizes files in a folder by type, date, or extension — with dry-run preview
undo
real-time watch mode
duplicate detection, and a rich terminal UI.

---

## Features

- **Organize by type** — Images, Videos, Documents, Audio, Code, Archives, and more
- **Organize by date** — Groups files into `YYYY/MM` folders by last modified date
- **Organize by extension** — Groups files into `JPG/`, `PDF/`, `MP4/` folders
- **Dry-run mode** — Preview exactly what will move before touching anything
- **Undo** — Reverse the last organize operation, file by file
- **Watch mode** — Auto-organize new files the moment they land in a folder
- **Duplicate detection** — SHA-256 content hashing finds identical files regardless of name
- **Config file** — Customize rules and folder names via `.organizer.json`
- **Conflict resolution** — Never overwrites; renames to `file (1).jpg` automatically
- **Rich terminal UI** — Colored output, progress bars, and preview tables

---

## Installation

```bash
git clone https://github.com/nits04/File-organizer.git
cd File-organizer/nits04-main/file-organizer
pip install -r requirements.txt
python main.py [directory] [options]
# Organize by file type (default)
python main.py ~/Downloads
---
Exmple
# Organize by date modified
python main.py ~/Downloads --by date

# Organize by file extension
python main.py ~/Downloads --by extension

# Preview without moving anything
python main.py ~/Downloads --dry-run

# Detect duplicates before organizing
python main.py ~/Downloads --duplicates

# Undo last operation
python main.py ~/Downloads --undo

# Watch and auto-organize in real time
python main.py ~/Downloads --watch

# Generate a config file
python main.py ~/Downloads --init-config


Downloads/
├── Images/
├── Videos/
├── Documents/
├── Audio/
├── Archives/
├── Code/
└── Others/

Downloads/
└── 2024/
    ├── 01/
    └── 03/

Downloads/
├── JPG/
├── PDF/
└── Others/

{
  "type_rules": {
    "Images": [".jpg", ".jpeg", ".png", ".gif"],
    "Videos": [".mp4", ".avi", ".mov"],
    "Documents": [".pdf", ".docx", ".txt"],
    "MyCustomFolder": [".sketch", ".fig"]
  },
  "ignored_files": [".ds_store", "thumbs.db"],
  "duplicate_action": "report",
  "others_folder": "Others",
  "date_format": "%Y/%m"
}
Tech Stack
Component	Library
CLI	argparse
Terminal UI	rich
File watching	watchdog
Hashing	hashlib (stdlib)
File ops	shutil, os, pathlib (stdlib)

pip install pytest
pytest tests/ -v

file-organizer/
├── main.py
├── organizer/
│   ├── rules.py
│   ├── config.py
│   ├── core.py
│   ├── duplicates.py
│   ├── undo.py
│   └── watcher.py
├── tests/
│   └── test_organizer.py
├── requirements.txt
└── setup.py

License
MIT
