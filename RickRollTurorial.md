
# 🎩 RickRoll Tutorial ( best in the World )

Make your Windows **PowerShell** feel magical: type `rick` and a fresh **cmd** window pops up to stream the classic ASCII animation via `curl`.

This guide is **step-by-step**, **corporate‑network friendly**, and sprinkled with tips, gotchas, and rollback instructions. No prior PowerShell knowledge required.

> 🗓️ Last updated: 2026‑01‑07
>
> 🧰 Works on: **Windows 10/11**, PowerShell **5.x** and **7.x**.
>
> 🔐 Network‑aware: Handles the common Schannel revocation error (corporate firewalls/proxies) with a safe, opt‑in flag.

---

## 🌟 What you’ll get
- A PowerShell function named **`rick`**.
- It opens a **new `cmd.exe` window** and runs:
  ```cmd
  curl --ssl-no-revoke https://ascii.live/rick
  ```
- The window **stays open** so you can enjoy the animation.

Why `cmd`? Because in PowerShell the command `curl` is historically an **alias for `Invoke-WebRequest`**, which behaves differently than real `curl`. In `cmd`, `curl` resolves to the **real `curl.exe`** that ships with Windows 10/11, so everything “just works”.

---

## 🏁 Quick Start (TL;DR)
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
# Opens a new cmd window and runs curl, keeping the window open
function rick {
    Start-Process cmd.exe -ArgumentList '/k', 'title RickRoll && curl --ssl-no-revoke https://ascii.live/rick'
}
```

Reload your profile (or open a new PowerShell):

```powershell
. $PROFILE
```

Now type:

```powershell
rick
```

🎉 A new **cmd** window appears and streams the ASCII animation.🎉

---



Happy RickRolling! 🕺


