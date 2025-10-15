# OverTheWire-Bandit
This repository contains a walkthrough guide to completing the Bandit levels in the OverTheWire wargames.

This repository serves as:

Documentation of my methods and thought process as I solve each level.
Revision guide based on the key takeaways from solving each challenge.
Each level of the walkthrough guide summarises the:

Level Goal (taken verbatim from what's given on the site)
Key Takeaways
Alternatives (if any)
Common misconceptions (if any)
Tip: For those using the Windows Command Prompt to ssh into each level's server, you can right-click on the cmd after copying the password unlocked from the previous level. The right-click pastes the password which was copied. Using the normal shortcut keys to paste (CTRL + V or SHIFT + INSERT) did not work for me.
# 🔧 OverTheWire Bandit — Useful Commands (Cheat Sheet)

**Purpose:** Quick reference for common commands and one‑liners used while solving Bandit levels.  
**Tip:** Keep this file public-safe — never paste real passwords or private keys here.

---

# Walkthrough Guide
# 🎯 Bandit Level 00

**Level Goal:**  
Access the first file in the home directory.

**💡 Tip:**  
Hidden files can be listed with `ls -la`.

## 📝 Commands Used  
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
bandit0@bandit.labs.overthewire.org s password: b*n*#t0
ls
cat readme

# The output of the above command is the password for level 0.
```
# 🎯 Bandit Level 00 → Level 01
*⚠️ Spoiler Alert:**  
This walkthrough contains the solution to Bandit Level 1. Open only if you want to see the answer.

---

## 🎯 Level Goal
The password for the next level is stored in a file called `readme` located in the home directory.

---

## 💡 Tip
- Windows users: Right-click in CMD to paste the copied password (CTRL+V often doesn’t work).  
- Always use `ls -la` to see hidden files if needed.

---

## 📝 Commands Used
```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
bandit1@bandit.labs.overthewire.org s password: Use the password you obtained from level 0 (store it only locally; do not push to remote).
ls
cat ./-

# The output of the above command is the password for level 1.
```
# 🎯 Bandit Level 01 → Level 02

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 1 to level 2. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
The password for the next level is stored in a file called `-` located in the home directory.

---

## 💡 Quick Tip
- If a filename looks odd (like `-`), many commands treat `-` as stdin. To refer to a filename that begins with a dash, prefix it with `./` or use `--` where supported.
- Never commit real passwords or keys to a public repo — use `<REDACTED>`.

---

## 📝 Commands Used
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
bandit2@bandit.labs.overthewire.org s password: Use the password you obtained from level 1 (store it only locally; do not push to remote).
ls
cat ./--spaces\ in \ this \ filename\--

# The output of the above command is the password for level 2.
```
# 🎯 Bandit Level 02 → Level 03

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 2 to level 3. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
The password for the next level is stored in a file called `spaces in this filename` located in the home directory.

---

## 💡 Quick Tip
- Filenames can contain spaces. Use quotes (`"..."` or `'...'`) or escape spaces with backslashes (`\ `) when referring to such files.
- Don't publish real passwords — use `<REDACTED>` in public repos.

---

## 📝 Commands Used
```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
bandit3@bandit.labs.overthewire.org s password: Use the password you obtained from level 2 (store it only locally; do not push to remote).
ls
cd inhere
ls -a
cat ./...Hiding-From-You

# The output of the above command is the password for level 3.
```
# 🎯 Bandit Level 03 → Level 04

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 3 to level 4. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
The password for the next level is located somewhere inside a directory called `inhere` in the home directory.

---

## 💡 Quick Tip
- Use `ls -la` and `file` to inspect files and discover which file is likely to contain readable text.  
- `find` is your friend when many files/subdirectories exist — filter by type/size to speed things up.  
- Never publish real passwords — use `<REDACTED>` in public repos.

---

## 📝 Commands Used
```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
bandit4@bandit.labs.overthewire.org s password: Use the password you obtained from level 3 (store it only locally; do not push to remote).
ls
cd inhere
ls -a
file ./*
cat ./-file07

# The output of the above command is the password for level 4.
```
# 🎯 Bandit Level 04 → Level 05

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 4 to level 5. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
The password for the next level is hidden somewhere inside the `inhere` directory (it may be nested); you must locate and read the correct file to get the password.

---

## 💡 Quick Tips
- Use `find` to recursively search — it's the most reliable tool for nested directories.  
- Use `file` to filter for plain text files.  
- Use size filters (small files often contain short passwords) or inspect file types to narrow candidates quickly.  
- Do **not** publish real passwords in your repo — use `<REDACTED>`.

---

## 📝 Commands Used (examples)
```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
bandit5@bandit.labs.overthewire.org s password: Use the password you obtained from level 4 (store it only locally; do not push to remote).
ls
cd inhere
find . -type f -size 1033c -not -executable -exec file {} + | grep ASCII
cat ./maybehere07/.file2

# The output of the above command is the password for level 5.
```
# 🎯 Bandit Level 05 → Level 06

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 5 to level 6. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
Locate and read the file that contains the password for the next level (it may be inside a directory or in an unusually-named file). 

---

## 💡 Quick Tips
- When directories contain many files, use `find` + `file` to quickly locate plain-text candidates.  
- Use `strings` on binary/data files that might hide readable text.  
- Use `ls -lb` to reveal weird/hidden characters in filenames.  
- **Do NOT** publish real passwords — replace them with `<REDACTED>` in public repos.

---

## 📝 Commands Used (examples)
```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
bandit6@bandit.labs.overthewire.org s password: Use the password you obtained from level 5 (store it only locally; do not push to remote).
ls
find / -type f -user bandit7 -group bandit6 -size 33
find / -type f -user bandit7 -group bandit6 -size 33c 2> dev/null/var/lib/dpkg/info/bandit7.password
cat /var/lib/dpkg/info/bandit7.password

# The output of the above command is the password for level 6.
```
# 🎯 Bandit Level 06 → Level 07

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 6 to level 7. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
The password for the next level is hidden in a file somewhere in the home directory — it may be encoded or archived (not plain text).

---

## 💡 Quick Tips
- If a file is not plain text, try `file`, `strings`, or view a hex dump (`xxd` / `hexdump`) to inspect it.  
- Common encodings/compressions used in Bandit: Base64, gzip, bzip2, tar, zip. Try decoding/unpacking systematically.  
- Use `file` first — it often tells you the format (e.g., gzip compressed data, ASCII text, POSIX tar archive).  
- **Do NOT** publish real passwords — use `<REDACTED>` in public repos.

---

## 📝 Commands Used (examples)
```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
bandit7@bandit.labs.overthewire.org s password: Use the password you obtained from level 6 (store it only locally; do not push to remote).
ls
head -n 10 data.txt
grep millionth data.txt

# The output of the above command is the password for level 7.
```
# 🎯 Bandit Level 07 → Level 08

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 7 to level 8. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
Find and read the file that contains the password for the next level. The file may have unusual permissions or be accessible only in a specific way.

---

## 💡 Quick Tips
- Check file permissions and ownership with `ls -la`. Look for files readable by your user or group.  
- Use `find` to search for files with specific permissions (`-perm`) or ownership (`-user`/`-group`).  
- If a file looks like a private key, **do not** publish it — keep it local and safe.  
- **Do NOT** publish real passwords — use `<REDACTED>` in public repos.

---

## 📝 Commands Used (examples)
```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
bandit8@bandit.labs.overthewire.org s password: Use the password you obtained from level 7 (store it only locally; do not push to remote).
ls
head -n 10 data.txt
cat data.txt | sort | uniq -u

# The output of the above command is the password for level 7.
```
# 🎯 Bandit Level 08 → Level 09

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 8 to level 9. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
The password for the next level is stored somewhere accessible from the current account — it may require inspecting file contents, permissions, or using an available key/tool to read it.

---

## 💡 Quick Tips
- Inspect home directory first: `pwd && ls -la`. Many Bandit levels hide the password in home or a nearby folder.  
- Check `.ssh` and other dotfiles for keys or hints, but **do not** publish private keys.  
- Use `file`, `strings`, `stat`, and `ls -lb` to understand file types and spot weird filenames.  
- `find` with filters (size, owner, permissions) narrows down candidates quickly.  
- Use `<REDACTED>` in repo; keep real password only in local/private notes.

---

## 📝 Commands Used (examples)
```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
bandit9@bandit.labs.overthewire.org s password: Use the password you obtained from level 8 (store it only locally; do not push to remote).
ls
head -n 4 data.txt
cat data.txt | strings -e s | grep ==

# The output of the above command is the password for level 8.
```
# 🎯 Bandit Level 09 → Level 10

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 9 to level 10. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
Locate and read the file that contains the password for the next level. The password may be hidden inside a file with unusual format, encoding, or permissions.

---

## 💡 Quick Tips
- Start with `pwd && ls -la` to understand where you are.  
- Use `file`, `strings`, and `hexdump`/`xxd` to inspect non-plain-text files.  
- Try common decoders/unpackers (base64, gzip, bzip2, tar, zip) based on `file` output.  
- Use `find` + `wc -c` to surface very small files (passwords are often short).  
- **Never** publish real passwords or private keys to a public repo — use `<REDACTED>`.

---

## 📝 Commands Used (examples)
```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
bandit10@bandit.labs.overthewire.org s password: Use the password you obtained from level 9 (store it only locally; do not push to remote).
ls
cat data.txt
cat data.txt | base64 -d

# The output of the above command is the password for level 9.
```
# 🎯 Bandit Level 10 → Level 11

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 10 to level 11. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
Locate and read the file that contains the password for the next level. The password may be hidden in a file, require using a private key found in the environment, or require reading a file owned by a different user (but accessible to you).

---

## 💡 Quick Tips
- Start with `pwd && ls -la` to see your home and hidden files.  
- Look for SSH keys or oddly-named files (`.ssh`, `id_rsa`, `keyfile`, etc.) but **do not** publish keys.  
- If you find a private key and it's allowed to be used, set secure permissions locally (`chmod 600 keyfile`) before using it with `ssh -i`.  
- Use `file`, `strings`, `stat`, `ls -lb`, and `find` to locate likely candidates.  
- Always redact passwords/keys in public repos: use `<REDACTED>`.

---

## 📝 Commands Used (examples)
```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
bandit11@bandit.labs.overthewire.org s password: Use the password you obtained from level 10 (store it only locally; do not push to remote).
ls
cat data.txt
cat data.txt | 'A-Za-z' 'N-ZA-Mn-za-m'

# The output of the above command is the password for level 10.
```
# 🎯 Bandit Level 11 → Level 12

**⚠️ SPOILER ALERT**  
This file contains the full solution for moving from Bandit level 11 to level 12. If you want to solve it yourself, stop reading now.

---

## 🎯 Level Goal
Locate and read the file that contains the password for the next level. The password may be hidden in a file with special permissions, unusual ownership, or located outside the home directory but accessible to the current account.

---

## 💡 Quick Tips
- Start with `pwd && ls -la` to see your working directory and hidden files.  
- Use `find` to search the filesystem for interesting files (by owner, permissions, size, or name).  
- Inspect file metadata with `stat` and `file` before trying to open files.  
- Use `strings`, `hexdump`/`xxd`, or `file` for non‑plain files.  
- Keep any keys or passwords private — **do NOT** publish real secrets to GitHub. Use `<REDACTED>`.

---

## 📝 Commands Used (examples)
```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
bandit12@bandit.labs.overthewire.org s password: Use the password you obtained from level 11 (store it only locally; do not push to remote).
