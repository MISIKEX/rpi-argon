# Argon One Telepítő

Ez a szkript létrehoz egy ideiglenes könyvtárat, letölti a telepítőt, futtatja azt, majd takarításként törli az ideiglenes fájlt.

### Telepítés futtatása:

Másold be az alábbi parancsot a terminálba:

```bash
tmp=$(mktemp) && \
curl -fsSL [https://raw.githubusercontent.com/MISIKEX/rpi-argon/main/argon1.sh](https://raw.githubusercontent.com/MISIKEX/rpi-argon/main/argon1.sh) -o "$tmp" && \
chmod +x "$tmp" && \
sudo bash "$tmp" && \
rm -f "$tmp"
