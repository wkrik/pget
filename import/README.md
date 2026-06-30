# Import From Other Password Managers
Follow the Instructions that applies to you:
* **Manual** import of passwords from other password manager
* **Keepass** import: Run the provided script "**./convert_keepass --help**" to view the KeePass instruction below.

---

## Manual
Password vaults are simply formatted text files that are encrypted. They have 4 fields *(in this order: Title, ID, Password, any other data you want)*, and is all delimited by tabs. To Import other password managers into pget, perform the following:

1.  Export from the data from your existing password manager to a CSV file.
2.  Open the CSV file into a spreadsheet (ie. Excel or Libreoffice).
3.  Massage each line in the file to match the mandatory 4 fields:

| Title | ID | Password | Comments and Notes Password Manager |  
| --- | --- | --- | --- |  
| Amazon | johndoe | beiFo!qu#ee8a^ep | AWS Account \| prime \| for work |

**Note**: If you have multiple comments for the 4th field, separate them with a "|" (vertical bar), so it .

4. Export as a **CSV** file, **TAB** delimited.
5. Save the new tab delimited export file as **pget.tsv**
7.  From a Linux shell, run:
```
$ pget -E
```

After entering the password and you will see the unencrypted default password vault in vim.

9.  Inside vim, enter the command:
```
:r pget.tsv
```
to append the newly exported pget.tsv file to the end of default password vault file.

10. Save and exit vim:
```
:wq!
```

Your passwords have been imported.

---

## KeePass
Run the provided script "**./convert_keepass --help**" to view the below instructions.

1. Inside KeePass do one of the following:
        **File > Export > CSV**
   or
        **Group > Data Exchange > Export > CSV**

3. Run the provided conversion script:
```
./convert_keepass input.csv output.tsv
 ```
  
If a group is exported, run:
```
./convert_keepass -g GroupName input.csv output.tsv
```

Examples:
  ./convert_keepass keepass.csv pget.tsv
  ./convert_keepass -g Network keepass.csv pget.tsv

5. Run:
```
$ pget -E
```

7. Import output.tsv file. Inside vim, entry the command:
```
:r output.tsv
```

8. Save and quit vim with the command:
```
:wq!
```
