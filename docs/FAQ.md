# F.A.Q Troubleshooting
1. VIM will not encrypt my password
2. AES256.CFB is not known
3. Can I force AES256 explicitly
4. Dialog box borders render incorrectly when entering master password

---

### 1. VIM will not encrypt my password
* Check that you login as the true user. 
Not "superuser" and switched to the user: su - [user]
vim and pget require direct access to the actual user's tty
* If testing vim + encryption, make sure you have 
write permissions in the current directory you are in.

---

### 2. AES256.CFB is not known
When vim launches a red warning message appears briefly:

  *The cipher AES256.CFB is not known by the local gpg command. Using default!*

#### Cause:
vim-gnupg detects the encryption mode as AES256.CFB, while GPG
reports supported ciphers as AES256. The mode suffix (.CFB) is not
recognized by GPG as part of the cipher name, so vim-gnupg falls
back to the default, which is AES256.

#### Impact:
None. The file remains encrypted using AES256.

#### Verification:
You can confirm the cipher type after editing with the command:

  gpg --list-packets Primary.gpg | grep -i 'symkey enc packet\|encrypted data'

Expected output should indicate AES256.

---

### 3. Can I force AES256 explicitly:
Yes. If it makes you feel more comfortable, set AES256 in your 
GPG configuration:

  echo "cipher-algo AES256" >> ~/.gnupg/gpg.conf

This makes AES256 the default for all symmetric encryption operations.

---

### 4 Dialog box borders render incorrectly when entering master password

When asked for the master password, and this is displayed:

```
lqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqk
x Enter passphrase                                     x
x                                                      x
x                                                      x
x Passphrase: ________________________________________ x
x                                                      x
x       <OK>                              <Cancel>     x
mqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqj
```

When this was expected:

```
┌──────────────────────────────┐
│ Enter passphrase             │
│                              │
│ Passphrase: _________        │
│                              │
│   <OK>      <Cancel>         │
└──────────────────────────────┘
```

That’s classic pinentry-curses using ASCII fallback instead of 
Unicode/line-drawing characters. Those lqqq...k / x / mqqq...j 
are VT100-style box drawing characters, not the smooth ones you 
expect. pinentry-curses decides how to draw based on: 
locale + terminal capabilities

1. Check:
  $ locale

   If you see something without .UTF-8, that’s the problem. Like:
   LANG=C
   or
   LANG=en_US

  FIX:
  sudo locale-gen en_US.UTF-8
  sudo update-locale LANG=en_US.UTF-8

  Then logout/login
  Check locale again
  You want to see: LANG=en_US.UTF-8

If it still doesn't work, you can fall back to a 
place text, box:

Install pinentry-tty as your other option:
  $ sudo apt install pinentry-tty

   Then set:
$ cat > ~/.gnupg/gpg-agent.conf <<'EOF'
pinentry-program /usr/bin/pinentry-tty
EOF

pinentry-tty is plain text, no box graphics at all.
$ gpgconf --kill gpg-agent


