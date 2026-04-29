# Bandit Level 1 → Level 2

## 📌 Thông tin

| | |
|---|---|
| **Nguồn** | [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/bandit2.html) |
| **Level** | 1 → 2 |
| **Độ khó** | ⭐☆☆☆☆ |
| **Ngày giải** | 2026-29-4 |
| **Thời gian** | ~5 phút |

---

## 🎯 Mục tiêu (Goal)

> The password for the next level is stored in a file called - located in the home directory
---

## 💡 Kiến thức cần có (Concepts)

Những khái niệm/lệnh liên quan đến level này:

- `cd` — dùng để di chuyển giữa các thư mục
- `ls` — liệt kê file trong thư mục
- `cat` — đọc nội dung file

> 📚 **Tôi học được gì mới?**  
> Đối với các file hoặc folder có tên là các ký tự đặc biệt - (dashed line) sử dụng -- hoặc ./ để xử lý
> ví dụ: cat -- -file hoặc cat ./-file
---

## 🔍 Quá trình giải (Walkthrough)

### Bước 1 — Kết nối SSH vào server

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
# Password: từ bandit0

**Giải thích:**
- `bandit1` là username
- `-p 2220` chỉ định port (OverTheWire dùng port 2220, không phải 22 mặc định)

### Bước 2 — Xem có file gì trong thư mục home

```bash
ls -la
```

**Output:**
```
total 24  
-rw-r-----   1 bandit2 bandit1   33 Apr  3 15:17 -   
drwxr-xr-x   2 root    root    4096 Apr  3 15:17 .    
drwxr-xr-x 150 root    root    4096 Apr  3 15:20 ..   
-rw-r--r--   1 root    root     220 Mar 31  2024 .bash_logout  
-rw-r--r--   1 root    root    3851 Apr  3 15:10 .bashrc            
-rw-r--r--   1 root    root     807 Mar 31  2024 .profile 
```

**Nhận xét:** thấy có "-" và group bandit1 có quyền đọc cái này. Không biết là file hya folder

### Bước 3 — Truy suất thử xem phải folder không? 

```bash
cd ./-
```

**Output:**
```
-bash: cd: ./-: Not a directory 
```
**Nhận xét:** Không phải folder -> là file

### Bước 4 - Đọc file
```bash
cat ./-
```
**Output**
```
263JGJPfgU6LtdEvgfWU1XP5yac29mFx 
```
---

## 🚩 Password tìm được

```
263JGJPfgU6LtdEvgfWU1XP5yac29mFx 
```

> ⚠️ **Lưu ý:** Password thay đổi theo thời gian — đừng dựa vào password này, hãy tự giải để lấy password hiện tại.

---

## 📖 Bài học rút ra (Takeaways)

1.Đọc kỹ đề bài "đã ghi là file - located in home directory"
2.  
---

## 🔗 Tài liệu tham khảo
google search dashed filename in linux 

---

*Writeup bởi trantrung1291(https://github.com/trantrung1291) · Học cybersecurity từ đầu · [Xem tất cả writeups](../../README.md)*
