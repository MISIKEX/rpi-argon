# 🛠️ RPi Argon One - Egyéni Telepítők

![Status](https://img.shields.io/badge/Status-Private_Use-orange)
![Platform](https://img.shields.io/badge/Platform-Raspberry_Pi-red)

### ⚠️ Fontos Figyelmeztetés
> **Megjegyzés:** Ez a repozitórium **privát használatra** készült. A tartalom a saját eszközeink specifikációihoz van igazítva. Csak saját felelősségre használd!

---

## Helyi fejlesztés natív Ubuntun

A fejlesztői munkafa `/home/misikex/Projektek/rpi-argon`, a munkaállomás natív Ubuntu 26.10 Desktop GNOME, `misikex` felhasználóval és `codex` gépnévvel. A grafikus Codexből a projekt gyökerében futtasd a natív Linux Git-, Bash-, Python- és statikus ellenőrzéseket. A napi fejlesztéshez nincs WSL- vagy PowerShell-köztes réteg; Windows csak távoli kliens lehet.

A rendszer `/usr/bin/python3` interpreterét (Ubuntu Python 3.14.8) ne cseréld le. A külön `python3.15` az uv által kezelt CPython 3.15.2; szükséges helyi Python-függőséget elkülönített virtuális környezetbe telepíts. Ezek a munkaállomás eszközei, nem új minimumkövetelmények a Pi telepítőjéhez.

A telepítő célja továbbra is a saját Raspberry Pi hardver. A teljes telepítőt ne futtasd a fejlesztői munkaállomáson: a Pi OS, boot-, GPIO-, kijelző-, Wayland- és eszközfüggő viselkedést csak a külön kijelölt céleszköz igazolhatja. Hardvertelepítő csak külön telepítési kérésre futtatható; a helyi klón létrehozása nem telepítési felhatalmazás.


## Telepítési célok és belépési pontok

Az alábbi parancsokat csak a kijelölt Raspberry Pi-n, a repó gyökeréből használd.
A hardverpárosítás forrása a mellékelt [V2 kézikönyv](argon-one-v2/argon-one-v2.pdf)
és [V3 kézikönyv](argon-one-v3/argon-one-v3.pdf); az OS-feltételek a tényleges
telepítőforrásokból származnak.

| Cél | Helyi belépési pont | Hardver és OS-előfeltétel |
| --- | --- | --- |
| Argon ONE Pi 4 V2 | `sudo bash argon-one-v2/argon1.sh` | Raspberry Pi 4 és hozzá való V2 ház; Pi-n futó, apt/dpkg-alapú rendszer, GPIO/I²C és írható Pi bootkonfiguráció. |
| Argon ONE V3 / M.2 NVMe PCIe | `sudo bash argon-one-v3/argon1.sh` | Raspberry Pi 5 és hozzá való V3 ház/bővítő; ugyanilyen Pi-rendszer, a Pi 5 ágon NVMe/PCIe- és USB-tápbeállításokkal. |
| V3 EEPROM-alapbeállítás | `sudo bash argon-one-v3/argon-eeprom.sh` | A kijelölt Pi-n Raspberry Pi OS és létező `/usr/bin/rpi-eeprom-config`; a script `raspbian` vagy `debian` OS-azonosítót fogad el az EEPROM-ághoz. |

A két `argon1.sh` jelenleg azonos tartalmú; a könyvtárnév nem automatikus
hardvervédelem. A scriptek felismernek `raspbian`, `debian` és `ubuntu`
OS-azonosítót, de nem tartalmaznak teljes, tesztelt OS-verziómátrixot.
Az Ubuntu-ág létezése nem igazolja minden Ubuntu/Pi-kombináció támogatását;
az EEPROM-lépés más OS-ágon kimarad, Raspberry Pi OS használatát kérve.

Futtatás előtt legyen működő internet, helyes rendszeridő, `bash`, `curl`,
`wget`, `sudo`/rendszergazdai hozzáférés, `apt-get`/`dpkg-query` és `systemd`.
A fő telepítők többek között `python3-libgpiod`, `python3-smbus` és `i2c-tools`
csomagokat telepítenek, boot-/I²C-/soros konfigurációt módosítanak, majd Argon
rendszerszolgáltatást indítanak. Az EEPROM-ág `apt-get update`,
`apt-get upgrade -y` és `rpi-eeprom-update` parancsot is futtat.
A V3 kézikönyv az EEPROM-beállítás után, majd a vezérlőtelepítés után is újraindítást ír elő.
A tényleges ventilátor-, gomb-, boot- és EEPROM-működés csak a célhardveren igazolható.

## Külső letöltések és ismételhetőség

A `argon1-info` és `argon-eeprom-info` fájlok Bash-indítóreceptek:
a megfelelő scriptet a GitHub `main` ágáról ideiglenes fájlba töltik,
majd `sudo bash` alatt futtatják. Ellenőrzött helyi klón esetén a fenti
közvetlen belépési pontok használhatók.

A fő telepítők további Python-/shellfájlokat, systemd-unitokat és képi asseteket
töltenek le a `https://download.argon40.com` címről; az EEPROM-script innen kéri az
`argon-rpi-eeprom-config-default.py` segédet. A pontos források:
[V2 telepítő](argon-one-v2/argon1.sh), [V3 telepítő](argon-one-v3/argon1.sh),
[EEPROM-telepítő](argon-one-v3/argon-eeprom.sh).
Az időellenőrzés a `http://worldtimeapi.org/api/ip.txt` szolgáltatást is használja.
A gyártói letöltések nincsenek ebben a repóban verzióhoz vagy hashhez rögzítve:
a klón önmagában nem teljes offline telepítő és nem garantál változatlan külső tartalmat.

A natív Ubuntu fejlesztői környezet visszaállításához a
[központi munkaállomás-helyreállítási útmutató](https://github.com/MISIKEX/server-admin-mcp/blob/main/.github/docs/WORKSTATION_REINSTALL.md)
tartozik. A Pi hardvertelepítése ettől külön művelet; a munkaállomáson csak a forrás olvasása
és statikus ellenőrzése végezhető.
