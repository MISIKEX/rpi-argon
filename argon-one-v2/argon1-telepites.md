# 🛠️ RPi Argon One - Egyéni Telepítő

![Status](https://img.shields.io/badge/Status-Private_Use-orange)
![Platform](https://img.shields.io/badge/Platform-Raspberry_Pi-red)

Ez a tároló az **argon1.sh** szkript módosított változatát tartalmazza. Elsősorban saját projektek fejlesztéséhez és egyéni igényeink kiszolgálására hoztuk létre.

---

### ⚠️ Fontos Figyelmeztetés
> **Megjegyzés:** Ez a repozitórium **privát használatra** készült. A tartalom a saját eszközeink specifikációihoz van igazítva. Csak saját felelősségre használd!

---

### 🚀 Gyors Telepítés
Ha szeretnéd futtatni a telepítőt anélkül, hogy felesleges fájlokat hagynál a rendszereden, használd az alábbi, "egyvonalas" parancsot. 

Ez a módszer létrehoz egy ideiglenes fájlt, letölti a kódot, végrehajtja a telepítést, majd automatikusan törli a nyomokat:

```bash
tmp=$(mktemp) && \
curl -fsSL [https://raw.githubusercontent.com/MISIKEX/rpi-argon/main/argon1.sh](https://raw.githubusercontent.com/MISIKEX/rpi-argon/main/argon1.sh) -o "$tmp" && \
chmod +x "$tmp" && \
sudo bash "$tmp" && \
rm -f "$tmp"
