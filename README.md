
# 🕷️ Daily Bugle — TryHackMe Write-Up

## 📌 Machine Information

- Platform: TryHackMe  
- Room: Daily Bugle  
- Difficulty: Hard  
- Target: Joomla CMS  
- Exploit Chain: SQLi → Admin → Reverse Shell → Privilege Escalation  

---

# 🔍 Enumeration

## Nmap

```bash
nmap -sC -sV -p- -T4 TARGET_IP
```

Key findings:

- Apache Web Server
- Joomla CMS
- Vulnerable version detected
- SQL Injection vulnerability present

---

# 📂 Directory Enumeration

```bash
gobuster dir -u http://TARGET_IP -w /usr/share/wordlists/dirb/common.txt -x php,txt,html
```

Interesting paths:

- /administrator
- /components
- /templates

---

# 💉 Exploitation

- Joomla SQL Injection used
- Extracted user credentials
- Cracked password hash

---

# 🐚 Reverse Shell

Injected PHP reverse shell into Joomla template.

Listener:

```bash
nc -lvnp 4444
```

---

# 🔍 Post Exploitation

Extracted database credentials from:

```bash
/var/www/html/configuration.php
```

---

# 🚀 Privilege Escalation

Used sudo permission on:

```bash
/usr/bin/yum
```

Spawned root shell using plugin technique.

---

# 🏁 Flags

## User Flag

```
27a260fe3cba712cfdedb1c86d80442e
```

## Root Flag

```
eec3d53292b1821868266858d7faf679
```

---

# 🧠 Skills Demonstrated

- Web exploitation
- SQL Injection
- Password cracking
- Reverse shells
- Linux privilege escalation
- Post-exploitation

