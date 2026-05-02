# Bandit Level 2 → Level 3

## 📌 Info

| | |
|---|---|
| **Source** | [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/bandit3.html) |
| **Level** | 1 → 2 |
| **Difficulty** | 1⭐|
| **Date** | 2026-4-30 |
| **Time** | ~2 min |

---

## 🎯 Goal

> *The password for the next level is stored in a file called --spaces in this filename-- located in the home directory*

---

## 💡 Concepts

- `cat` — reads file content, but treats ` ` as **stdin** (keyboard input) by default
- `./` — explicitly references a file in the **current directory**


> 🧠 **What's new here?**  
> Not all filenames are "normal". Dashes, spaces, and special characters can break standard commands — you need to tell the shell *exactly* what you mean.

---

## 🔍 Walkthrough

### Step 1 — Connect

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
# Password: (from Level 1)
```

### Step 2 — List files

```bash
ls
```

```
--spaces in this filename--

```

Using "*" for the file with the space in the filename.

### Step 3 — The problem solving

```bash
cat ./"--spaces in this filename--"
```

**Output:**
```
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

---

## 🚩 Password

```
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

> ⚠️ Passwords rotate periodically. Always retrieve your own.

---

## 📖 Takeaways

1. **`-` and inside space are not a filename the shell handles naturally** — prefix with `./` whenever a filename starts with a special character and use double quote if there's a space in filename
---

## 🔗 References

None

---

*Writeup by trantrung1291(https://github.com/trantrung1291) · Learning cybersecurity from scratch · [All writeups](../../README.md)*
