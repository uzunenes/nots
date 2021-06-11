# How to use darknet library ?

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

## Test library
```
// test_darknet_library.c
#include <stdio.h>
#include <darknet.h>

int
main()
{
	cuda_set_device(0);
	
	printf("Test libdarknet \n");
	
	return 0;
}
```

```
$ gcc -Wall test_darknet_library.c -ldarknet -o test_darknet_library.out
$ ./test_darknet_library.out
```

