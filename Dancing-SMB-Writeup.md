# 🕺 HTB Starting Point - Dancing (SMB Enumeration)
> 🗂 Category: SMB  
> 🛠 Difficulty: Easy  
> 📅 Date: [ضع التاريخ هنا]

---

## 🎯 Objective  
Enumerate and exploit an SMB share on the target machine `Dancing` to retrieve the root flag.

---

## 🛠 Tools Used
- nmap
- smbclient

---

## 🔍 Enumeration

### 🔎 What does the acronym SMB stand for?
**SMB = Server Message Block**  
It is a network protocol used for sharing files, printers, serial ports, etc. between computers.

---

### 🔌 What port does SMB use?
**Port 445** (modern SMB over TCP/IP)  
Older versions also used ports 137–139 (NetBIOS over TCP/IP).

---

### 📡 What is the service name for port 445?
**microsoft-ds**

---

### 📂 Enumerating SMB Shares
Used the following command to list shares:
```bash
smbclient -L \\10.129.242.98\
```

**Switch used:** `-L`  
This lists all available shares on the target.

---

## 📁 Accessing Shares

- Found **4 shares**.
- Successfully accessed the share named **WorkShares** with **blank password**:
```bash
smbclient \\10.129.242.98\WorkShares
```

---

## 💾 Downloading Files

From within the SMB shell, used:
```bash
get [filename]
```
To download the available files.

---

## 🏁 Capturing the Flag

Opened the downloaded file and found the root flag:
```bash
5f61c10dffbc77a704d76016a22f1664
```

---

## 🧠 Lessons Learned

- SMB enumeration is essential in network penetration testing.
- Misconfigured shares with anonymous access can lead to full compromise.
- `smbclient` is a powerful tool for accessing and downloading SMB resources.

---

## 📸 Screenshots (Optional)
> يمكنك إضافة صور مثل:
- قائمة الشيرز من smbclient
- صورة التوصل إلى WorkShares
- صورة الـ flag بعد الوصول إليه

---

## 🔗 References
- [SMB Protocol - Wikipedia](https://en.wikipedia.org/wiki/Server_Message_Block)
- [smbclient man page](https://www.samba.org/samba/docs/current/man-html/smbclient.1.html)

---

✅ **Writeup by:** [محمد حمدي]