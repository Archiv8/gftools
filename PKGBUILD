#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/fontfinder/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/fontfinder/discussions>

pkgname="gftools"
pkgver=0.9.10
pkgrel=1
pkgdesc="Miscellaneous tools for working with the Google Fonts library"
arch=(any)
url="https://github.com/googlefonts/$pkgname"
license=(
  "Apache"
)
depends=(
  "absl-py"
  "hyperglot"
  "python"
  "python-babelfont"
  "python-brotli"
  "python-browserstack-local"
  "python-fontfeatures"
  "python-fontmake"
  # optdepends of fonttols required for [ufo]
  "python-fonttools"
  "python-fs"

  "python-glyphslib"
  "python-glyphsets"
  "python-jinja"
  "python-opentype-sanitizer"
  "python-protobuf"
  "python-pyaml"
  "python-pybrowserstack-screenshots"
  "python-pygit2"
  "python-pygithub"
  "python-requests"
  "python-skia-pathops"
  "python-strictyaml"
  "python-tabulate"
  "python-ufolib2"
  "python-ttfautohint-py"
  "python-unidecode"
  "python-vttlib"
  "python-statmake"
)
makedepends=(
  "python-build"
  "python-installer"
  "python-setuptools-scm"
  "python-wheel"
)
_tarname="$pkgname-$pkgver"
source=(
  "https://files.pythonhosted.org/packages/source/${pkgname::1}/$pkgname/$_tarname.tar.gz"
)
sha512sums=(
  "31322198bccca26049ad01c61cd37b87dd9ea94df4d08a4930df689683ddc3a8577af9e552870f319675f1532913be0b5c437008652294df8a4d388497aa2a49"
)

prepare() {

  cd "$_tarname"

  sed -i -e "/setup_requires/s/>=.*'/'/" setup.py
}

build() {

  cd "$_tarname"

  python -m build -wn
}

package() {

  cd "$_tarname"

  python -m installer -d "$pkgdir" dist/*.whl
}
