# Bandit Level 7 → Level 8

## 📌 Info

| | |
|---|---|
| **Source** | [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/bandit7.html) |
| **Level** | 7 → 8 |
| **Difficulty** | 3⭐|
| **Date** | 2026-5-3 |
| **Time** | ~10 min |

---

## 🎯 Goal

> *
The password for the next level is stored in the file data.txt next to the word millionth
 *

---

## 💡 Concepts

- `grep` - command to search for plaintext or strings in files
- Piping (|)- to send an output of a command to another command for further pocessing.

> 🧠 **What's new here?**  
> We can seach contents of files using `grep`.

## 🔍 Walkthrough

### Step 1 — Examine the contents of data.txt

First, I check the contents of data.txt. There are so many users and password. 
Then, i used piping and `grep` to search for the string `millionth`.


```bash
cat data.txt | grep "millionth"
```
If you don't want to use Piping, we can used just `grep` command and got the same output

```bash
grep "millionth" data.txt
```

**Output**

```
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
````

## 🚩 Password

```
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

```

> ⚠️ Passwords rotate periodically. Always retrieve your own.

---

## 📖 Takeaways

There are many ways to solve a problem. Dont forget to check the manual page of a command using `man`.
---

## 🔗 References
1.https://manpages.ubuntu.com/manpages/resolute/man1/man.1.html

---

*Writeup by trantrung1291(https://github.com/trantrung1291) · Learning cybersecurity from scratch · [All writeups](../../README.md)*
