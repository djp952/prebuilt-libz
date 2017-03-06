#LIBZ 1.2.11
[http://www.zlib.net/](http://www.zlib.net/)   
  
**TARGETS**   
* linux-i686 (gcc-4.9)   
* linux-x86_64 (gcc-4.9)   
* android-armeabi-v7a (ndk-r12b/api-21)   
* android-arm64-v8a (ndk-r12b/api-21)  
* android-x86 (ndk-r12b/api-21)   
   
**BUILD ENVIRONMENT**  
* Windows 10 x64 15025   
* Bash on Ubuntu on Windows 16.04.1 LTS   

**CONFIGURE BASH ON UBUNTU ON WINDOWS**   
Open "Bash on Ubuntu on Windows"   
```
sudo apt-get update
sudo apt-get install gcc g++ gcc-multilib g++-multilib gcc-4.9 g++-4.9 gcc-4.9-multilib g++-4.9-multilib
sudo apt-get install autoconf libtool make p7zip-full python
```

**CONFIGURE ANDROID TOOLCHAINS**   
Open "Bash on Ubuntu on Windows"   
```
wget https://dl.google.com/android/repository/android-ndk-r12b-linux-x86_64.zip
7z x android-ndk-r12b-linux-x86_64.zip
android-ndk-r12b/build/tools/make_standalone_toolchain.py --arch arm --api 21 --stl gnustl --install-dir ./arm-linux-androideabi
android-ndk-r12b/build/tools/make_standalone_toolchain.py --arch arm64 --api 21 --stl gnustl --install-dir ./aarch64-linux-android
android-ndk-r12b/build/tools/make_standalone_toolchain.py --arch x86 --api 21 --stl gnustl --install-dir ./i686-linux-android
```
  
**BUILD LIBZ (linux-i686)**   
Open "Bash on Ubuntu on Windows"   
```
git clone https://github.com/madler/zlib.git -b v1.2.11 --depth=1
export CC=gcc-4.9
export AR=gcc-ar-4.9
export RANLIB=gcc-ranlib-4.9
cd zlib
CFLAGS="-m32 -fPIC" ./configure --static
make
```
   
Get zlib.h, zconf.h and libz.a from zlib 
   
**BUILD LIBZ (linux-x86_64)**   
Open "Bash on Ubuntu on Windows"   
```
git clone https://github.com/madler/zlib.git -b v1.2.11 --depth=1
export CC=gcc-4.9
export AR=gcc-ar-4.9
export RANLIB=gcc-ranlib-4.9
cd zlib
CFLAGS=-fPIC ./configure --static
make
```
   
Get zlib.h, zconf.h and libz.a from zlib 
   
**BUILD LIBZ (android-armeabi-v7a)**   
Open "Bash on Ubuntu on Windows"   
```
git clone https://github.com/madler/zlib.git -b v1.2.11 --depth=1
export ANDROID_NDK_ROOT=$(pwd)/android-ndk-r12b
export PATH=$(pwd)/arm-linux-androideabi/bin:$PATH
export CROSS_COMPILE=arm-linux-androideabi-
export CC=arm-linux-androideabi-gcc
export AR=arm-linux-androideabi-ar
export RANLIB=arm-linux-androideabi-ranlib
cd zlib
./configure --static
make
```
   
Get zlib.h, zconf.h and libz.a from zlib 
   
**BUILD LIBZ (android-arm64-v8a)**   
Open "Bash on Ubuntu on Windows"   
```
git clone https://github.com/madler/zlib.git -b v1.2.11 --depth=1
export ANDROID_NDK_ROOT=$(pwd)/android-ndk-r12b
export PATH=$(pwd)/aarch64-linux-android/bin:$PATH
export CROSS_COMPILE=aarch64-linux-android-
export CC=aarch64-linux-android-gcc
export AR=aarch64-linux-android-ar
export RANLIB=aarch64-linux-android-ranlib
cd zlib
./configure --static
make
```
   
Get zlib.h, zconf.h and libz.a from zlib   
   
**BUILD LIBZ (android-x86)**   
Open "Bash on Ubuntu on Windows"   
```
git clone https://github.com/madler/zlib.git -b v1.2.11 --depth=1
export ANDROID_NDK_ROOT=$(pwd)/android-ndk-r12b
export PATH=$(pwd)/i686-linux-android/bin:$PATH
export CROSS_COMPILE=i686-linux-android-
export CC=i686-linux-android-gcc
export AR=i686-linux-android-ar
export RANLIB=i686-linux-android-ranlib
cd zlib
./configure --static
make
```
   
Get zlib.h, zconf.h and libz.a from zlib 
   