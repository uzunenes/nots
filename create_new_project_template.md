# Project template creation guidelines


- Create a new .git repository on github, gitlab vs.
	- Add only a license (MIT) file.


- Clone .git repository on local machine
	```
	$ git clone https://github.com/uzunenes/sradio
	$ cd sradio/
	```


- Rename License file
	```
	$ mv LICENSE License
	$ git add LICENSE License 
	$ git commit -m "renamed"
	```


- Add Readme file
	```
	$ touch Readme.md
	$ git add Readme.md
	$ git commit -m "created and added"
	```


- Add .gitignore file
	```
	$ echo "*.o" >> .gitignore
	$ echo "*.out" >> .gitignore
	$ echo "*.so" >> .gitignore
	$ echo "*.pc" >> .gitignore
	$ echo "./obj" >> .gitignore
	$ git add .gitignore
	$ git commit -m "created and added"
	```

- Add source and include folders
	```
	$ mkdir src/ include/
	$ git add src/ include/
	$ git commit -m "created and added"
	```
	- Create "include/Version.h" file
		```
		#ifndef VERSION_H
		#define VERSION_H

			#define Version "0.1"

		#endif // VERSION_H
		```

	- Create "src/main.c" file
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

	- Add .git
		```
		$ git add src/main.c include/Version.h
		$ git commit -m "created and added"
		```


- Create Makefile file
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

	- add .git
		```
		$ git add Makefile
		$ git commit -m "created and added"
		```

- Test repo
	```
	$ make
	$ ./sradio.out
	```
