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

# 🎯 Bandit Level 01
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
bandit1@bandit.labs.overthewire.org s password: whatever you got in bandit0 write down there
ls
cat ./-


