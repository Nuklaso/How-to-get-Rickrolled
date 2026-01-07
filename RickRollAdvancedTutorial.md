# 🎩 RickRoll++ — (PowerShell → opens CMD, launches YouTube, waits 15s, then shuts down PC)
---

## 🌟 Goal
When you type `rickroll` in **PowerShell**, it will automatically open a **new `cmd.exe` window** that:
1. launches the YouTube page (Rick Astley 😉) in your default browser,
2. waits **15 seconds**,
3. shuts down the PC.

Why `cmd`? In PowerShell, `curl` is often an alias for `Invoke-WebRequest`. For YouTube, we need the **browser** — `cmd` handles this easily with `start`. Also, `shutdown` works reliably in `cmd`.

---

## 🏁 Quick Start
Open **PowerShell** and run these commands in order:

```powershell
# 1) Check if a profile exists
Test-Path $PROFILE

# 2) Create profile if needed
New-Item -Path $PROFILE -ItemType File -Force

# 3) Open the profile in Notepad
notepad $PROFILE
```

Paste this into the file and **save**:

```powershell
# Function: rickroll
# Opens a new CMD window, launches YouTube, waits 15s, then shuts down the PC
function rickroll {
    Start-Process cmd.exe -ArgumentList '/k', 'title RickRoll && start "" https://www.youtube.com/watch?v=dQw4w9WgXcQ && timeout /t 15 /nobreak && shutdown /s /t 0'
}
```

Reload your profile (or open a new PowerShell window):

```powershell
. $PROFILE
```

Test:

```powershell
rickroll
```

🎉 A new **cmd** window opens, your browser launches the YouTube link, after 15s the PC shuts down.
