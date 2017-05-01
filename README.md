-----------------------------------------------------------------------------
### Requirements: ###

Xcode: 7.2.1

-----------------------------------------------------------------------------
**1. Getting the source code**
-----------------------------------------------------------------------------
    
    cd $HOME
    git clone --depth 1 -b yab git://github.com/Memphiz/xbmc.git Kodi

-----------------------------------------------------------------------------
**2. Install Kodi build depends & binary addons**
-----------------------------------------------------------------------------
    
    cd $HOME/Kodi
    cd tools/depends
    ./bootstrap
    ./configure --host=arm-apple-darwin --with-cpu=arm64 --with-platform=tvos
    make -j$(getconf _NPROCESSORS_ONLN)
    make -C target/binary-addons

-----------------------------------------------------------------------------
**3. How to compile**
-----------------------------------------------------------------------------
    
    cd $HOME/Kodi
    make -C tools/depends/target/xbmc
    make clean
    make xcode_depends

-----------------------------------------------------------------------------
**4. Using Xcode**
-----------------------------------------------------------------------------

Go to Kodi folder located in home folder ($HOME/Kodi).<br>
Open Kodi.xcodeproj
<br>
Set target compilation as Kodi-TVOS > GenericTVOS<br>

Do changes for Target <b>Kodi-TVOS & TVOSTopShelf:</b><br>
Change Bundle Identifier to a unique name.<br>
Select your Team and Provisional Profile.

After all required fields are satisfied.<br>
Xcode Main Menu > Products > Clean > and then Build.

-----------------------------------------------------------------------------
**5. Using Terminal (command-line)**
-----------------------------------------------------------------------------

    cd $HOME/Kodi
    xcodebuild -project Kodi.xcodeproj -target Kodi-TVOS -configuration Release build \ ONLY_ACTIVE_ARCH=YES ARCHS=arm64 VALID_ARCHS=arm64

-----------------------------------------------------------------------------
**6. Build Path & Code Sign**
-----------------------------------------------------------------------------
This is the path when using Terminal Build
    /Users/*you*/Kodi/build/Release-appletvos
    
This is the path when using Xcode Build (to get Library folder- Hold Alt and navigate to finder GO)<br>
    /Users/***your name***/Library/Developer/Xcode/DerivedData/Kodi-xxxxxxxxxxxxx/Build/Products/Debug-appletvos/Kodi.app

NOTE: Code Sign it with [https://dantheman827.github.io/ios-app-signer/](https://dantheman827.github.io/ios-app-signer/)
