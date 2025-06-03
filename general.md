
## 📘 Knowledge List

---

### 1. 🐚 What Is a Shell?
> A **shell** is a program that lets humans **interact with other programs** via typed commands.
- Example: Bash, Zsh, FTP shell, Python shell
- Shells can be **REPLs** or non-REPL

---

### 2. 🔁 What Is a REPL?
> **Read-Eval-Print Loop** — an interactive environment that:
1. **Reads** your input  
2. **Evaluates** it  
3. **Prints** the result  
4. Loops again  

✅ Python, Node.js, and DuckDB all offer REPLs.

```
$ python
>>> 2 + 2
4
```

---

### 3. 🟡 Node vs JavaScript
| Concept      | Role                              |
|--------------|-----------------------------------|
| JavaScript   | The **language**                  |
| Node.js      | The **runtime** to run JS outside a browser |

- Like Python's CPython interpreter  
- You can write `.js` files and run: `node file.js`

---

### 4. ⚙️ What Is an Interpreter?
> A program that **executes code line by line**.
- Example: Python uses **CPython**
- Others: PyPy, Jython, IronPython

Check your interpreter:
```python
import platform
platform.python_implementation()
```

---

### 5. 🧠 Python Interpreters (Runtimes)
| Interpreter   | Platform             |
|---------------|----------------------|
| CPython       | Default              |
| PyPy          | Fast (JIT compiled)  |
| Jython        | On Java (JVM)        |
| IronPython    | On .NET              |
| MicroPython   | Microcontrollers     |

---

### 6. 🧠 What Is a Runtime?
> A **runtime** is the environment that runs your code and provides:

- Memory management  
- Execution engine  
- I/O interfaces  
- Scheduler, event loop  

| Component        | Role                        |
|------------------|-----------------------------|
| Parser           | Understands your code       |
| Interpreter/VM   | Executes code               |
| Memory Manager   | Manages RAM                 |
| Native APIs      | Talks to OS (e.g., files)   |

✅ Python, Node.js, DuckDB all have runtimes.

---

### 7. 📡 What Is a Protocol?
> A **protocol** is a set of rules that define how computers talk to each other.

🧪 Examples:
- **FTP**: Send files (`USER`, `GET`)
- **HTTP**: Web requests (`GET /index.html`)
- **SMTP**: Email

🧠 Protocols are like languages for machines.  
Many are string-based (like a command conversation).

---

### 8. 📂 What Is FTP?
> **File Transfer Protocol** – a way to **send/receive files** between computers over a network.

| Command        | Meaning                     |
|----------------|-----------------------------|
| `USER`         | Login name                  |
| `PASS`         | Password                    |
| `LIST`         | Show files                  |
| `RETR file`    | Download file               |

👤 Example:
```bash
ftp ftp.example.com
Name: anonymous
Password: (your email)
```

---

### 9. 🧠 What Is an API? (vs. Shell)
> An **API** is a set of rules for **programs to talk to programs**.

| Concept    | Shell                          | API                             |
|------------|---------------------------------|----------------------------------|
| For        | Humans                          | Programs                         |
| Used by    | Typing in terminal              | Writing code                     |
| Example    | `ftp> get file.txt`             | `ftp.get("file.txt")` (Python)   |

🧠 Summary:
> A **shell** lets humans talk to programs.  
> An **API** lets programs talk to programs.

---

### 10. 🖥️ What Does “Installing a Server” Mean?
> Installing a **server** = installing a program that:
- Opens a network **port**
- Waits for connections
- Responds using a **protocol**

🧪 Example:
```bash
brew install vsftpd         # Install FTP server
sudo vsftpd                 # Start the server
ftp localhost               # Connect from client
```

---

### 11. 🏗️ Setup an FTP Server on macOS (vsftpd)

| Step | Command / Action                                                                 |
|------|----------------------------------------------------------------------------------|
| ✅ Install        | `brew install vsftpd`                                               |
| 🔍 Find config    | `ls /opt/homebrew/etc/vsftpd.conf`                                  |
| 🛠️ Create jail    | `sudo mkdir -p /opt/vsftpd/empty && sudo chown root:wheel ...`      |
| ⚙️ Update config  | Set `secure_chroot_dir=/opt/vsftpd/empty` in `vsftpd.conf`          |
| 🚀 Start server   | `sudo /opt/homebrew/sbin/vsftpd /opt/homebrew/etc/vsftpd.conf`      |
| 🔁 Test login     | `ftp localhost` → `220 (vsFTPd 3.0.5)` prompt expected              |

✅ You now know how to start and test a local server securely.

---

## 🔧 Git Essentials

### 🔄 What Is `--set-upstream-to`?

It connects a **local branch** to a **remote branch**, so Git knows how to sync them.

---

### 🧱 Setup via Push
```bash
git push -u origin my-feature
```
- Pushes to `origin/my-feature`
- Sets it as upstream for local `my-feature`

---

### ⚙️ Manual Setup
```bash
git branch --set-upstream-to=origin/main
```
Or, if names differ:
```bash
git branch --set-upstream-to=origin/dev main
```

---

### 🔍 Why Do You Need Upstream?

| Command       | Why it needs upstream                          |
|---------------|-------------------------------------------------|
| `git push`    | Knows where to push                            |
| `git pull`    | Knows where to fetch/merge from                |
| `git status`  | Shows tracking: ahead/behind                   |

---

### 📌 Why Does a *Branch* Need an Upstream?

So Git can:
- Track changes
- Show diffs
- Pull/push without repeating remote names

Otherwise, you'd have to do:
```bash
git pull origin dev
git push origin dev
```
... every time.

✅ With upstream, just use `git pull` and `git push`.

---

