## Important Note

No password manager can fully protect secrets if the device itself accessing the passwords (local or in the cloud) is compromised. Malware, remote access tools, keyloggers, screen capture tools, and clipboard monitors can compromise both local and cloud-based password managers.

**The following is a security-focused comparison between pget, a local GPG-backed terminal password manager, and typical cloud-based password management tools**

* * *

| Marker | Meaning |
| --- | --- |
| 🟢  | Lower risk / stronger control |
| 🟡  | Moderate risk / depends on configuration or user behavior |
| 🔴  | Higher risk / larger exposure |
| ⚪   | Not applicable |

## Security Model Overview

| Security Area | pget | Cloud Password Manager |
| --- | --- | --- |
| Data location | 🟢 Local encrypted vault only | 🔴 Remote cloud vault |
| Network exposure | 🟢 None required | 🔴 Internet-connected service |
| Server breach risk | 🟢 No central server to breach | 🔴 Vendor infrastructure can be targeted |
| Vendor trust | 🟢 No vendor required | 🟡 Must trust provider and platform |
| Encryption model | 🟢 GPG symmetric encryption | 🟢 Vendor-managed strong encryption |
| Offline use | 🟢 Fully offline | 🟡 Often limited or cached |
| Account takeover risk | 🟢 No online account | 🔴 Online account can be attacked |

* * *

## Session and Unlock Behavior

| Security Area | pget | Cloud Password Manager |
| --- | --- | --- |
| Passphrase caching | 🟢 User controlled through GPG agent | 🟡 App/browser session controlled |
| Auto-lock on exit | 🟢 Optional auto-kill of GPG agent | 🟡 Timeout or app lock dependent |
| Manual lock | 🟢 `pget -x` or interactive `x` | 🟡 App-specific |
| Reuse of unlocked session | 🟢 Low when auto-kill is enabled | 🟡 Session/token dependent |
| Walk-away risk | 🟡 Low to medium | 🟡 Low to medium |

* * *

## Attack Surface

| Security Area | pget | Cloud Password Manager |
| --- | --- | --- |
| Browser extension exposure | 🟢 None | 🔴 Common attack surface |
| Web app exposure | 🟢 None | 🔴 Web app can be targeted |
| API/backend exposure | 🟢 None | 🔴 Provider backend exists |
| Supply-chain risk | 🟡 Local OS/tools only | 🔴 App, extension, backend, vendor updates |
| Large-scale breach risk | 🟢 Very low | 🔴 Higher because cloud vaults are high-value targets |

* * *

## Secret Handling

| Security Area | pget | Cloud Password Manager |
| --- | --- | --- |
| Clipboard exposure | 🔴 Manual copy can leave secrets in clipboard | 🟡 Often has clipboard timeout features |
| Autofill phishing risk | 🟢 No autofill | 🔴 Autofill can be abused by fake sites |
| Screen exposure | 🔴 Visible when shown | 🔴 Visible when shown |
| Memory exposure | 🔴 Exists in memory while in use | 🔴 Exists in memory while in use |
| Terminal scrollback risk | 🟡 Possible depending on terminal behavior | ⚪ Not usually applicable |
| Clipboard manager risk | 🔴 Possible | 🟡 Often reduced but still possible |

* * *

## Local Data Leakage

| Security Area | pget | Cloud Password Manager |
| --- | --- | --- |
| Plaintext disk writes | 🟢 Avoided by design | 🟡 Depends on app implementation |
| Vim swap/backup leakage | 🟢 Disabled in hardened `.vimrc` | ⚪ Not applicable |
| Undo/history leakage | 🟢 Disabled in hardened `.vimrc` | 🟡 Depends on app |
| Encrypted backups | 🟢 Local encrypted backups only | 🟡 Cloud/provider backups |
| Temporary files | 🟢 Encrypted temp output only | 🟡 Depends on client |

* * *

## Failure and Recovery

