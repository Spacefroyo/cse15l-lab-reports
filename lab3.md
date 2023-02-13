# Lab Report 3

Researching the ```find``` command. This command finds all files and directories matching a specified criteria within the given directory. 
The following are flags that specify that criteria.

Source: https://www.redhat.com/sysadmin/linux-find-command

## Empty

Example 1:

Before adding empty files/directories to the folder

Finds all files/directories that are empty. This is useful for checking whether there are any empty files/directories left over from experiments or 
files that were passed into a ```PrintWriter``` but the program didn't finish running properly.

```find . -empty```

```
```

Example 2:

After adding empty files/directories to the folder

Finds all files/directories that are empty. This is useful for finding the paths of all empty files/directories which might have been made
for experiments or demonstrations. It is also a good way of deleting all of them without doing so manually (pass the paths into a delete command).

```find . -empty```

```
./non-fiction/OUP/Empty1.txt
./non-fiction/OUP/Rybczynski/Empty3.ipynb
./non-fiction/OUP/Rybczynski/Empty4
./Empty2.java
```

## Type

Example 1:

Finds all directories in the non-fiction folder. This useful for checking only the directories (authors in thise case) rather than listing all the
texts as well.

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

Finds all files in the non-fiction folder. This is useful for just getting the files without getting the directories, which lets us do file-only
commands like ```cat``` on the list of paths.

```find non-fiction -type f```

```
non-fiction/OUP/Berk/ch2.txt
non-fiction/OUP/Berk/ch1.txt
non-fiction/OUP/Berk/CH4.txt
non-fiction/OUP/Berk/ch7.txt
non-fiction/OUP/Abernathy/ch2.txt
non-fiction/OUP/Abernathy/ch3.txt
non-fiction/OUP/Abernathy/ch1.txt
non-fiction/OUP/Abernathy/ch7.txt
non-fiction/OUP/Abernathy/ch6.txt
non-fiction/OUP/Abernathy/ch8.txt
non-fiction/OUP/Abernathy/ch9.txt
non-fiction/OUP/Abernathy/ch15.txt
non-fiction/OUP/Abernathy/ch14.txt
non-fiction/OUP/Rybczynski/ch2.txt
non-fiction/OUP/Rybczynski/ch3.txt
non-fiction/OUP/Rybczynski/ch1.txt
non-fiction/OUP/Kauffman/ch3.txt
non-fiction/OUP/Kauffman/ch1.txt
non-fiction/OUP/Kauffman/ch4.txt
non-fiction/OUP/Kauffman/ch5.txt
non-fiction/OUP/Kauffman/ch7.txt
non-fiction/OUP/Kauffman/ch6.txt
non-fiction/OUP/Kauffman/ch8.txt
non-fiction/OUP/Kauffman/ch9.txt
non-fiction/OUP/Kauffman/ch10.txt
non-fiction/OUP/Fletcher/ch2.txt
non-fiction/OUP/Fletcher/ch1.txt
non-fiction/OUP/Fletcher/ch5.txt
non-fiction/OUP/Fletcher/ch6.txt
non-fiction/OUP/Fletcher/ch9.txt
non-fiction/OUP/Fletcher/ch10.txt
non-fiction/OUP/Castro/chR.txt
non-fiction/OUP/Castro/chP.txt
non-fiction/OUP/Castro/chQ.txt
non-fiction/OUP/Castro/chB.txt
non-fiction/OUP/Castro/chC.txt
non-fiction/OUP/Castro/chA.txt
non-fiction/OUP/Castro/chV.txt
non-fiction/OUP/Castro/chW.txt
non-fiction/OUP/Castro/chM.txt
non-fiction/OUP/Castro/chZ.txt
non-fiction/OUP/Castro/chL.txt
non-fiction/OUP/Castro/chN.txt
non-fiction/OUP/Castro/chY.txt
non-fiction/OUP/Castro/chO.txt
```

## Max Depth

Example 1:

Finds all files/directories which are at most nested twice (including the working directory). This is useful for only looking at the 'shallower'
files/directories which are the main ones rather than worrying about all of the specific subdirectories and files.

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

Finds all files/directories which are immediately . This is useful for only looking at the 'shallower' files/directories which in this case are 
the authors without looking at all of their works.

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

Example 1:

Finds all files/directories with the specified name but case insensitive. This is useful for finding a file whose name you know but whose 
capitalization you don't.

```find . -iname "wheretoindia.txt"```

```
./travel_guides/berlitz1/WhereToIndia.txt
```

Example 2:

Finds all files/directories with the specified name but case insensitive. This is useful for finding all files that match the given name without
caring about capitalization (in this case I just want the 4th chapter of all the books and don't care if their file names were capitalized).

```find . -iname "ch4.txt"```

```
./non-fiction/OUP/Berk/CH4.txt
./non-fiction/OUP/Kauffman/ch4.txt
```
