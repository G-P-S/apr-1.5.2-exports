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

