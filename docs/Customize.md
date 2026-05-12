# Customize pget

The following **variables** can be changed in the top of the **pget** main script to your preference. If a pget update is performed, 
these will need to be changed again.
1. Where the vaults are stored 
2. Where backups are written
3. Set number of backups taken before recycles
4. Name of the "Default" vault
5. Set password generator.
6. Auto kill cache on exit
7. Display Settings
8. Color Themes

---

### 1. Where the vaults are stored: 
```
  vpath="$HOME/vault"
```

---

### 2. Where  backups are written:
```
  bpath="$vpath/backups"
```
  **Note:** *Backups are performed incase one fat-fingers a master password.*

---

### 3. Set number of backups taken before recycles:
```
  auto_prune=10
```

---

### 4. Name of the "Default" vault.
```
  vault_name="Primary"
```
---

### 5. Set password generator.
```
  #PWGEN="pwgen -s 15 1"
  #PWGEN="openssl rand -base64 15"
  PWGEN="head -c 15 /dev/urandom | base64"
 ``` 
  **Recommendation:** A 15 character Minimum is recommended:

---

### 6. Auto kill cache on exit
By default, GPG caches the passphrase for about 10 minutes after exiting pget.

Setting this to 1 kills the GPG agent on exit for improved security, but requires re-entering the password next time.
```
  AUTO_KILL_GPG_AGENT=0
```

---

### 7. Display Settings
While ths window frame auto-resizes, these settings
control display width and truncation behavior for
long entries.

  max_total=80
  win_size=20
  msg_row=0

---

### 8. Color Themes
Controls the foreground and background colors used in pget.
  
  Ascii Color Chart:<br>
  https://raw.githubusercontent.com/fidian/ansi/master/images/color-codes.png
  
```
  HIGHLIGHT_ON=$(tput setab 236 2>/dev/null || printf '\033[48;5;236m')
  HIGHLIGHT_OFF=$(tput sgr0 2>/dev/null || printf '\033[0m')
  HIGHLIGHT_FG=$(tput setaf 7 2>/dev/null || printf '\033[47m')
  VISABLE_BG=$(tput setab 88 2>/dev/null || printf '\033[48;5;88m')
  PATTERN_FONT_FG=$(tput setaf 6 2>/dev/null || printf '\033[36m')
  COPIED_BG=$(tput setab 2 2>/dev/null || printf '\033[42m')
  VAULT_FG=$(tput setaf 208 2>/dev/null || printf '\033[208m')
```
