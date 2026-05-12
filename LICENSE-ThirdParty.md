**pget** is a lightweight Bash-based tool for retrieving and managing files, with optional automatic encryption using the Vim plugin vim-gnupg.

This project is designed to be simple, transparent, and easy to audit. All core functionality is implemented in bash shell scripts.

---

## 📦 Included Components

This distribution bundles the following third-party plugin:

### vim-gnupg
- License: GNU General Public License v2.0 (GPL-2.0)  - See: https://www.gnu.org/licenses/old-licenses/gpl-2.0.txt
- Copyright: James McCoy - https://github.com/jamessan/vim-gnupg/
- Source: Included in `plugins/vim-gnupg/`

vim-gnupg is **not modified** and is included for convenience. It remains a separate program under its original license.

---

## 🧩 License Relationship

This project distributes pget and vim-gnupg together as **separate programs**.

- pget does **not incorporate or link** vim-gnupg or gnupg code
- vim-gnupg are invoked as an external Vim plugin
- gnupg is invoked as an external call
- This distribution is considered **mere aggregation** under GPL terms

Each component retains its own license.

---

## ⚠️ Disclaimer

pget and vim-gnupg is free software is provided **as-is**, without warranty of any kind. 

---

