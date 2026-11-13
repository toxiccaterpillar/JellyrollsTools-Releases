# Jellyroll's Tools

A free toolbox for **Toontown Rewritten** on Windows: a multiboxer, Fishboxer (cast with several Toons at once), a multi-account launcher, the Cog Health overlay, and My Toon, Guide, Battle Calc and Suit Planner pages that read your Toon from the game.

> Not affiliated with or endorsed by Toontown Rewritten or Disney. Toontown Rewritten is a trademark of its owners.

**Download:** the latest version is on the [Releases page](https://github.com/toxiccaterpillar/JellyrollsTools-Releases/releases/latest). Download only from there.

---

## Is it safe?

Short answer: it only works with your own game windows and your own computer, it has no ads and no tracking, and it never sends your passwords or files anywhere. The details are below so you can check for yourself.

### What it does
- **Reads your Toon from the game's own Companion App API**, which runs on your own computer (`localhost`, ports 1547–1552). The game asks you once to allow it.
- **Sends keyboard and mouse input to your Toontown windows** (multiboxing, Fishboxer), the same input you would give with your own keyboard and mouse.
- **Looks at your screen** for the Cog Health overlay and for finding bobbers in Fishboxer. The pictures are looked at on your computer and thrown away. They are not saved or sent anywhere.
- **Reads each game's own log file** (Multi Manager, Cog Overlay). The log shows the toon's name, whether the game lost its connection and why, how fast it runs, and which Cog HQ facility the toon is in. It only reads; it works for any Toontown Rewritten window, including ones not started here. The Cog Overlay uses the facility to name the right boss (Factory Foreman, Mint Auditor, Office Clerk, Club President).
- **Checks that your game files are up to date** (Multi Manager). It reads the files in your Toontown Rewritten folder, works out their fingerprints and compares them with the file list Toontown Rewritten publishes for its official launcher. It only looks: if an update is needed it tells you to open the official launcher once.
- **Starts the game for you** (Multi Manager / Multitoon Launcher) by logging in with Toontown Rewritten's official login API.

### What it does *not* do
- It does **not** read or change the game's memory, inject code into the game, or modify any game files.
- It does **not** send your passwords, accounts, screenshots, keystrokes or settings to anyone.
- It has **no ads, no tracking and no analytics**.
- It does **not** record what you type. Windows needs a program to listen for keys to offer hotkeys (F2, F3, F12 and the multiboxing keys), but the keys are only acted on while a Toontown window is in use.

### Everywhere it connects to the internet
| What | Where |
|---|---|
| Your Toon's information | the game on your own PC (`localhost`) |
| Logging in to launch the game | `www.toontownrewritten.com` (the official login API) |
| Invasions, Field Offices, Doodles, population, Silly Meter, release notes, game status, the Cavalcade, Riggy's donations, racing leaderboards | `www.toontownrewritten.com` (the official public APIs) |
| The list of the newest game files (to check yours are up to date) | `cdn.toontownrewritten.com` (the file list the official launcher uses) |
| Toon pictures | `rendition.toontownrewritten.com` (the game's own picture service) |
| Guide articles and pictures | `toontownrewritten.wiki` |
| Looking for a newer version | `api.github.com` and the release page on GitHub |

Nothing else.

### Why it asks for administrator rights
Windows only lets a program send keys and clicks to a game window that runs at the *same or a lower* level than itself. The Toontown Rewritten game can end up running as administrator (a game started by an administrator launcher runs as administrator), so Jellyroll's Tools asks for administrator rights once when it opens, to be able to talk to those windows. It does not install anything.

### Your passwords (Multi Manager / Multitoon Launcher)
- Passwords are stored in **Windows Credential Manager**, the same place Windows keeps your other saved passwords. They are **not** written to the program's settings file or to its log.
- The settings file only holds your usernames, which accounts are ticked, and the path to the game.
- Passwords are only ever sent to Toontown Rewritten's official login address. Removing an account in Account Manager also deletes its saved password.
- The game's login cookie is never written to the log.
- You can see and delete everything yourself: Windows search → **Credential Manager** → **Windows Credentials** → look for `MultiLauncherService`.

### What it saves on your PC
- Settings: `%APPDATA%\JellyrollsTools\`
- Launcher: `%APPDATA%\MultiLauncher\` (usernames, a log, which game belongs to which account)
- Toon pictures it has downloaded, in the same Jellyroll's Tools folder.
- The fingerprints of your game files from the last update check (`game_hashes.json`), so the next check is quick.
- `crash.log` in the Jellyroll's Tools folder: if the program hits an unexpected error, the details are written there.

Delete those folders and the saved passwords (above) and nothing of the program is left behind.

### Updates
The program can look for newer versions on its GitHub release page. When you choose to update, it downloads the new `.exe`, checks the file's **SHA-256** against the one GitHub recorded for that release, and only then swaps it in.

---

## Checking your download

Every release on the Releases page shows a **SHA-256** for the `.exe`. To compare it with your file, open PowerShell in the folder you downloaded it to and run:

```powershell
Get-FileHash .\JellyrollsTools.exe -Algorithm SHA256
```

(Use the real file name.) The two should match exactly. You can also upload the file to [VirusTotal](https://www.virustotal.com) to scan it with many antivirus programs.

### If your antivirus or Windows warns about it
Programs that send keys to other windows and ask for administrator rights are often flagged by antivirus software, even when they're harmless. That is called a *false positive*.

- **"Windows protected your PC" (SmartScreen):** this appears for any program Windows hasn't seen many times. Choose **More info → Run anyway** only if you downloaded it from the Releases page above and the SHA-256 matches.
- **Your antivirus quarantines it:** check the file against VirusTotal first, then add the Jellyroll's Tools folder to your antivirus' exceptions.

If you're not comfortable, don't run it. Questions are welcome in the Issues tab first.

---

## Getting started
1. Download the `.exe` from the Releases page and put it in a folder of its own.
2. Run it and accept the administrator prompt.
3. Start Toontown Rewritten and log in. The first time a tool reads your Toon, the game asks you to **allow** it.
4. Press **Help** in the program's top bar for every feature and hotkey.

## Problems or ideas
Open an issue on this repository and say which Windows version you use, what you pressed, and what you expected. Screenshots help a lot. If the program closed or misbehaved, attach `%APPDATA%\JellyrollsTools\crash.log` if it exists.
