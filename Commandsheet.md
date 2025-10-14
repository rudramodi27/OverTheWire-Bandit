# 🔧 OverTheWire Bandit — Useful Commands (Cheat Sheet)

**Purpose:** Quick reference for common commands and one‑liners used while solving Bandit levels.

> ⚠️ **Reminder:** Do **not** publish real passwords, private keys, or other secrets in your repo. Use `<REDACTED>` where needed.

---

## 🧭 Basic shell / navigation
```bash
pwd               # show current directory
ls -la            # list all files (including hidden) with details
cd /path/to/dir   # change directory
cd ~              # go to your home directory
cd -              # go back to previous directory
```

---

## 📄 Inspect files & types
```bash
file filename         # detect file type (text, gzip, ELF, etc.)
ls -lb                # show filenames with escapes for special chars
stat filename         # show metadata (owner, perms, timestamps)
hexdump -C filename   # hex + ASCII dump (view binary content)
xxd filename          # another hex dump tool
```

---

## 👀 View file contents
```bash
cat filename                 # print entire file (small files)
less filename                # page through file (useful for long files)
more filename
head -n 20 filename          # show first 20 lines
tail -n 20 filename          # show last 20 lines
sed -n '1,40p' filename     # print specific line range
awk 'NR>=1 && NR<=40{print}' filename  # print specific lines with awk
```

---

## 🔎 Search & grep
```bash
grep "pattern" file           # search for pattern in file
grep -R --line-number -I "pattern" . 2>/dev/null
# -R recursive, --line-number show line, -I ignore binary files

# find files containing printable strings (fast heuristic)
grep -R --line-number -I "[a-zA-Z0-9]" . 2>/dev/null
```

---

## 🔍 Find files (powerful)
```bash
# find files by name/type/owner/permissions/size
find . -type f                       # all files under current dir
find . -type f -maxdepth 2           # limit depth
find . -type f -name "pattern"       # name match (use quotes for spaces)
find / -user banditX -type f 2>/dev/null   # files owned by user banditX

# find readable files (by user)
find . -type f -perm -u=r -exec ls -l {} + 2>/dev/null

# find smallest files (passwords often short)
find . -type f -exec wc -c {} + | sort -n | head -n 30

# find files matching a file-type filter using 'file'
find . -type f -exec file {} + | grep -i text
```

---

## 🧰 Tools for binary / hidden text
```bash
strings filename         # extract printable strings from binary
strings filename | less
xxd filename | less
hexdump -C filename | less
```

---

## 🔐 SSH & keys (how to use keys safely)
```bash
# SSH into bandit server (example)
ssh banditX@bandit.labs.overthewire.org -p 2220

# If you find a private key locally and are allowed to use it:
chmod 600 keyfile
ssh -i keyfile banditY@bandit.labs.overthewire.org -p 2220

# Inspect key fingerprint (safe to view)
ssh-keygen -lf keyfile

# NOTE: never commit keyfile to git; add patterns to .gitignore
```

---

## 🧩 Archives & compression
```bash
# tar
tar -tvf archive.tar         # list files in tar
tar -xvf archive.tar         # extract tar

# gz
gunzip -c file.gz > out      # dump contents without creating file via gunzip -c
zcat file.gz                 # view gzipped file

# bzip2
bunzip2 -c file.bz2 > out    # similar to gunzip

# zip
unzip -l file.zip            # list contents
unzip file.zip               # extract

# tar.gz / tgz
tar -xvzf file.tar.gz        # extract gzipped tar
```

---

## 🔁 Encodings (base64, hex)
```bash
# base64
base64 -d encoded.txt > out.bin    # decode base64 (GNU)
# or
openssl base64 -d -in encoded.txt -out out.bin

# hex (when file is hex-dump of raw bytes)
xxd -r -p hexfile > out.bin
# then inspect out.bin with file/strings/xxd
file out.bin
strings out.bin | less
```

---

## 🧪 Chaining commands (useful one-liners)
```bash
# base64 decode and pipe to tar extract (if base64 wraps an archive)
base64 -d file | tar -xvf -   # decode then extract from stdin

# decode to file then inspect
base64 -d file > /tmp/out && file /tmp/out && strings /tmp/out | head

# show file types for many files
find . -type f -exec file {} + | less
```

---

## 🧾 Permissions / ownership
```bash
ls -la                       # view rwx perms and owner
chmod 600 file               # set private permissions (for keys)
stat file                    # detailed permissions & owner info
getfacl file                 # show ACLs (if getfacl available)
```

---

## 🧰 Convenience / safety tips
```bash
# show non-printable characters in file (helpful to detect CRLF)
cat -v filename

# show filenames with unprintable chars escaped
ls -lb

# show commands you ran (history) - careful, don't leak secrets
history

# redirect error messages to /dev/null to avoid clutter
somecommand 2>/dev/null
```

---

## 🧩 Quick scripts / helpers (copy-paste safe)
```bash
# 1) quick-inspect.sh - run in a level dir to get candidates
#!/bin/bash
echo "PWD: $(pwd)"
ls -la
echo
echo "File types (quick):"
find . -maxdepth 2 -type f -exec file {} + | grep -i 'text\|ascii\|script' || true
echo
echo "Small files (likely passwords):"
find . -type f -exec wc -c {} + | sort -n | head -n 20
```

```bash
# 2) brute-cat-all.sh - show first lines of every file (use with caution)
#!/bin/bash
find . -type f -print0 | xargs -0 -I{} sh -c 'echo "==== {} ===="; head -n 5 "{}" 2>/dev/null || true'
```

---

## 🧾 .gitignore suggestions (do NOT commit secrets)
```
# ignore private keys and env files
*.pem
*.key
*.env
secrets/
private_keys/
*.private
```

---

## ✅ Good practices summary
- Always use `<REDACTED>` in public repo for passwords or keys.  
- Keep a **private** notes file locally for real passwords (never push it).  
- Use `file` first to figure out the format — it saves time.  
- Prefer `head`/`file`/`strings` before running unknown binaries.  
- Use `chmod 600` for private key files before using `ssh -i`.  
- Limit `find` scope and redirect `2>/dev/null` to avoid noisy permission errors.

---

## 🔚 Final note
This cheat sheet is concise and practical — add it to your repo as `commands.md` or `commands/README.md`. Keep secrets out of version control.

