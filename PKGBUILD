# Maintainer: xaque <xaque at 🦆 dot com>

# This package provides conveniences of having UE installed as a system pacakge without needing to track the actual engine files in the pacman db, leaving you in full control of your engine version or fork
# You must already have an Unreal Engine source build already on your system at the path below
_unrealroot="$HOME/Games/unreal-engine"

pkgname=unreal-engine-support
pkgver=5.0.3
pkgrel=1
pkgdesc="Support files for an untracked source build of Unreal Engine"
arch=('x86_64')
url='https://www.unrealengine.com/'
license=('custom')
conflicts=('unreal-engine' 'unreal-engine-4' 'unreal-engine-git' 'unreal-engine-bin')
depends=()
optdepends=('android-ndk: Android build support'
            'clion: CLion IDE support'
            'code: Visual Studio Code IDE support')
source=("unreal-engine.desktop")
sha256sums=("SKIP")

package() {
  # Symlink existing build to system paths
  mkdir -p "$pkgdir"/opt
  mkdir -p "$pkgdir"/usr/bin
  ln -s $_unrealroot "$pkgdir"/opt/unreal-engine
  ln -s $_unrealroot/Engine/Binaries/Linux/UnrealEditor "$pkgdir"/usr/bin/UnrealEditor

  # Install icons and desktop files
  install -Dm644 unreal-engine.desktop "$pkgdir"/usr/share/applications/unreal-engine.desktop
  pushd $_unrealroot/Engine/Source/Programs/UnrealVersionSelector/Private/Linux/Resources
    #install -Dm644 com.epicgames.UnrealEngine.desktop "$pkgdir"/usr/share/applications/com.epicgames.UnrealEngine.desktop
    #install -Dm644 com.epicgames.UnrealEngineEditor.desktop "$pkgdir"/usr/share/applications/com.epicgames.UnrealEngineEditor.desktop
    #install -Dm644 com.epicgames.UnrealVersionSelector.desktop "$pkgdir"/usr/share/applications/com.epicgames.UnrealVersionSelector.desktop
    install -Dm644 uproject.xml "$pkgdir"/usr/share/mime/packages/uproject.xml
    install -Dm644 Icon.png "$pkgdir"/usr/share/icons/hicolor/256x256/apps/ubinary.png
    mkdir -p "$pkgdir"/usr/share/icons/hicolor/256x256/mimetypes
    ln -s ../apps/ubinary.png "$pkgdir"/usr/share/icons/hicolor/256x256/mimetypes/uproject.png
  popd
}
