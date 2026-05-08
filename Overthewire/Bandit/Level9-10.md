# Bandit Level 9 → Level 10

## 📌 Info

| | |
|---|---|
| **Source** | [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/bandit9.html) |
| **Level** | 9 → 10 |
| **Difficulty** | 2⭐|
| **Date** | 2026-5-4 |
| **Time** | ~10 min |

---

## 🎯 Goal

> *
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.*

---

## 💡 Concepts

- `strings`- to print strings in files

- Piping (|)- to send an output of a command to another command for further pocessing.

> 🧠 **What's new here?**  
> Using Piping to process data efficiently.

## 🔍 Walkthrough

### Step 1 — Examine the contents of data.txt

First, I check the contents of data.txt. There are so many users and password. 

```bash
cat data.txt
```

I found out that data.txt was a binary file. So i used `strings` to display readable strings in file and using Piping and `grep` to search for the strings that appear after ""=="" characters
 
```bash
strings data.txt | grep "==.*"
```
in here, I used '==.*' to print out strings that match the '==......' pattern. 
Character 	Meaning
.	matches any character
*	repeats the preceding element zero or more times

**Output**
```
========== the
2========== password
========== is
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
````

## 🚩 Password

```
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

```

> ⚠️ Passwords rotate periodically. Always retrieve your own.

---

## 📖 Takeaways

learned more about grep because of its powerful string extraction capabilities.
---

## 🔗 References
1.https://ryanstutorials.net/linuxtutorial/grep.php

---

*Writeup by trantrung1291(https://github.com/trantrung1291) · Learning cybersecurity from scratch · [All writeups](../../README.md)*
