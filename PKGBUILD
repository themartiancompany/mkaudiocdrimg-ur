# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2022, 2023, 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

# shellcheck disable=SC2034
_namespace="tallero"
_py="python"
_pkg=mkaudiocdrimg
pkgbase="${_pkg}"
_pkgname="${pkgbase}"
pkgname="${pkgbase}"
pkgver=1.2.1
pkgrel=1
_pkgdesc=(
  "Make an audio CD-R image"
  "from media files."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://gitlab.com"
_http="https://github.com"
_ns="tallero"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgbase}"
depends=(
  "${_py}"
  'ffmpeg'
  'shntool'
  "${_py}-appdirs"
)
makedepends=(
  'git'
  "${_py}-setuptools"
)
provides=(
  "${_py}-${_pkg}=${pkgver}"
)

conflicts=(
  "${_py}-${_pkg}"
)
license=(
  "AGPL3"
)
_tarname="${_pkg}-${pkgver}"
source=(
  "${_tarname}::git+${url}#tag=${pkgver}"
)
sha256sums=(
  "SKIP"
)

package() {
  cd \
    "${_tarname}"
  "${_py}" \
    "setup.py" \
      install \
        --root="${pkgdir}" \
	--optimize=1
}
