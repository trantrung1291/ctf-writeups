# Bandit Level 8 → Level 9

## 📌 Info

| | |
|---|---|
| **Source** | [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/bandit8.html) |
| **Level** | 8 → 9 |
| **Difficulty** | 2⭐|
| **Date** | 2026-5-3 |
| **Time** | ~10 min |

---

## 🎯 Goal

> *
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once*

---

## 💡 Concepts

- `sort - command to sort file's contents
- `uniq` - to filter out repeat lines; -c, --count prefix lines by the number of occurrences; -u, --unique
only print unique lines

- Piping (|)- to send an output of a command to another command for further pocessing.

> 🧠 **What's new here?**  
> We can seach the repeat lines in file's contents.

## 🔍 Walkthrough

### Step 1 — Examine the contents of data.txt

First, I check the contents of data.txt. There are so many users and password. 

```bash
cat data.txt
```

There are more than 1000 lines of outputs. To find the lines that occur only once, i used `uniq` to check repeated lines. It has the `-u` option to print unique lines. That's what we need to solve the challenge

```bash
sort data.txt | uniq -u
```

**Output**

```
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
````

## 🚩 Password

```
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

```

> ⚠️ Passwords rotate periodically. Always retrieve your own.

---

## 📖 Takeaways

There are many ways to solve a problem. Dont forget to check the manual page of a command using `man`.
We have to use `sort` before using  `uniq`. 
---

## 🔗 References
1.https://ryanstutorials.net/linuxtutorial/piping.php

---

*Writeup by trantrung1291(https://github.com/trantrung1291) · Learning cybersecurity from scratch · [All writeups](../../README.md)*
