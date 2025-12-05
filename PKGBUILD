# Maintainer: Your Name <youremail@domain.com>
pkgname=isc-teaching-templates-git
_gitname=isc_teaching_templates
pkgver=0.0.2.r0.ga48f1f9 # This will be updated by the pkgver() function
pkgrel=1
pkgdesc="Templates and tools for creating exams, labs, and series for the ISC curriculum."
arch=('any')
url="https://github.com/MartTave/isc_teaching_templates"
license=('CC-BY-NC-SA-4.0')
depends=('texlive-binextra' 'texlive-xetex' 'texlive-latexrecommended' 'texlive-latexextra' 'texlive-fontsrecommended' 'texlive-fontsextra' 'parallel' 'texlive-bin')
makedepends=('git')

source=("git+${url}.git")
sha256sums=('SKIP')

pkgver() {
  cd "${_gitname}"
  git describe --long --tags | sed 's/^v//;s/-/.r/;s/-/./g'
}

build() {
  cd "${_gitname}"
  # Ensure build scripts are executable
  chmod -R +x build_tool/
}

package() {
  cd "${_gitname}"
  install -d "${pkgdir}/usr/share/${pkgname}"
  git archive HEAD | tar -x -C "${pkgdir}/usr/share/${pkgname}"

  install -d "${pkgdir}/usr/bin"
  ln -s "/usr/share/${pkgname}/build_tool/build_pandoc.sh" "${pkgdir}/usr/bin/isc-build-pandoc"
  ln -s "/usr/share/${pkgname}/build_tool/build_html.sh" "${pkgdir}/usr/bin/isc-build-html"
}
