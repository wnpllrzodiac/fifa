fifa
====

FreeImage For Android (3.15.4 version)

Prerequisites
-------------

    Android NDK
    
    Tested it on 64-bit Arch Linux only.

Build steps
-----------

None at all.



Following changes are already done in the repo, so that you can just do `ndk-build` from the `$REPO_ROOT`(assuming this variable points to the location of the repository on your machine) and build the freeimage shared library for android.
    
1. Android.mk file is created based on the steps explained [here](http://recursify.com/blog/2013/05/25/building-freeimage-for-android)
 
2. `SRC=$REPO_ROOT/jni/Source`

3. Commented the line `#define HAVE_SEARCH_H 1` from file `$SRC/LibTIFF4/tif_config.h`
    
4. Included the header `#include <byteswap.h>` in `$SRC\LibRawLite\internal\dcraw_common.cpp`
       for swab_16 implementation.
    
5. Copied the swab implementation from https://github.com/ajeet17181/mplayer-android
       (mplayer-android/osdep/swab.c) in the file `$SRC\LibRawLite\internal\dcraw_common.cpp`
    
In case of any build errors related to android platform, make sure the file `$REPO_ROOT/jni/Application.mk` is indicating the correct platform number. You can do so by using the variable `APP_PLATFORM:=android-<platform number>`.

For any other errors, kindly let me know so that i can fix them.

To speedup the build process, you can use -j <#> option of ndk-build command.
For eg. `ndk-build -j 6`

License
-------
This repo contains freeimage source files and it is licensed under FIPL. You can find the license over [here](http://freeimage.sourceforge.net/freeimage-license.txt).
