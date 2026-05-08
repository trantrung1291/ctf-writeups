# Bandit Level 10 → Level 11

## 📌 Info

| | |
|---|---|
| **Source** | [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/bandit10.html) |
| **Level** | 10 → 11 |
| **Difficulty** | 3⭐|
| **Date** | 2026-5-4 |
| **Time** | ~10 min |

---

## 🎯 Goal

> *
The password for the next level is stored in the file data.txt, which contains base64 encoded data*

---

## 💡 Concepts

- Base64 encoding is a common method for representing binary data in ASCII string format.
We can use the base64 command to encode a string: echo 'trung' | base64 -> dHJ1bmcK
To decode =, use `-d` flag:  echo 'dHJ1bmcK' | base64 -d -> trung 

- Piping (|)- to send an output of a command to another command for further pocessing.

> 🧠 **What's new here?**  
> base64 can be identified by strings that contain characters A–Z, a–z, 0–9, +, /, and end with =.

## 🔍 Walkthrough

### Step 1 — Examine the contents of data.txt

First, I check the contents of data.txt. There are so many users and password. 

```bash
cat data.txt
```
**Output**

```bash
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
```
I recognized that it was encoded data.

### Step 2 - Decode data.txt

I used `-d` flag with `base64` command
```bash
base64 -d data.txt
```
**Output**
```
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
````

## 🚩 Password

```
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

```

> ⚠️ Passwords rotate periodically. Always retrieve your own.

---

## 📖 Takeaways

Base64 encoded data can be identified by strings that contain characters A–Z, a–z, 0–9, +, /, and end with =.
---

## 🔗 References
1. https://www.geeksforgeeks.org/linux-unix/tr-command-in-unix-linux-with-examples/
---

*Writeup by trantrung1291(https://github.com/trantrung1291) · Learning cybersecurity from scratch · [All writeups](../../README.md)*
