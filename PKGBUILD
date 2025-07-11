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
_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
if [[ ! -v "_git" ]]; then
  _git="true"
fi
_namespace="tallero"
_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=mkaudiocdrimg
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
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
_gl_http="https://gitlab.com"
_gh_http="https://github.com"
_gl_ns="tallero"
_gh_ns="themartiancompany"
_gh_url="${_gh_http}/${_gh_ns}/${_pkg}"
_gl_url="${_gl_http}/${_gl_ns}/${_pkg}"
url="${_gh_url}"
depends=(
  'ffmpeg'
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
  "${_py}-appdirs"
  'shntool'
)
makedepends=(
  "${_py}-setuptools"
)
if [[ "${_git}" == "true" ]]; then
  makedepends=(
    'git'
  )
fi
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
_url="${url}"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_archive_sum='7a55511d466126a07ac33ac26b6fd3c82bef9ff5016d48dbb66d6522e9e0d489'
_evmfs_archive_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sum}"
_evmfs_archive_src="${_tarname}.zip::${_evmfs_archive_uri}"
_archive_sig_sum="1b77bbebc4e78b4a72891c0f4b56e66d115bcdf6c07484707d7f827a4c2c8443"
_archive_sig_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sig_sum}"
_archive_sig_src="${_tarname}.zip.sig::${_archive_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_archive_src}"
  source+=(
    "${_archive_sig_src}"
  )
  sha256sums+=(
    "${_archive_sig_sum}"
  )
elif [[ "${_git}" == "true" ]]; then
  _uri="git+${_url}#tag=${pkgver}"
  _src="${_tarname}::${_uri}"
fi
source=(
  "${_src}"
)
sha256sums=(
  "SKIP"
)

package_mkaudiocdrimg() {
  cd \
    "${_tarname}"
  "${_py}" \
    "setup.py" \
      install \
        --root="${pkgdir}" \
	--optimize=1
}
