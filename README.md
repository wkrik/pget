## pget - Password Management tool

![Password Manager](https://img.shields.io/badge/Type-Password%20Manager-darkred) ![Passwords](https://img.shields.io/badge/Passwords-Encrypted-critical) ![Secrets](https://img.shields.io/badge/Secrets-Protected-success) ![Vault](https://img.shields.io/badge/Vault-GPG%20Encrypted-red)  ![Shell](https://img.shields.io/badge/Shell-POSIX%20sh-black) ![Linux](https://img.shields.io/badge/Platform-Linux-darkgreen) ![Encryption](https://img.shields.io/badge/Encryption-GPG%20AES256-red) ![Security](https://img.shields.io/badge/Security-Local%20Vault-critical) ![Terminal](https://img.shields.io/badge/UI-Terminal-lightgrey)
![No Cloud](https://img.shields.io/badge/Cloud-None-success) ![WSL](https://img.shields.io/badge/WSL-supported-blue?logo=linux&logoColor=white)

**pget** is a feature rich interactive Linux CLI bash based Password Management tool using GPG-(AES256) backed encryption. Runs on on **Debian** (Kali, Ubuntu, Linux Mint, Zoran, etc); **Fedora** (Redhat, AlmaLinux Rocky Linux, etc); **WSL** (Windows Subsystem for Linux).

### Watch the short demo:
<p align="left">
  <a href="https://www.youtube.com/watch?v=_Mkx6ab1hAk" target=pget>
    <img src="https://img.youtube.com/vi/_Mkx6ab1hAk/maxresdefault.jpg" height=280>
  </a>
</p>

<a href=./gallery><b>VIEW THE IMAGE GALLERY</b></font></a>

---
## Security Model Overview
The following is a security-focused comparison between pget and a typical cloud-based password management tools. 
<p>

| Security Area | pget | Cloud Password Manager |
| --- | --- | --- |
| Data location | 🟢 Local encrypted vault only | 🔴 Remote cloud vault |
| Network exposure | 🟢 None required | 🔴 Internet-connected service |
| Server breach risk | 🟢 No central server to breach | 🔴 Vendor infrastructure can be targeted |
| Vendor trust | 🟢 No vendor required | 🟡 Must trust provider and platform |
| Encryption model | 🟢 GPG symmetric encryption | 🟢 Vendor-managed strong encryption |
| Offline use | 🟢 Fully offline | 🟡 Often limited or cached |
| Account takeover risk | 🟢 No online account | 🔴 Online account can be attacked |

**Read the full** <a href=./SECURITY_Review.md><b>Security Review</b></a>. 

---
## Features

* FULL Vault Lifecycle Management
  - Vault Manager
  - Multi-vault support
  - Structured Entry management 
  - Automated Backup system with auto-retention
* Full screen UI engine
* Interactive Search Engine (single or multiple pattern queries supported)
* Clipboard integration (OSC52/SSH-safe) over remote sessions
* Password generator support (pwgen, openssh, /dev/urandom)
* GPG AES256 Encryption / Decryption
* GPG TTY handling
* Supported Fields: Title, ID, Secret (support auto-generator), Comments
* Multi-vault support
* Interactive vault selector
* Detects decryption failures
* Hiddend Password Cursor 
* Dynamic window resizing
* WINCH signal handling
* On screen 
* Notification of Hidden / visible passwords
* List view format: Title | ID | ****** | Comments
* Secret masked unless visible
* Full entry viewing
* Structured display:
* Additional Display delimiters for COMMENTS (split by |)
* Enhanced navigation: arrows, j, k, Home, End, PageUp, PageDown
* Smart scrolling
* Mask (hidden) / unmask (open text) of passwords
* Ctrl-C protection
* Add Entry
* Modify Entry
* Delete Entry
* Interactive flow
* edit maste encryption file
* Interactive search
* On-demand Kill GPG agent (cache clearing)
* User variable control 
* Edge Case Handling

---
## Download
There are 3 methods for downloading from your local linux based device:

**git**:
```
$ git clone https://github.com/wkrik/pget
```
**curl or wget**: Extract the **zip'd tar file**
```
$ wget https://github.com/wkrik/pget/releases/download/v2.138/pget-v2.138.tz
$ curl -O https://github.com/wkrik/pget/releases/download/v2.138/pget-v2.138.tz

$ tar xvzf pget-v2.138.tz
```
**Web browser**: Go to the URL
```
https://github.com/wkrik/pget/releases/download/v2.138/pget-v2.138.tz
```

---

## Installation

There are 2 installations methods that can be used: Automated and Manual.

### Automated: The easiest method
Run the provided script in the pget directory:
```
$ ./setup_pget
```

Your done. Scroll down to testing and launching.

### Manual: 5 simple steps

**1.  Install the prerequisites:**

 - **Note:** pwgen (password generator) is optional. Two other methods can be used to generate a password in pget: openssl, and urandom. It is set ($PWGEN) in the main pget script.

Debian (ubuntu, Linux Mint, Kali, ...):
```
	$ sudo apt install vim vim-runtime gnupg pwgen
```

Fedora (RedHat, AlmaLinux, Rocky Linux, ...):
```
	$ sudo dnf install vim vim-enhanced gnupg pwgen pinentry pinentry-curses
```
 - **Note:** Some version of Fedora require the epel-release package be installed for pwgen. 

**2.  Go to the parent directory of pget:**
    
```
	$ cd /path/to/parent  
	$ ls pget/
```

**3.  Append the vimrc plugin configurations to ~/.vimrc:**
    
```
$ cat pget/vimrc.conf >> ~/.vimrc
```

    
**4.  Copy pget into /opt**
	If /opt does not exist, 
```
$ sudo mkdir -p /opt
```
    
```
$ sudo cp -r pget /opt/
```
    
**5.  Link path to executable***
    
```
$ sudo ln -s /opt/pget/pget /usr/local/bin/pget
```

That's it!

---

## Test Installation:
**1. Test vim encryption**
```
$ vim test.gpg
This is a test
:wq
```
   
You should be prompted for a passphrase.

**2. Verify AES256 encryption, and the file can be decrypted:**

To confirm it is AES256 encrypted:
   ```
$ gpg --list-packets test.gpg 2>&1 | grep 'encrypted data'
```

To confirm the file can be decrypted:
```
   $ gpg -d test.gpg
```

## Launch pget
pget will go through a first time launch process.
```
   $ ./pget
```

Each time afer, use a search pattern
```
   $ ./pget pattern
```

Usage:
```
$ pget [-v vault_name] [-E | -l | -x | --help] pattern
```
| Argument | Description |
| ----- | -----|
| -v | vault to connect to |
| -E | Edit encrypted vault |
| -l | List available vaults |
| -x  | Kill gpg-agent cache for all vaults (force password) | 
| --help | Displays help page |
| --version | get current version number | 
| pattern | Pattern to search, use " " for multiple patterns to search |

## Project Goals
pget was originally started in 2002 as a personal password management tool and evolved over time into a hardened interactive CLI vault manager focused on privacy, portability, and terminal efficiency. New Features and cosmetic updates are in the works.

Built for Linux users, terminal enthusiasts, system administrators, privacy advocates, and cybersecurity professionals.

## Support

First check out he <a href=/docs/Troubleshooting.md>Troubleshoot</a> guide.

Use the Discussion Group for any comments, questions, and feature requests, or Issues to report any issues.
