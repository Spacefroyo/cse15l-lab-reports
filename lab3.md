# Lab Report 3

Researching the ```find``` command. This command finds all files and directories matching a specified criteria within the given directory. 
The following are flags that specify that criteria.

## Empty

Finds all files/directories that are empty. This is useful in case a program that was supposed to overwrite a 
bunch of files didn't run properly and erased the files instead of overwriting them. For example, a ```PrintWriter``` was initialized
but the program ran into an error before using it.

Example 1:

Before adding empty files/directories to the folder

```find . -empty```

```
```

Example 2:

After adding empty files/directories to the folder

```find . -empty```

```
./non-fiction/OUP/Empty1.txt
./non-fiction/OUP/Rybczynski/Empty3.ipynb
./non-fiction/OUP/Rybczynski/Empty4
./Empty2.java
```

## Type

Finds all files/directories of a specified type. This is useful for just finding directories or just finding files
in case you wanted to do some operation that is only applicable to a specific type.

Example 1:

```find non-fiction -type d```

```
non-fiction
non-fiction/OUP
non-fiction/OUP/Berk
non-fiction/OUP/Abernathy
non-fiction/OUP/Rybczynski
non-fiction/OUP/Kauffman
non-fiction/OUP/Fletcher
non-fiction/OUP/Castro
```

Example 2:

```find non-fiction/OUP/Berk -type f```

```
non-fiction/OUP/Berk/ch2.txt
non-fiction/OUP/Berk/ch1.txt
non-fiction/OUP/Berk/CH4.txt
non-fiction/OUP/Berk/ch7.txt
```

## Max Depth

Finds all files/directories within a certain depth. This is useful for only finding the 'shallower' files/directories instead of
recursing all the way to the bottom. For example, you might only want to know the things that are immediately in the Desktop folder
instead of everything within those folders.

Example 1:

```find . -maxdepth 2```

```
.
./non-fiction
./non-fiction/OUP
./travel_guides
./travel_guides/berlitz1
./travel_guides/berlitz2
```

Example 2:

```find non-fiction/OUP -maxdepth 1```

```
non-fiction/OUP
non-fiction/OUP/Berk
non-fiction/OUP/Abernathy
non-fiction/OUP/Rybczynski
non-fiction/OUP/Kauffman
non-fiction/OUP/Fletcher
non-fiction/OUP/Castro
```

## Case-Insensitive Name

Finds all files/directories matching a given name, just like the -name flag, but is case insensitive. This is useful for finding files/directories
where you remember the name but aren't sure about the capitalization.

Example 1:

```find . -iname "wheretoindia.txt"```

```
./travel_guides/berlitz1/WhereToIndia.txt
```

Example 2:

```find . -iname "ch4.txt"```

```
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Kauffman/ch4.txt
```
