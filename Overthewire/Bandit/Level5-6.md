# Bandit Level 5 → Level 6

## 📌 Info

| | |
|---|---|
| **Source** | [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/bandit5.html) |
| **Level** | 5 → 6 |
| **Difficulty** | 3⭐|
| **Date** | 2026-4-30 |
| **Time** | ~10 min |

---

## 🎯 Goal

> *The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties: human-readable; 1033 bytes in size; not executable *

---

## 💡 Concepts

- `find`: - search in a directory
	+ find + path + option
		* path: (.): current directory; (/) root.
		* -type: file(f), directory(d)... 
		* -size: c,b,k,m...
- `grep`: Search for text
	+ option: -I: avoid binary file
- ....

> 🧠 **What's new here?**  
> `find` command is very powerful to search for file or directory. Using `--help` for more information.

## 🔍 Walkthrough

### Step 1 — Connect

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
# Password: (from Level 4)
```

### Step 2 — Using `find` to search files 

First, I listed all files and directories. Then I navigated to the `inhere` directory.

```bash
ls -la
cd inhere
```


I proceed to find all files in this directory,

```bash
find . -type f
```

**Output**

```
/maybehere16/spaces file2
./maybehere16/spaces file1
./maybehere16/-file3
./maybehere16/-file1
./maybehere16/-file2
./maybehere16/.file1
./maybehere16/spaces file3
./maybehere16/.file2
````

I found many files across different subdirectories. 

### Step 3 - The problem 

Many files across different subdirectories. 

### Step 4 - The fix

I used the `-size` parameter to filter files by size, The file size was `1033c` (1033 bytes)

```bash
find . -type f -size 1033c 
```

**Output**

```
./maybehere07/.file2
```

Checked its contents

```bash
cat ./maybehere07/.file2
```

**Output**

```
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

I used the`-exec` option to execute another command within one single `find` command.

```bash
find . -type f -size 1033c -exec cat {}\;
#or
find . -type f -size 1033c -exec grep . -I {} \;
```  

We have:
1. `-exec` option to execcute `cat` command.
2.  {} stands for searched files.
3.  (\;) stand for end of command.
4.  `grep .` → matches any line with at least one character; `-I` → ignores binary files

## 🚩 Password

```
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

```

> ⚠️ Passwords rotate periodically. Always retrieve your own.

---

## 📖 Takeaways

1. `find` command is very powerful if you know how to use it correctly.
2. `find` can search for files in a directory and its subdirectories
---

## 🔗 References
1.https://manpages.ubuntu.com/manpages/noble/man1/find.1.html

---

*Writeup by trantrung1291(https://github.com/trantrung1291) · Learning cybersecurity from scratch · [All writeups](../../README.md)*