---
title: "Installation problems solving"
taxonomy:
  category:
    - docs
---

## "Installation failed" error in macOS Catalina

During the installation you can face an error like this:

<img src="https://cdn.adguard.com/public/Adguard/kb/MAC/macerrorscreenEN.png" width="600" />

Follow this instruction to solve the problem:

1. Restart your Mac
2. As your Mac restarts, press and hold down the _Command(⌘) + R_ keys immediately upon hearing the startup chime. Hold the keys until the Apple logo appears to get the computer into Recovery mode.
3. From the top bar select _Utilities_ > _Terminal_, and execute this command: `csrutil disable`
4. Restar the Mac and log into Administrator's profile
5. Open the Finder window and select from the top bar _Go_ > _Go to Folder_ and type `~/private/`
6. Create a folder named _tmp_ and type in your password
7. Launch AdGuard installation

As the installation is completed, restart your Mac in Recovery mode using the instruction above and execute `csrutil enable` command in Terminal to enable system protection.
