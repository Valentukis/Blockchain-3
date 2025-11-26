1. Libbitcoin instaliavimas
  Is pradziu buvo bandyta per WSL Ubuntu, taciau kilo problemu del nesuderinamu Boost versiju. Tad naudojau savo paruosta VM su Docker, per kuri sukuriau konteineri senesniu Ubuntu pagrindu ir visiskai "svariu" environment. Panaudojus sias komandas, sekmingai instaliavau libbitcoin:
apt update
apt install -y build-essential autoconf automake libtool pkg-config git wget
wget https://raw.githubusercontent.com/libbitcoin/libbitcoin/version3/install.sh
chmod +x install.sh
./install.sh --prefix=/usr/local --build-boost --disable-shared

Taip pat reikejo paleisti komanda : export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig

Tai atlikus buvo sukurtas merkle.cpp failas, taciau reikejo pakeisti headeri is bitcoin.hpp i system.hpp

Galiausiai, kompiliavau ir testavau koda (naudojau g++, taip pat naujense versija naudoja pkg-config "libbitcoin-system"):
g++ -std=c++11 merkle.cpp -o merkle $(pkg-config --cflags --libs libbitcoin-system)  

(veliau sukelti nuotraukas)
