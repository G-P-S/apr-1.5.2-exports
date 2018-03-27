# apr-1.5.2-exports

Prebuilt binaries for Apache apr-1.5.2

## Linux
TBD

## Win
TBD

## Mac

to make fat libararies for apache apr
create individual 32bit and 64bit libs, then combine
when I tried the other techniques (e.g., ```CC="gcc -arch i386 -arch x86_64```)
I ran into troubles with the C preprocessor (which for some stupid reason
needs to be explicitly called to compile apr)

```
cd apr
git checkout 1.5.2
CC="gcc -arch i386" ./configure
make clean
make
rm -rf export32
mv .libs export32
./configure
make clean
make install
rm -rf export64
mv .libs export64
mkdir export
lipo -create export32/libapr-1.a export64/libapr-1.a -output export/libapr-1.a
lipo -info export/*.a
lipo -create export32/libapr-1.dylib export64/libapr-1.dylib -output export/libapr-1.dylib
file export/libapr-1.dylib 
```

## Arm A9S - release
./buildconf
CC=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-gcc CXX=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-g++ LD=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-ld CXXLD=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-ld STRIP=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-strip AR=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-ar AS=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-as NM=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-nm RANLIB=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-ranlib OBJDUMP=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-objdump ./configure --prefix=`pwd`/../apr-1.5.2-exports/linux-arm-a9s --host=arm-linux-gnueabi CFLAGS="-fPIC -pipe -mfpu=neon -funroll-loops -marm -march=armv7-a -mtune=cortex-a9"  \
ac_cv_file__dev_zero="yes" \
ac_cv_func_setpgrp_void="yes" \
apr_cv_process_shared_works="yes" \
apr_cv_mutex_robust_shared="no" \
apr_cv_tcp_nodelay_with_cork="yes" \
ac_cv_sizeof_struct_iovec="8" \
apr_cv_mutex_recursive="yes"

./libtool --mode=compile gcc -g -O2   -DHAVE_CONFIG_H  -DLINUX -D_REENTRANT -D_GNU_SOURCE   -I./include  -I./include/arch/unix -I./include/private  -o tools/gen_test_char.lo -c tools/gen_test_char.c && touch tools/gen_test_char.lo

./libtool --mode=link gcc -g -O2   -DHAVE_CONFIG_H  -DLINUX -D_REENTRANT -D_GNU_SOURCE   -I./include -I./include/arch/unix -I./include/private -no-install -o tools/gen_test_char tools/gen_test_char.lo    -lrt -lcrypt  -ldl

make
make install

## Arm A9S - debug
./buildconf
CC=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-gcc CXX=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-g++ LD=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-ld CXXLD=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-ld STRIP=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-strip AR=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-ar AS=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-as NM=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-nm RANLIB=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-ranlib OBJDUMP=/opt/BUILD_TOOLS/arm-a9s/bin/arm-linux-gnueabihf-objdump ./configure --prefix=`pwd`/../apr-1.5.2-exports/linux-arm-a9s-debug --host=arm-linux-gnueabi --enable-debug CFLAGS="-fPIC -pipe -mfpu=neon -funroll-loops -marm -march=armv7-a -mtune=cortex-a9"  \
ac_cv_file__dev_zero="yes" \
ac_cv_func_setpgrp_void="yes" \
apr_cv_process_shared_works="yes" \
apr_cv_mutex_robust_shared="no" \
apr_cv_tcp_nodelay_with_cork="yes" \
ac_cv_sizeof_struct_iovec="8" \
apr_cv_mutex_recursive="yes"

./libtool --mode=compile gcc -g -O2   -DHAVE_CONFIG_H  -DLINUX -D_REENTRANT -D_GNU_SOURCE   -I./include  -I./include/arch/unix -I./include/private  -o tools/gen_test_char.lo -c tools/gen_test_char.c && touch tools/gen_test_char.lo

./libtool --mode=link gcc -g -O2   -DHAVE_CONFIG_H  -DLINUX -D_REENTRANT -D_GNU_SOURCE   -I./include -I./include/arch/unix -I./include/private -no-install -o tools/gen_test_char tools/gen_test_char.lo    -lrt -lcrypt  -ldl

make
make install

