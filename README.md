fifa
====

FreeImage For Android

The .mk files for android were created based on the steps explained at the below url http://recursify.com/blog/2013/05/25/building-freeimage-for-android.

Except step 3 in the above tutorial, i followed almost all of it. Below given changes are the differences in step 3 for this build.

    3a) Commented out `#define HAVE_SEARCH_H 1` as done in above.
    
    3b) Android NDK does provide (at least it does now, not sure if it was there before) bswap\_16 implementation in the header `#include <byteswap.h>` which you can find in the include folder of the corresponding android platform arch-arm folder.
    swab implementation from https://github.com/ajeet17181/mplayer-android(mplayer-android/osdep/swab.c) was used.
