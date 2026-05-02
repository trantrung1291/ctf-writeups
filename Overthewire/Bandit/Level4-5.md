# Bandit Level 4 → Level 5

## 📌 Info

| | |
|---|---|
| **Source** | [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/bandit4.html) |
| **Level** | 4 →5 |
| **Difficulty** | 2⭐|
| **Date** | 2026-4-30 |
| **Time** | ~4min |

---

## 🎯 Goal

> *he password for the next level is stored in the only human-readable file in the inhere directory.*

---

## 💡 Concepts

- `ls`- List all the files and folders
- `cd` - Change directory to inhere folder.
- ....

> 🧠 **What's new here?**  
> There are many kinds of files, human-readable file and not. 
> 
>Wildcard characters in Unix/Linux (like "*" , ?...) allow the matching of files in an abstracted way. Asterisk *" character matches any characters. Question mark matches a single character.

## 🔍 Walkthrough

### Step 1 — Connect

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
# Password: (from Level 3)
```

### Step 2 — List files

```bash
ls -la
cd inhere
ls -la
```

First, I listed all files and directories. Then I navigated to the `inhere` directory and examined its contents


### Step 3 — The problem 

**Output:**
```
total 48
drwxr-xr-x 2 root    root    4096 Apr  3 15:17 .
drwxr-xr-x 3 root    root    4096 Apr  3 15:17 ..
-rw-r----- 1 bandit5 bandit4   33 Apr  3 15:17 -file00
-rw-r----- 1 bandit5 bandit4   33 Apr  3 15:17 -file01
-rw-r----- 1 bandit5 bandit4   33 Apr  3 15:17 -file02
-rw-r----- 1 bandit5 bandit4   33 Apr  3 15:17 -file03
-rw-r----- 1 bandit5 bandit4   33 Apr  3 15:17 -file04
-rw-r----- 1 bandit5 bandit4   33 Apr  3 15:17 -file05
-rw-r----- 1 bandit5 bandit4   33 Apr  3 15:17 -file06
-rw-r----- 1 bandit5 bandit4   33 Apr  3 15:17 -file07
-rw-r----- 1 bandit5 bandit4   33 Apr  3 15:17 -file08
-rw-r----- 1 bandit5 bandit4   33 Apr  3 15:17 -file09
```
It's not clear which files are human-readable.
The challange hint at using `ls, cat, cd, file, du, find` to solve.

---

### Step 4 - Problem solving

```bash
file ./-file*
```
Because some filenames start with a dash(-), they can be interpreted as command options, so i used ./ as the prefix and asterisk to determined the file types of all files starting with -file.

**Output**
```
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```
I noticed that file07 has an 'ASCII text' filetype so I proceeded to examine its contents.
```bash
cat ./-file07
```
**Output**
```
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

## 🚩 Password

```
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

```

> ⚠️ Passwords rotate periodically. Always retrieve your own.

---

## 📖 Takeaways

1. When dealing with a large number of file in a directory, manually checking is a time-consuming approach. When you noticed that many files follow a similar naming pattern, you can use wildcards such as asterisk * or question mark ? to filter and process files more efficiently and avoid missing relevant files
---

## 🔗 References
1. https://www.warp.dev/terminus/linux-wildcards
2. https://manpages.ubuntu.com/manpages/noble/man1/file.1.html

---

*Writeup by trantrung1291(https://github.com/trantrung1291) · Learning cybersecurity from scratch · [All writeups](../../README.md)*