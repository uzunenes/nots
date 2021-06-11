# How to use darknet so library ?

## Clone darknet repository
```
$ git clone https://github.com/AlexeyAB/darknet
```

## Make darknet
>Warning: Edit makefile flags
```
$ make
```

## Install files
```
$ cp include/darknet.h /usr/local/include
$ cp libdarknet.so /usr/local/lib
```

## Install pkgconfig file
```
$ echo "Name: libdarknet" >> libdarknet.pc
$ echo "Description: https://github.com/AlexeyAB/darknet" >> libdarknet.pc
$ echo "Libs: -L/usr/local/lib -ldarknet" >> libdarknet.pc
$ echo "Cflags: -I/usr/local/include" >> libdarknet.pc
$ cp libdarknet.pc /usr/local/lib/pkgconfig
```

## Configure linker
```
$ ldconfig
```
