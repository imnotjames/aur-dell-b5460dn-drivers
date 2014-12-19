# Contributor: Thomas Kinnen <thomas.kinnen@gmail.com>
pkgname=dell-b5460dn-drivers
provides="dell-b5460dn-drivers"
pkgdesc="Linux cups printer driver for Dell B5460dn Laser Printer"
url="http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=J74G7"
pkgver=1.0
pkgrel=1
arch=('i686' 'x86_64')
license=('custom')
depends=('cups')
makedepends=('rpmextract')
source=('http://downloads.dell.com/FOLDER01277951M/1/B5460_Linux_J74G7.zip')
md5sums=('dfce5586915eb9e7f8d4dfb9ffa6182d')

package() {
	rpmextract.sh $srcdir/B5460_Linux_J74G7/dell-PPD-Files-DKADP-$pkgver-1.$CARCH.rpm

	mkdir -p $srcdir/foomatic

	tar xf $srcdir/usr/local/dell/ppd/dell-PPD-Files-DKADP/foomatic/UTF-8/foomatic.tar -C $srcdir/foomatic
	
	mkdir -p $pkgdir/usr/share/cups/model
	cp $srcdir/usr/local/dell/ppd/dell-PPD-Files-DKADP/GlobalPPD_1.4/Dell_B5460dn_Laser_Printer.ppd $pkgdir/usr/share/cups/model/

	mkdir -p $pkgdir/usr/lib/cups/filter
	cp $srcdir/usr/local/dell/ppd/dell-PPD-Files-DKADP/GlobalPPD_1.4/fax-pnh-filter $pkgdir/usr/lib/cups/filter/

	mkdir -p $pkgdir/usr/share/foomatic/db/source/printer
	cp $srcdir/foomatic/printer/* $pkgdir/usr/share/foomatic/db/source/printer/

	mkdir -p $pkgdir/usr/share/foomatic/db/source/opt
	cp $srcdir/foomatic/opt/* $pkgdir/usr/share/foomatic/db/source/opt/
}

