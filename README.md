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

# Walkthrough Guide
# 🎯 Bandit Level 00

**Level Goal:**  
Access the first file in the home directory.

**💡 Tip:**  
Hidden files can be listed with `ls -la`.

**Commands Used:**  
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
bandit0@bandit.labs.overthewire.org s password: bandit0
ls
cat readme
## 🔑 Password for Next Level
`<REDACTED>`  <!-- Replace with actual password only in your local copy. Do NOT publish the real password publicly. -->

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
```
# The output of the above command is the password for level 1.
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
```
# The output of the above command is the password for level 2.
