
# Project template creation guidelines

## creater a new repository
Choose only a license (MIT) file.

## clone repository
```
$ git clone https://github.com/uzunenes/test
$ cd test/
```

## add readme file
```
$ touch Readme.md
$ git add Readme.md
$ git commit -m "created and added file"
```

## add .gitignore file
```
$ echo "*.o" >> .gitignore
$ echo "*.out" >> .gitignore
$ echo "*.so" >> .gitignore
$ echo "*.pc" >> .gitignore
$ echo "./obj" >> .gitignore
$ git add .gitignore
$ git commit -m "created and added template file"
```

## readme files
```
mv LICENSE License
```

## add new folders
```
$ mkdir src
$ mkdir include
```

## add Makefile
```

```


