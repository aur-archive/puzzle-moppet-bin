# Maintainer: David Becker <david dot becker at gmx dot org>

pkgname=puzzle-moppet-bin
pkgver=1.0
pkgrel=2
pkgdesc="Puzzle Moppet is a serenely peaceful yet devilishly challenging 3D puzzle game.Precompiled Version"
source=("http://garnetgames.com/PuzzleMoppetFull.tar.gz")
md5sums=('e61d71a36367e8018c542ba2ac6e6d34')
license=('WTFPL 2.0')
url="http://garnetgames.com/puzzlemoppet/"
arch=('i686' 'x86_64')
depends=('libxrandr')

build() {
cat > puzzle-moppet.desktop << "EOF"
[Desktop Entry]
Name=Puzzle Moppet
Comment=3D block shifting puzzle game.
Terminal=false
Type=Application
Categories=Game;LogicGame;
Icon=/usr/share/puzzle-moppet/icons/main.png
Exec=/usr/share/puzzle-moppet/bin/PuzzleGame
Path=/usr/share/puzzle-moppet/bin
EOF

cat > puzzle-moppet-config.desktop << "EOF"
[Desktop Entry]
Name=Puzzle Moppet Settings
Comment=Configuration utility for Puzzle Moppet
Terminal=false
Type=Application
Categories=Game;LogicGame;
Icon=/usr/share/puzzle-moppet/icons/config.png
Exec=/usr/share/puzzle-moppet/bin/config
Path=/usr/share/puzzle-moppet/bin
EOF

cat > puzzle-moppet << "EOF"
#!/bin/bash
cd /usr/share/puzzle-moppet/bin
./PuzzleGame
EOF

cat > puzzle-moppet-config << "EOF"
#!/bin/bash
cd /usr/share/puzzle-moppet/bin
./config
EOF

}

package() {
install -d "${pkgdir}/usr/share/puzzle-moppet/bin"
install -Dm755 "${srcdir}/PuzzleMoppetFullVersion/bin/config" "${pkgdir}/usr/share/puzzle-moppet/bin"
install -Dm644 "${srcdir}/PuzzleMoppetFullVersion/bin/libalut.so.0" "${pkgdir}/usr/share/puzzle-moppet/bin"
install -Dm644 "${srcdir}/PuzzleMoppetFullVersion/bin/libopenal.so.1" "${pkgdir}/usr/share/puzzle-moppet/bin"
install -Dm755 "${srcdir}/PuzzleMoppetFullVersion/bin/PuzzleGame" "${pkgdir}/usr/share/puzzle-moppet/bin"

install -d "${pkgdir}/usr/bin"
install -Dm755 "${srcdir}/puzzle-moppet" "${pkgdir}/usr/bin/"
install -Dm755 "${srcdir}/puzzle-moppet-config" "${pkgdir}/usr/bin/"

install -d "${pkgdir}/usr/share/puzzle-moppet/icons"
install -Dm664 "${srcdir}/PuzzleMoppetFullVersion/icons/main.png" "${pkgdir}/usr/share/puzzle-moppet/icons"
install -Dm664 "${srcdir}/PuzzleMoppetFullVersion/icons/config.png" "${pkgdir}/usr/share/puzzle-moppet/icons"

cp -R ${srcdir}/PuzzleMoppetFullVersion/{licenses,projects} ${pkgdir}/usr/share/puzzle-moppet/.

install -d "${pkgdir}/usr/share/applications/"
cp *.desktop ${pkgdir}/usr/share/applications/
}

