-----------------------------------------------------------------------------
### Requirements: ###
Xcode: 7.2.1
tvOS 9.1 SDK

-----------------------------------------------------------------------------
**1. Getting the source code**
-----------------------------------------------------------------------------
    cd $HOME
    git clone --depth 1 -b yab git://github.com/Memphiz/xbmc.git Kodi

-----------------------------------------------------------------------------
**2. Install Kodi build depends & binary addons**
-----------------------------------------------------------------------------
 The following commands will build using the latest iOS SDK found on your
 system.

    cd $HOME/Kodi
    cd tools/depends
    ./bootstrap
    ./configure --host=arm-apple-darwin --with-cpu=arm64 --with-platform=tvos
    make -j$(getconf _NPROCESSORS_ONLN)
    make -C target/binary-addons


NOTE: if you only want to build specific addons you can specify like this:

    make -C target/binary-addons ADDONS="pvr.hts pvr.dvblink"

-----------------------------------------------------------------------------
**3. How to compile**
-----------------------------------------------------------------------------
    cd $HOME/Kodi
    make -C tools/depends/target/xbmc
    make clean
    make xcode_depends

-----------------------------------------------------------------------------
**4. Using Terminal (command-line)**
-----------------------------------------------------------------------------

    cd $HOME/Kodi
    xcodebuild -project Kodi.xcodeproj -target Kodi-TVOS -configuration Release build \ ONLY_ACTIVE_ARCH=YES ARCHS=arm64 VALID_ARCHS=arm64

-----------------------------------------------------------------------------
**5. Build Path & Code Sign**
-----------------------------------------------------------------------------

    /Users/*you*/Kodi/build/Release-appletvos

NOTE: Code Sign it with [https://dantheman827.github.io/ios-app-signer/](https://dantheman827.github.io/ios-app-signer/)
