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

# Maintainer:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer:
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

# shellcheck disable=SC2034
_os="$( \
  uname \
    -o)"
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
  _git="false"
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
pkgver=1.2.3
_commit="ebb6be35d133b071338a60a12b7c90eb28fe984b"
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
  "ffmpeg"
  "flac"
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
  "${_py}-appdirs"
  'shntool'
)
if [[ "${_os}" == "Android" ]]; then
  depends+=(
    "media-types"
  )
fi
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
_archive_sum="08ef52d93bfe6c8718adfdc9350b3ba686a684771dd47823256696e657e05c72"
_archive_sig_sum="54dbf23ad02f5e9e9a981366f232fbbde72c88e8bdf688ec96b5d32a0ec0544a"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
if [[ "${_evmfs}" == "true" ]]; then
  _tag="${_commit}"
elif [[ "${_git}" == "false" ]]; then
  _tag="${pkgver}"
fi
_tarname="${_pkg}-${_tag}"
_url="${url}"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_archive_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sum}"
_evmfs_archive_src="${_tarname}.tar.gz::${_evmfs_archive_uri}"
_archive_sig_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sig_sum}"
_archive_sig_src="${_tarname}.tar.gz.sig::${_archive_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  _src="${_evmfs_archive_src}"
  _sum="${_archive_sum}"
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
  _sum="SKIP"
fi
source=(
  "${_src}"
)
sha256sums=(
  "${_sum}"
)
validpgpkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

package_mkaudiocdrimg() {
  local \
    _make_opts=()
  cd \
    "${_tarname}"
  _make_opts=(
    DESTDIR="${pkgdir}"
  )
  "${_py}" \
    "setup.py" \
      install \
      --root="${pkgdir}" \
      --optimize=1
  make \
    "${_make_opts[@]}" \
    install-man
  install \
    -vDm644 \
    "COPYING" \
    "${pkgdir}/usr/share/licenses/${pkgname}"
}
