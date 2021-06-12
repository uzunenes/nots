
# Project template creation guidelines


## create a new repository on github
Choose only a license (MIT) file.


## clone repository
```
$ git clone https://github.com/uzunenes/sradio
$ cd sradio/
```


## rename License
```
$ mv LICENSE License
$ git add LICENSE License 
$ git commit -m "renamed"
```


## add readme file
```
$ touch Readme.md
$ git add Readme.md
$ git commit -m "created and added"
```


## add .gitignore file
```
$ echo "*.o" >> .gitignore
$ echo "*.out" >> .gitignore
$ echo "*.so" >> .gitignore
$ echo "*.pc" >> .gitignore
$ echo "./obj" >> .gitignore
$ git add .gitignore
$ git commit -m "created and added"
```


## add source and include folders
```
$ mkdir src include
$ git add src/ include/
$ git commit -m "created and added"
```


- include/Version.h
```
#ifndef VERSION_H
#define VERSION_H

#define Version "0.1"

#endif // VERSION_H
```

- src/main.c
```
#include <stdio.h>
#include "../include/Version.h"

int
main(int argc, char** argv)
{
        printf("[%s] started, Version: [%s] \n", argv[0], Version);

        return 0;
}
```

```
$ git add src/main.c include/Version.h
$ git commit -m "created and added"
```


## add Makefile
```
PROJECT_NAME = sradio 
CC = gcc
CPP = g++
CFLAGS = -Wall -Wextra -O3

OBJCC = $(patsubst src/%.c, obj/%.o, $(wildcard src/*c))
OBJCPP = $(patsubst src/%.cpp, obj/%.o, $(wildcard src/*cpp))

LDFLAGS +=
CFLAGS +=


all: obj $(PROJECT_NAME)


$(PROJECT_NAME): $(OBJCC) $(OBJCPP)
	$(CPP) $(OBJCC) $(OBJCPP) $(LDFLAGS) -o $(PROJECT_NAME).out


obj/%.o: src/%.c
	$(CC) -c $< $(CFLAGS) -o $@

obj/%.o: src/%.cpp
	$(CPP) -c $< $(CFLAGS) -o $@


obj:
	mkdir -p obj


clean:
	rm -f *.out obj/*.o
```
```
$ git add Makefile
$ git commit -m "created and added"
```

## test repo
```
$ make
$ ./sradio.out
```
