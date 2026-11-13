# 🛠️ RPi Argon One - Egyéni Telepítők

![Status](https://img.shields.io/badge/Status-Private_Use-orange)
![Platform](https://img.shields.io/badge/Platform-Raspberry_Pi-red)

### ⚠️ Fontos Figyelmeztetés
> **Megjegyzés:** Ez a repozitórium **privát használatra** készült. A tartalom a saját eszközeink specifikációihoz van igazítva. Csak saját felelősségre használd!

---

## Helyi fejlesztés natív WSL-ben

A fejlesztői munkafa `/home/codex/projects/rpi-argon` az `Ubuntu-26.04` alatt. Git-, Bash-, Python- és statikus ellenőrzéseket natív Linux-eszközökkel futtass; a Windows-native Codex Desktopból a `C:\- CODEX\RENDSZER\WSL.ps1` indító ezt a `-WorkingDirectory` értéket használja. A meglévő Windows-kapcsolatok megmaradnak, automatikus munkafa-szinkron nincs.

A telepítő célja továbbra is a saját Raspberry Pi hardver. A teljes telepítőt ne futtasd WSL-ben: a Pi OS, boot-, GPIO-, kijelző-, Wayland- és eszközfüggő viselkedést csak a külön kijelölt céleszköz igazolhatja. A helyi klón létrehozása nem telepítési felhatalmazás.