## Arm ep - Chopes
```
./buildconf
CC=/root/CHP_SDK/cross_compile/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-gcc CXX=/root/CHP_SDK/cross_compile/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-g++ LD=/root/CHP_SDK/cross_compile/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-ld CXXLD=/root/CHP_SDK/cross_compile/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-ld STRIP=/root/CHP_SDK/cross_compile/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-strip AR=/root/CHP_SDK/cross_compile/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-ar AS=/root/CHP_SDK/cross_compile/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-as NM=/root/CHP_SDK/cross_compile/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-nm RANLIB=/root/CHP_SDK/cross_compile/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-ranlib OBJDUMP=/root/CHP_SDK/cross_compile/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-objdump ./configure --prefix=`pwd`/../apr-1.5.2-exports/linux-arm-ep --host=arm-poky-linux-gnueabi --with-sysroot=/root/CHP_SDK/sysroot CFLAGS="-fPIC -pipe -funroll-loops --sysroot=/root/CHP_SDK/sysroot"  \
ac_cv_file__dev_zero="yes" \
ac_cv_func_setpgrp_void="yes" \
apr_cv_process_shared_works="yes" \
apr_cv_mutex_robust_shared="no" \
apr_cv_tcp_nodelay_with_cork="yes" \
ac_cv_sizeof_struct_iovec="8" \
apr_cv_mutex_recursive="yes"

./libtool --mode=compile gcc -g -O2   -DHAVE_CONFIG_H  -DLINUX -D_REENTRANT -D_GNU_SOURCE   -I./include  -I./include/arch/unix -I./include/private  -o tools/gen_test_char.lo -c tools/gen_test_char.c && touch tools/gen_test_char.lo

./libtool --mode=link gcc -g -O2   -DHAVE_CONFIG_H  -DLINUX -D_REENTRANT -D_GNU_SOURCE   -I./include -I./include/arch/unix -I./include/private -no-install -o tools/gen_test_char tools/gen_test_char.lo    -lrt -lcrypt  -ldl

make
make install
```

## arm-a53 - Tasmania
```
./buildconf
CC=/opt/tas_sdk/sysroots/x86_64-linux/usr/bin/arm-oe-linux-gnueabi/arm-oe-linux-gnueabi-gcc CXX=/opt/tas_sdk/sysroots/x86_64-linux/usr/bin/arm-oe-linux-gnueabi/arm-oe-linux-gnueabi-g++ LD=/opt/tas_sdk/sysroots/x86_64-linux/usr/bin/arm-oe-linux-gnueabi/arm-oe-linux-gnueabi-ld CXXLD=/opt/tas_sdk/sysroots/x86_64-linux/usr/bin/arm-oe-linux-gnueabi/arm-oe-linux-gnueabi-ld STRIP=/opt/tas_sdk/sysroots/x86_64-linux/usr/bin/arm-oe-linux-gnueabi/arm-oe-linux-gnueabi-strip AR=/opt/tas_sdk/sysroots/x86_64-linux/usr/bin/arm-oe-linux-gnueabi/arm-oe-linux-gnueabi-ar AS=/opt/tas_sdk/sysroots/x86_64-linux/usr/bin/arm-oe-linux-gnueabi/arm-oe-linux-gnueabi-as NM=/opt/tas_sdk/sysroots/x86_64-linux/usr/bin/arm-oe-linux-gnueabi/arm-oe-linux-gnueabi-nm RANLIB=/opt/tas_sdk/sysroots/x86_64-linux/usr/bin/arm-oe-linux-gnueabi/arm-oe-linux-gnueabi-ranlib OBJDUMP=/opt/tas_sdk/sysroots/x86_64-linux/usr/bin/arm-oe-linux-gnueabi/arm-oe-linux-gnueabi-objdump ./configure --prefix=`pwd`/../apr-1.5.2-exports/linux-arm-a53 --host=arm-oe-linux-gnueabi --with-sysroot=/opt/tas_sdk/sysroots/apq8053-32 CFLAGS="-fPIC -pipe -funroll-loops --sysroot=/opt/tas_sdk/sysroots/apq8053-32"  \
ac_cv_file__dev_zero="yes" \
ac_cv_func_setpgrp_void="yes" \
apr_cv_process_shared_works="yes" \
apr_cv_mutex_robust_shared="no" \
apr_cv_tcp_nodelay_with_cork="yes" \
ac_cv_sizeof_struct_iovec="8" \
apr_cv_mutex_recursive="yes"

./libtool --mode=compile gcc -g -O2   -DHAVE_CONFIG_H  -DLINUX -D_REENTRANT -D_GNU_SOURCE   -I./include  -I./include/arch/unix -I./include/private  -o tools/gen_test_char.lo -c tools/gen_test_char.c && touch tools/gen_test_char.lo; 
./libtool --mode=link gcc -g -O2 -DHAVE_CONFIG_H -DLINUX -D_REENTRANT -D_GNU_SOURCE -I./include -I./include/arch/unix -I./include/private -no-install -o tools/gen_test_char tools/gen_test_char.lo -lrt -lcrypt  -ldl

make
make install
```

