# Contributor: Swift Geek <swiftgeek «at» gmail.com>
pkgname=perl-module-extutils-cppguess
pkgver=0.07
pkgrel=1
pkgdesc="ExtUtils::CppGuess - guess C++ compiler and flags"
arch=('any')
url="http://search.cpan.org/dist/ExtUtils-CppGuess/"
license=('GPL' 'PerlArtistic')
depends=('perl>=5.10.0' 'perl-capture-tiny')
makedepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=(!emptydirs)
install=
source=("http://search.cpan.org/CPAN/authors/id/S/SM/SMUELLER/ExtUtils-CppGuess-${pkgver}.tar.gz")
md5sums=('350dd7c661189ea770d6c9354ebbc6c2')

build() {
  cd "$srcdir/ExtUtils-CppGuess-$pkgver"
  
  # Setting these env variables overwrites any command-line-options we don't want...
  export PERL_MM_USE_DEFAULT=1 PERL_AUTOINSTALL=--skipdeps \
    PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'" \
    PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
    MODULEBUILDRC=/dev/null

  # If using Makefile.PL
#  { /usr/bin/perl Makefile.PL &&
#    make &&
#    make test &&
#    make install; } || return 1

  # If using Build.PL
 { /usr/bin/perl Build.PL &&
   ./Build &&
   ./Build test &&
   ./Build install; } || return 1

  # remove perllocal.pod and .packlist
  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}
