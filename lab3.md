# Lab Report 3

Researching the ```find``` command

## Empty

Finds all files/directories that are empty. This is useful in case a program that was supposed to overwrite a 
bunch of files didn't run properly and erased the files instead of overwriting them. For example, a ```PrintWriter``` was initialized
but the program ran into an error before using it.

## Type

Finds all files/directories of a specified type. This is useful for just finding directories or just finding files
in case you wanted to do some operation that is only applicable to a specific type.

## Depth

Finds all files/directories within a certain depth. This is useful for only finding the 'shallow' files/directories instead of
recursing all the way to the bottom. For example, you might only want to know the things that are immediately in the Desktop folder
instead of everything within those folders.

## Iname

Finds all files/directories matching a given name, just like the -name flag, but is case insensitive. This is useful for finding files/directories
where you remember the name but aren't sure about the capitalization.
