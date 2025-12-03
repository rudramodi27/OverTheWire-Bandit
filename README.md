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
