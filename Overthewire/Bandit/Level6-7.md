# Bandit Level 6 → Level 7

## 📌 Info

| | |
|---|---|
| **Source** | [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/bandit6.html) |
| **Level** | 5 → 6 |
| **Difficulty** | 3⭐|
| **Date** | 2026-5-3 |
| **Time** | ~10 min |

---

## 🎯 Goal

> *
The password for the next level is stored somewhere on the server and has all of the following properties:
owned by user bandit7
owned by group bandit6
33 bytes in size
 *

---

## 💡 Concepts

- `find`: - search in a directory
- `2>/dev/null` option - to filter out the error so that you can't see the error output.


> 🧠 **What's new here?**  
> Sometimes, The output contains a lot of errors like: permission denied... You should filter out them for the cleaner output

## 🔍 Walkthrough

### Step 1 — Connect

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
# Password: (from Level 4)
```

### Step 2 — Examine the contents of the directories

First, I listed all files and directories.
```bash
ls -la
```

**Output**

```
total 20
drwxr-xr-x   2 root root 4096 Apr  3 15:17 .
drwxr-xr-x 150 root root 4096 Apr  3 15:20 ..
-rw-r--r--   1 root root  220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root root 3851 Apr  3 15:10 .bashrc
-rw-r--r--   1 root root  807 Mar 31  2024 .profile
````

### Step 3 - Problem solving

 Used `find` to search for files that match the challenge requirements.
 Added some option `-type`,`-size`, `-user`, `-group`
 `/` to search for files in root directory and its subdirectories

```bash
find / -type f -size 33c -user bandit7 -group bandit6
```

**Output**

```
find: ‘/tmp’: Permission denied
find: ‘/etc/credstore.encrypted’: Permission denied
find: ‘/etc/sudoers.d’: Permission denied
find: ‘/etc/stunnel’: Permission denied
find: ‘/etc/multipath’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/etc/polkit-1/rules.d’: Permission denied
find: ‘/etc/credstore’: Permission denied
find: ‘/etc/xinetd.d’: Permission denied
find: ‘/dev/mqueue’: Permission denied
find: ‘/dev/shm’: Permission denied
find: ‘/snap’: Permission denied
find: ‘/lost+found’: Permission denied
....
```

It was time-consuming to check the output, so i added `2>/dev/null` to filter out the errors

```bash
find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null
```

**Output**

```
/var/lib/dpkg/info/bandit7.password
```

Check this file.

```bash
cat /var/lib/dpkg/info/bandit7.password
```  
**Output**
```
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

## 🚩 Password

```
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

```

> ⚠️ Passwords rotate periodically. Always retrieve your own.

---

## 📖 Takeaways

You should search for files in the root directory and its subdirectories to avoid missing relevant files. Using 2>/dev/null to filter out errors and got the cleaner output.
---

## 🔗 References
1.https://manpages.ubuntu.com/manpages/noble/man1/find.1.html

---

*Writeup by trantrung1291(https://github.com/trantrung1291) · Learning cybersecurity from scratch · [All writeups](../../README.md)*
