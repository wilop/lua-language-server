pkgname=lua-language-server
pkgver=3.18.0
pkgrel=1
pkgdesc='A language server that offers Lua language support'
arch=('x86_64')
url='https://luals.github.io/'
license=('MIT')
depends=(lua)

source=("https://github.com/LuaLS/${pkgname}/releases/download/${pkgver}/${pkgname}-${pkgver}-linux-x64.tar.gz")

sha256sums=('21ddc896959f1ea60fa37562535774ec32a23c2cb1e01953a6bb3567a2f8162a')

prepare(){
cat <<EOF > "${pkgname}"
#!/bin/bash
exec "/usr/lib/${pkgname}/bin/${pkgname}" \\
"/usr/lib/${pkgname}/bin/main.lua" \\
--logpath="\$HOME/.cache/${pkgname}/log" \\
--metapath="\$HOME/.cache/${pkgname}/meta" \\
"\$@"
EOF
}

package() {
    install -Dm755 "${srcdir}/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
    install -dm755 "$pkgdir/usr/lib/${pkgname}"
    cp -r "$srcdir/bin" "${pkgdir}/usr/lib/${pkgname}/"
    cp -r "$srcdir/locale" "${pkgdir}/usr/lib/${pkgname}/"
    cp -r "$srcdir/meta" "${pkgdir}/usr/lib/${pkgname}/"
    cp -r "$srcdir/script" "${pkgdir}/usr/lib/${pkgname}/script"
    install -Dm644 "$srcdir/changelog.md" "${pkgdir}/usr/lib/${pkgname}/changelog.md"
    install -Dm644 "$srcdir/debugger.lua" "${pkgdir}/usr/lib/${pkgname}/debugger.lua"
    install -Dm644 "$srcdir/main.lua" "${pkgdir}/usr/lib/${pkgname}/main.lua"
    install -Dm644 "$srcdir/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
