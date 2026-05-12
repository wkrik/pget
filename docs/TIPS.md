# TIPS for using pget

### 1. Think vim!
### 2. Searching Made Easy
### 3. Formatting Entries


## 1. Think vim!
Initially pget was vim based only. As the UI was developed
vim like keystrokes were used to quickly launch what is
needed most and quickly using just the right hand:
j | up
k | down
h | hide and unhide secrets/password
l | look/show more information on an entry
y | yank to the clipboard
/ | slash to search

## 2. Searching Made Easy
Search one pattern, multiple patterns or no patterns.

Shell:
$ pget bank | search the default vault for all entries with the pattern "bank". 
$ pget -v Work microsoft |
* Single pattern:
: from linux shell:

There are times when you want to list the entries
in the vault and not search.
* Entering a slash "/" by itself will list the first 40 entries.
This can be changed in pget-lib-vault, search: max_empty_results 
* Entering slash space "/ " will display ALL entries.

## 3. Formating
The format of a vault file is 4 fields separated by tabs:
Title [tab] ID [tab] SECRET [tab] Comment

Here are some formatting tips to make searching easier

Use Categories before the title to group searches together
Category: Title 

Ins: AAA 
Ins: Mercury
Ins: Cigna
Ins: Aetna


