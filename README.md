# 🔐 linux-system-management-2

> **Project 2 of 3** in the Linux System Management series  
> Focus: Shadow file, user states, password locks, ulimit, and file ops

---

## 📌 Objectives

- Understand Linux user authentication and shadow file structure
- Analyze locked, disabled, and unset passwords in `/etc/shadow`
- Practice safe file operations using `mv -u` and `mkdir -p`
- Configure and verify user limits with `ulimit`

---

## 📁 Project Structure

```
linux-system-management-2/
├── README.md
├── outputs/
│   ├── 01a-shadow-passwd-d.txt
│   ├── 01b-shadow-passwd-l.txt
│   ├── 02-ulimit-output.txt
│   └── (03 and 04 will be added next)
└── screenshots/
    ├── 01a-passwd-d-shadow.png
    ├── 01b-passwd-l-shadow.png
    ├── 02-ulimit-output.png
    ├── 02b-ulimit-focused.png
    └── 02c-ulimit-test-dd.png
```

---

## ⚙️ Command Execution & Results

### 1️⃣ Examine `/etc/shadow` Password States

```bash
# Create user and remove password
sudo useradd testuser1
sudo passwd -d testuser1
sudo grep testuser1 /etc/shadow

# Lock the user account
sudo passwd -l testuser1
sudo grep testuser1 /etc/shadow
```

📄 [`01a-shadow-passwd-d.txt`](outputs/01a-shadow-passwd-d.txt)  
📄 [`01b-shadow-passwd-l.txt`](outputs/01b-shadow-passwd-l.txt)  

📷 ![01a-passwd-d-shadow](screenshots/01a-passwd-d-shadow.png)  
📷 ![01b-passwd-l-shadow](screenshots/01b-passwd-l-shadow.png)

---

### 2️⃣ Set and View `ulimit` Resource Limits

```bash
ulimit -a
ulimit -u
ulimit -n
```

📄 [`02-ulimit-output.txt`](outputs/02-ulimit-output.txt)  
📷 ![02-ulimit-output](screenshots/02-ulimit-output.png)  
📷 ![02b-ulimit-focused](screenshots/02b-ulimit-focused.png)

---

### 🧪 Deep Dive: Enforcing File Size Limit with `ulimit -f`

To simulate a file size enforcement scenario, I temporarily limited the shell's max file size:

```bash
ulimit -f 100
dd if=/dev/zero of=testfile bs=1M count=2
```

📸 ![02c-ulimit-test-dd](screenshots/02c-ulimit-test-dd.png)

> ✅ This triggered the expected failure:  
> `File size limit exceeded (core dumped)`

Restored default limit afterward:

```bash
ulimit -f unlimited
rm -f testfile
```

---

## ✅ Summary

This project reinforces Linux+ exam skills around user account management, shadow file analysis, and essential file operations.  
Screenshots and command outputs offer a complete trace of each concept in practice.

---

## 🧠 Next Project

→ [linux-system-management-3](https://github.com/carlos-tech-ops/linux-system-management-3)  
Focus: SSH, PXE, DNS, name resolution, and network boot behavior
