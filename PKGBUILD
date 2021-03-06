# Maintainer: Tomasz Gąsior <tomaszgasior.pl>

# This file is based on original PKGBUILD of GTK3 package.
# https://git.archlinux.org/svntogit/packages.git/plain/trunk/PKGBUILD?h=packages/gtk3

__arch_pkg_commit="3313de611df4a2893692b70ca96e481c4d930df3"

pkgname=gtk3-mushrooms
pkgver=3.24.1
pkgrel=2
pkgdesc="GTK3 patched for classic desktops like XFCE or MATE. Please see README."
url="https://github.com/TomaszGasior/gtk3-mushrooms"
conflicts=(gtk3 gtk3-print-backends)
provides=(gtk3=$pkgver gtk3-classic=$pkgver gtk3-print-backends)
arch=(x86_64)
license=(LGPL)
depends=(
	atk cairo libxcursor libxinerama libxrandr libxi libepoxy gdk-pixbuf2
	libxcomposite libxdamage pango shared-mime-info at-spi2-atk wayland libxkbcommon
	json-glib librsvg wayland-protocols desktop-file-utils mesa gtk-update-icon-cache
)
makedepends=(
	gobject-introspection libcanberra gtk-doc sassc libcups
)
optdepends=(
	'libcups: printers in printing dialog'
	'dconf: default GSettings backend'
	'libcanberra: sounds events'
	'adwaita-icon-theme: default icon theme'
	'cantarell-fonts: default font'
)
source=(
	# Patch files.
	"appearance__buttons-menus-icons.patch"
	"appearance__disable-backdrop.patch"
	"appearance__file-chooser.patch"
	"appearance__message-dialogs.patch"
	"appearance__print-dialog.patch"
	"appearance__smaller-statusbar.patch"
	"csd__clean-headerbar.patch"
	"csd__disabled-by-default.patch"
	"csd__server-side-shadow.patch"
	"file-chooser__places-sidebar.patch"
	"file-chooser__typeahead.patch"
	"fixes__atk-bridge-errors.patch"
	"fixes__labels-wrapping.patch"
	"fixes__too-large-menu-covers-bar.patch"
	"fixes__trayicon-parent-relative.patch"
	"fixes__xfce-inhibit-errors.patch"
	"other__default-settings.patch"
	"other__hide-insert-emoji.patch"
	"other__mnemonics-delay.patch"
	"popovers__color-chooser.patch"
	"popovers__file-chooser-list.patch"
	"popovers__places-sidebar.patch"

	# Theme CSS stylesheet.
	"smaller-adwaita.css"

	# GTK source code.
	"https://download.gnome.org/sources/gtk+/${pkgver%.*}/gtk+-$pkgver.tar.xz"

	# Arch Linux package files.
	"settings.ini::https://git.archlinux.org/svntogit/packages.git/plain/trunk/settings.ini?h=packages/gtk3&id=$__arch_pkg_commit"
	"gtk-query-immodules-3.0.hook::https://git.archlinux.org/svntogit/packages.git/plain/trunk/gtk-query-immodules-3.0.hook?h=packages/gtk3&id=$__arch_pkg_commit"
)
sha256sums=(
	"68b26360764a2ea7e057a2aaa29c6fdfe164b9987866e038d8d0188a025477fb"
	"eade303471a5929ccf6cf14ff434deccb0da017d5c4fdce3f5a3ffa117c1c954"
	"86f48054a2df6319d97db14fd17ea15d50b32ea6ba594d83e8faa1596ec657ab"
	"54020144ac0472ae170297b4158da719b49860b17234bf54351ba30f793a7fe7"
	"be4ddf03a5cce8270e8118eb331b3056972c0bd490faa6e4a4ebe332ec4c2e91"
	"81138fbaff82e37a83da1c4aa074a6c708e6c50340e0ddeff3fb70e2a0b52e1f"
	"515ff6df72934aa4294cdb1befd6c542a187fe3b4326cda68a8541dabbe657fd"
	"63bf214d836f688e628b30d1743ff9e47deb64d0f4bde9f0eb9c352fc00ca8d4"
	"1508ddc7e682cdaace327ffe2955abe90f903cf7ec923892b85673a37f76a32f"
	"8271342e6a0394f70b6e5a21afb21e2e0b645edf39a0d149d5e8b4d6b062846d"
	"7b987cc9bd7ca9722bfb881b30b082c0d7409e3cd68592f5e7a1f401d73e7672"
	"99b12d7af7efc6a014e6afcab1ee82ea0feb0b5a4e9bbd663d1c45354cd34f2b"
	"7a604d453beb9c425b8ed4a60b5e9435c3f4ee10438490641c0ade448401306a"
	"21b8c90ceec02300affb5b30fecf390531cb76322faaf1dd01e2f1ca239ed729"
	"22ec5d9ee91b50775d7c5662fa683791a1da55d44c03790636552bdc16be7bbd"
	"40ea6615a9f9942e3a9ae52297c9f88a3fbbb70c8da9a559143d649414ab7076"
	"37e3278dd33542b706eb9e1db56997b194a7e2f1fd729a8511369387a74b22bd"
	"acd3babd22add981690728e84a89fb8bb332b7ac746e9db7cdb27c47f1ac0042"
	"c213812e1fafeb5565f7e329c4501195f04adcfe377b88439a6d51d478edc071"
	"7f3e5da1622e243243ea9b1e487460f608dc375e79d800d2f0d826fd30be68ed"
	"ef4fed3a364db8eb9c15c9ce0e733035722f168dc88b385df2178fc1168ada54"
	"2de68b575494d0d034accd7cd0ce881f366d5201a48496d8748c43f297836eac"
	"cae4474d2ef9b4b56316efe2b53d717188f3ef578d5513d1067ceaff87f2270d"
	"68387be307b99aadcdc653561d7a2a7f0113b93561fb18ded7075ec9ced5b02f"
	"01fc1d81dc82c4a052ac6e25bf9a04e7647267cc3017bc91f9ce3e63e5eb9202"
	"de46e5514ff39a7a65e01e485e874775ab1c0ad20b8e94ada43f4a6af1370845"
)

