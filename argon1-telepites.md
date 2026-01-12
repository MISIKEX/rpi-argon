# Ideiglenes letölés, telepítés majd törlés

tmp=$(mktemp) && \
curl -fsSL https://raw.githubusercontent.com/MISIKEX/rpi-argon/main/argon1.sh -o "$tmp" && \
chmod +x "$tmp" && \
sudo bash "$tmp" && \
rm -f "$tmp"
