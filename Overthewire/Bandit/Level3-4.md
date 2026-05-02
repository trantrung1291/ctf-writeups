# Bandit Level 3 → Level 4

## 📌 Info

| | |
|---|---|
| **Source** | [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/bandit3.html) |
| **Level** | 3 → 4 |
| **Difficulty** | 2⭐|
| **Date** | 2026-4-30 |
| **Time** | ~2 min |

---

## 🎯 Goal

> *The password for the next level is stored in a hidden file in the inhere directory.*

---

## 💡 Concepts

- `ls`- List all the files and folders
- `cd` - Change directory to inhere folder.
- `ls -la` list long information included hidden stuffs

> 🧠 **What's new here?**  
> Using `ls` cannot show hidden files or folder.
> -a --all to show all 
> -l use a long listing format
---

## 🔍 Walkthrough

### Step 1 — Connect

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
# Password: (from Level 2)
```

### Step 2 — List files

```bash
ls
cd inhere
ls
```

List all the file and folder. Then change to the inhere directory and list infomation in here.


### Step 3 — The problem 

**Output:**
```
NOthing

```
Because `ls` command cannot show hidden files and folders.
---

### Step 4 - Problem solving

```bash
ls -a
```
Or Using the parameter -l for more information
```bash
ls -la
```
**Output**
```
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
## 🚩 Password

```
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

```

> ⚠️ Passwords rotate periodically. Always retrieve your own.

---

## 📖 Takeaways

1. You should you -la for more information and to see hidden files and folder.
---

## 🔗 References

.....

---

*Writeup by trantrung1291(https://github.com/trantrung1291) · Learning cybersecurity from scratch · [All writeups](../../README.md)*
