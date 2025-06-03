### 🛡️ Blue

**Room:** [Blue — TryHackMe](https://tryhackme.com/room/blue)  
**Status:** ✅ Completed  
**Date:** *03 June 2025*

---

### 🎯 Objective  
Exploit a vulnerable Windows machine using MS17-010 (EternalBlue), gain remote access, escalate privileges, dump password hashes, and recover planted flags.

---

### 🗝️ Key Concepts  
- **MS17-010 / EternalBlue** — A critical SMB vulnerability in Windows XP/7/2008 systems, allowing remote code execution.  
- **Metasploit Framework** — Used to scan, exploit, and manage post-exploitation tasks.  
- **Shell to Meterpreter Upgrade** — Using a Metasploit post module to convert a basic shell to a Meterpreter session.  
- **Privilege Escalation** — Using `getsystem` to obtain NT AUTHORITY\SYSTEM access.  
- **Process Migration** — Switching to a SYSTEM-owned process for more stable control.  
- **Hashdump & Cracking** — Dumping NTLM password hashes and cracking them offline.

---

### 🛠️ Tools Used  
- `nmap` — For scanning ports and identifying the SMB service.  
- `exploit/windows/smb/ms17_010_eternalblue` — Main exploit used via Metasploit.  
- `set payload windows/x64/shell/reverse_tcp` — Payload for creating a reverse shell.  
- `post/multi/manage/shell_to_meterpreter` — Module to upgrade shell to Meterpreter.  
- `hashdump` — Dumps local SAM password hashes.  
- `John the Ripper` — Used to crack the password hash.  

---

### ⚠️ Challenges Faced  
- Remembering to `set RHOSTS` before running the exploit.  
- Meterpreter migration was unstable at times — had to retry on different process IDs.  

---

### 🧠 What I Learned  
- EternalBlue (MS17-010) is still one of the most famous vulnerabilities in Windows history.  
- A simple reverse shell can be upgraded to a full Meterpreter session with the right module.  
- Being SYSTEM doesn't always mean your process is — migration matters.  
- Hashdump provides real password hashes, and cracking them teaches how weak passwords can be exposed quickly.  
- Important Windows data can be found in places like the root directory, SAM database, and user folders.

---

### 🔐 Cracked Credentials  
- **User:** Jon  
- **Password Hash:** `aad3b435b51404eeaad3b435b51404ee:35b69fa7495cf56b4c8f59d1b621c198`  
- **Cracked Password:** `alqfna22`  

---

### 🏁 Flags Found  
- **Flag 1:** `flag{access_the_machine}`  
- **Flag 2:** `flag{sam_database_elevated_access}`  
- **Flag 3:** `flag{admin_documents_can_be_valuable}`

---

### 🌐 Real-World Application  
> EternalBlue has been used in real-world attacks, including WannaCry and NotPetya. Understanding how it works gives insight into how outdated systems become entry points for attackers — and why patching is critical.

---

### 💭 Reflections  
- This room was a solid step back after the difficulty of *Metasploit: Meterpreter*. It helped me regain some confidence.  
- The walkthrough format made EternalBlue exploitation feel much clearer and more manageable.  
- Seeing how quickly a machine can be taken over with an unpatched vulnerability reinforces how important basic hygiene like updates really is.  
- I feel much better coming out of this room than I did going into the last one.