__patch_makefiles()
{
	__replace_string_in_file()
	{
		sed -i".bak" "s/$1/$2/" "$3"
		rm "$3.bak"
	}

	__replace_string_in_file \
		"SRC_SUBDIRS = gdk gtk libgail-util modules demos tests testsuite examples" \
		"SRC_SUBDIRS = gdk gtk libgail-util modules demos" \
		"Makefile.am"

	__replace_string_in_file \
		"SUBDIRS = po po-properties \$(SRC_SUBDIRS) docs m4macros build" \
		"SUBDIRS = po \$(SRC_SUBDIRS) m4macros build" \
		"Makefile.am"

	__replace_string_in_file \
		"SUBDIRS = gtk-demo widget-factory icon-browser" \
		"SUBDIRS = widget-factory" \
		"demos/Makefile.am"

	__replace_string_in_file \
		"gtk-update-icon-cache" \
		"" \
		"gtk/Makefile.am"
}

__patch_gtk_code()
{
	for patch_file in $srcdir/*.patch; do
		patch -p 2 -i "$patch_file"
	done

	cat "$srcdir/smaller-adwaita.css" | tee -a gtk/theme/Adwaita/gtk-contained{,-dark}.css > /dev/null
}

prepare()
{
	cd "$srcdir/gtk+-$pkgver"

	# Make building faster by skipping tests, code examples and unused elements.
	__patch_makefiles

	# Apply patches to GTK code.
	__patch_gtk_code

	NOCONFIGURE=1 ./autogen.sh
}

build()
{
	cd "$srcdir/gtk+-$pkgver"

	CXX=/bin/false ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var \
		--enable-x11-backend --enable-wayland-backend --enable-broadway-backend \
		--disable-cloudprint --enable-colord=no \
		--disable-schemas-compile --disable-gtk-doc-html

	# https://bugzilla.gnome.org/show_bug.cgi?id=655517
	sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool

	make
}

package()
{
	cd "$srcdir"

	DESTDIR="$pkgdir" make -C "gtk+-$pkgver" install

	install -Dt "$pkgdir/usr/share/gtk-3.0" -m644 settings.ini
	install -Dt "$pkgdir/usr/share/libalpm/hooks" -m644 gtk-query-immodules-3.0.hook
}
