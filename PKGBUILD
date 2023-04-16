# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>

pkgname=xiaomi-lavender-adaptation
provides=(halium9-post-install)
conflicts=(halium9-post-install)
pkgver=1$(date +%y%m%d)
pkgrel=1
pkgdesc="Manjaro libhybris adaptation for xiaomi lavender"
arch=('any')
url="https://github.com/manjaro-libhybris-devices/xiaomi-lavender-adaptation"
license=('GPL')
depends=('gzip' 'glibc-locales' 'wget' 'systemd')
makedepends=('git')
source=("xiaomi-lavender-adaptation::git+https://github.com/manjaro-libhybris-devices/xiaomi-lavender-adaptation.git")
install=$pkgname.install
md5sums=('SKIP')

package() {
    mv "${srcdir}/xiaomi-lavender-adaptation/xiaomi-lavender-adaptation.sh" "${srcdir}/xiaomi-lavender-adaptation/xiaomi-lavender-adaptation"

    mkdir -p "${pkgdir}/usr/bin/"
    install -Dm755 "${srcdir}/xiaomi-lavender-adaptation/xiaomi-lavender-adaptation" -t "${pkgdir}/usr/bin/"
    mkdir -p "${pkgdir}/usr/lib/systemd/system/"
    install -Dm644 "${srcdir}/xiaomi-lavender-adaptation/xiaomi-lavender-adaptation.service" -t "${pkgdir}/usr/lib/systemd/system/"
    mkdir -p "${pkgdir}/usr/lib/sysusers.d/"
    install -Dm644 "${srcdir}/xiaomi-lavender-adaptation/android.conf" -t "${pkgdir}/usr/lib/sysusers.d/"

    mkdir -p ${pkgdir}/etc/phosh/
    install -Dm644 "${srcdir}/xiaomi-lavender-adaptation/phoc.ini" -t "${pkgdir}/etc/phosh/"

    mkdir -p "${pkgdir}/etc/udev/rules.d/"
    cp -r "${srcdir}/xiaomi-lavender-adaptation/70-lavender.rules" -t "${pkgdir}/etc/udev/rules.d/"
    cp -r "${srcdir}/xiaomi-lavender-adaptation/90-backlight.rules" -t "${pkgdir}/etc/udev/rules.d/"

    mkdir -p "${pkgdir}/boot/"
    install -Dm644 "${srcdir}/xiaomi-lavender-adaptation/boot.img" -t "${pkgdir}/boot/"
    install -Dm644 "${srcdir}/xiaomi-lavender-adaptation/dtbo.img" -t "${pkgdir}/boot/"
    install -Dm644 "${srcdir}/xiaomi-lavender-adaptation/vbmeta.img" -t "${pkgdir}/boot/"

    mkdir -p "${pkgdir}/usr/lib/systemd/system/"
    install -Dm644 "${srcdir}/xiaomi-lavender-adaptation/brightness.service" "${pkgdir}/usr/lib/systemd/system/"

    mkdir -p "${pkgdir}/usr/share/glib-2.0/schemas/"
    install -Dm644 "${srcdir}/xiaomi-lavender-adaptation/90_manjaro.gschema.override" -t "${pkgdir}/usr/share/glib-2.0/schemas/"
}
