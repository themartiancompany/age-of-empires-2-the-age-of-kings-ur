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

_uuid="SLES-50282"
_app_id="com.ensemblestudios.AgeOfEmpiresIITheAgeOfKings"
_title="Age Of Empires II: The Age of Kings"
_rom_filename="Age of Empires II - The Age of Kings (Europe) (En,Fr,De,Es,It) (v2.00)"
pkgname=age-of-empires-2-the-age-of-kings
pkgver=1.0
pkgrel=1
_pkgdesc=(
  "Real-time strategy video game"
  "developed by Ensemble Studios"
  "and published by Microsoft"
)
arch=(
  'any'
)
url="https://it.wikipedia.org/wiki/${_title}"
depends=(
  'pcsx2'
)
makedepends=(
  'bchunk'
  'p7zip'
)
license=(
  "custom"
)
_iso_sum=""
source=(
  "${_uuid}.bin::https://archive.org/download/age-of-empires-ii-the-age-of-kings-europe-en-fr-de-es-it-v-2.00.-7z/Age%20of%20Empires%20II%20-%20The%20Age%20of%20Kings%20%28Europe%29%20%28En%2CFr%2CDe%2CEs%2CIt%29%20%28v2.00%29.7z/Age%20of%20Empires%20II%20-%20The%20Age%20of%20Kings%20%28Europe%29%20%28En%2CFr%2CDe%2CEs%2CIt%29%20%28v2.00%29.bin"
  "${_uuid}.cue"
  "ps2-template.desktop"
  "${_app_id}.png::https://upload.wikimedia.org/wikipedia/en/5/56/Age_of_Empires_II_-_The_Age_of_Kings_Coverart.png"
)
sha256sums=(
  "9bb74ac0c02a18b3aab121e3ae83395bc306ef3edf70fc809348262e2021c908"
  "1312e0bcec587cea0737a320627b88295a12efcbbcc66541a7b78887b30ba29e"
  "dca9cf8e0064abaaf09666951a105c7697ba5cd377a3d11070338ef5ad7f08ee"
  "92dc96bfa14916b8faca4443806fffafed7fd15071bd774710be5f8037939902"
)

prepare() {
  mv ps2-template.desktop "${_app_id}.desktop"
  sed -i "s/%_title%/${_title}/g" "${_app_id}.desktop"
  sed -i "s/%pkgdesc%/${pkgdesc}/g" "${_app_id}.desktop"
  sed -i "s/%_app_id%/${_app_id}/g" "${_app_id}.desktop"
  sed -i "s/%_uuid%/${_uuid}/g" "${_app_id}.desktop"
  
  sed -i -e "s/${_rom_filename}/${_uuid}/g" "${_uuid}.cue"
  bchunk "${_uuid}.bin" "${_uuid}.cue" "${_uuid}"
  mv "${_uuid}01.iso" "${_uuid}.iso"
}

package() {
  local \
    _game="${pkgdir}/usr/games/${_app_id}"
  install \
    -vDm644 \
    "${_uuid}.iso" \
    "${_game}/${_uuid}.iso"
  install \
    -vDm755 \
    "${_app_id}.desktop" \
    "${pkgdir}/usr/share/applications/${_app_id}.desktop"
  install \
    -vDm644 \
    "${_app_id}.png" \
    "${pkgdir}/usr/share/icons/${_app_id}.png"
}
