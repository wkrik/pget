# pget - Feature and Function Inventory

---

# 🔐 CORE CONCEPT
A multi-vault, GPG-(AES256)backed, interactive password manager with:
- FULL Vault Lifecycle Management
  - Vault Manager
  - Structured Entry management 
  - Automated Backup system with auto-prune
- UI engine
- Navigation
- Search engine
- Clipboard integration (OSC52/SSH-safe)
- Password generator

---
# Features
* Full-screen UI
* GPG AES256 Encryption / Decryption
* Supported Fields: Title, ID, Secret (support auto-generator), Comments
* Multi-vault support
* Interactive vault selector
* Interactive Search Engine (single or multiple pattern queries supported)
* Password generator support (pwgen, openssh, /dev/urandom)
* Automatic backup system
* Auto-backup prune
* Detects decryption failures
* Hiddend Password Cursor 
* Dynamic window resizing
* WINCH signal handling
* On screen 
* Notification of Hidden / visible passwords
* List view format: Title | ID | ****** | Comments
* Secret masked unless visible
* Full entry popup
* Structured display:
* Additional Display delimiters for COMMENTS (split by |)
* Enhanced navigation: arrows, j, k, Home, End, PageUp, PageDown
* Wrap-around navigation
* Smart scrolling
* Mask (hidden) / unmask (open text) of passwords
* Copy Clipboard w/OSC52 (SSH-safe) - over remote sessions
* Ctrl-C protection
* Add Entry
* Modify Entry
* Delete Entry
* Interactive flow
* edit maste encryption file
* Interactive search
* On-demand Kill GPG agent (cache clearing)
* GPG TTY handling
* User variable control 
* Edge Case Handling
