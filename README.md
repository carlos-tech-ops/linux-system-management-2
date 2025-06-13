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
│   ├── 01-shadow-file.txt
│   ├── 02-ulimit-output.txt
│   ├── 03-mv-test-output.txt
│   └── 04-mkdir-test-output.txt
└── screenshots/
    ├── 01-shadow-file.png
    ├── 02-ulimit-output.png
    ├── 03-mv-test-output.png
    └── 04-mkdir-test-output.png
```

---

## ⚙️ Command Execution & Results

### 1️⃣ Examine `/etc/shadow` Password States

```bash
sudo cat /etc/shadow | grep testuser
```

Try with a locked, unlocked, and passwordless test user.  
Interpret fields like `!`, `!!`, and empty.

📄 [`01-shadow-file.txt`](outputs/01-shadow-file.txt)  
📷 ![01-shadow-file](screenshots/01-shadow-file.png)

---

### 2️⃣ Set and View `ulimit` Resource Limits

```bash
ulimit -a
ulimit -u
ulimit -n
```

📄 [`02-ulimit-output.txt`](outputs/02-ulimit-output.txt)  
📷 ![02-ulimit-output](screenshots/02-ulimit-output.png)

---

### 3️⃣ Test `mv -u` (Move if Newer)

```bash
touch oldfile.txt
sleep 2
echo "Newer version" > newfile.txt
mv -u newfile.txt oldfile.txt
```

📄 [`03-mv-test-output.txt`](outputs/03-mv-test-output.txt)  
📷 ![03-mv-test-output](screenshots/03-mv-test-output.png)

---

### 4️⃣ Test `mkdir -p` (Recursive Create)

```bash
mkdir -p /tmp/testdir1/testdir2/testdir3
ls -R /tmp/testdir1
```

📄 [`04-mkdir-test-output.txt`](outputs/04-mkdir-test-output.txt)  
📷 ![04-mkdir-test-output](screenshots/04-mkdir-test-output.png)

---

## ✅ Summary

This project reinforces Linux+ exam skills around user account management, shadow file analysis, and essential file operations.  
Screenshots and command outputs offer a complete trace of each concept in practice.

---

## 🧠 Next Project

→ [linux-system-management-3](https://github.com/carlos-tech-ops/linux-system-management-3)  
Focus: SSH, PXE, DNS, name resolution, and network boot behavior