| Security Area | pget | Cloud Password Manager |
| --- | --- | --- |
| Forgotten master password | 🔴 No recovery | 🟡 Some recovery options may exist |
| Vendor recovery abuse | 🟢 None | 🟡 Depends on provider model |
| Data corruption recovery | 🟡 Local backups required  <br>(Auto-backups, user set retention) | 🟢 Often provider-managed |
| User responsibility | 🔴 High | 🟡 Medium |
| Convenience safeguards | 🟡 Minimal | 🟢 Stronger for average users |

* * *

## Malware and Compromised Device Risk

| Security Area | pget | Cloud Password Manager |
| --- | --- | --- |
| Malware on device | 🔴 Total compromise possible | 🔴 Total compromise possible |
| Keylogger risk | 🔴 Master password can be captured | 🔴 Master password can be captured |
| Remote desktop/session hijack | 🔴 Active session can be observed | 🔴 Active session can be observed |
| Protection after compromise | 🔴 Very limited | 🔴 Very limited |

> **Important:** If the computer itself is compromised, both pget and cloud password managers are at serious risk.

* * *

## Where pget Is Stronger

🟢 **No cloud vault**  
There is no remote service storing the encrypted vault. Not relying on a third party vendor or its supply chain.

🟢 **No browser extension**  
This removes a major attack surface.

🟢 **No online account**  
There is no account takeover path.

🟢 **Manual unlock control**  
The user can manually clear the GPG cache with `pget -x` or interactive `x`.

🟢 **Auto-kill GPG agent on exit**  
When enabled, the vault does not remain conveniently unlocked after pget exits.

🟢 **Transparent behavior**  
The storage format, encryption flow, and UI behavior are visible and auditable.

* * *

## Where Cloud Password Managers Are Stronger

🟢 **Better convenience**  
They usually provide browser integration, mobile access, and autofill.

🟢 **Built-in sync**  
Multi-device access is automatic.

🟢 **Recovery options**  
Some cloud managers provide account recovery or emergency access.

🟢 **Clipboard timeout features**  
Many tools clear copied secrets automatically.

🟢 **Lower burden for average users**  
Less manual handling means fewer operational mistakes for non-technical users.

* * *

## Biggest pget Risks

| Rank | Risk | Severity |
| --- | --- | --- |
| 1   | Compromised machine or malware | 🔴 High |
| 2   | Lost master password | 🔴 High |
| 3   | Clipboard exposure | 🔴 High |
| 4   | Visible secrets on screen  <br>(Controlled by user) | 🟡 Medium |
| 5   | Terminal/session exposure | 🟡 Medium |
| 6   | User-managed backups | 🟡 Medium |

* * *

## Biggest Cloud Password Manager Risks

| Rank | Risk | Severity |
| --- | --- | --- |
| 1   | Vendor breach or service compromise | 🔴 High |
| 2   | Account takeover | 🔴 High |
| 3   | Browser extension exposure | 🔴 High |
| 4   | Autofill phishing | 🔴 High |
| 5   | Device compromise | 🔴 High |
| 6   | Vendor lock-in or service dependency | 🟡 Medium |

* * *

## Bottom Line

| Summary | pget | Cloud Password Manager |
| --- | --- | --- |
| Best security trait | 🟢 Minimal attack surface | 🟢 Convenience with managed protections |
| Biggest weakness | 🔴 User responsibility | 🔴 Cloud/vendor/supply chain/browser exposure |
| Best fit | Security-focused local users | General users needing sync and convenience |
| Overall security style | Local, manual, transparent | Cloud, automated, provider-managed |

* * *

## One-Line Summary

> **pget is safer from external/cloud attacks. Cloud password managers are safer from many everyday user mistakes.**

* * *

## Practical Verdict

For a technical user who understands local file management, GPG, backups, and terminal workflows:

🟢 **pget provides a strong local-first security model with very little external attack surface.**

For a non-technical user who needs syncing, autofill, recovery, and mobile access:

🟡 **A reputable cloud password manager may be safer in practice because it reduces user error.**
