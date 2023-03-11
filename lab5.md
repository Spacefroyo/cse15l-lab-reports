# Lab Report 5

Researching the ```find``` command. This command looks through the input files and outputs all lines that contain a specified pattern.

Source: https://www.geeksforgeeks.org/grep-command-in-unixlinux/

## Count

Example 1:

Count number of lines in ```non-fiction/OUP/Abernathy/ch1.txt``` that mention book

Finds the number of lines in the given file that contain the string ```"book"```. 
This is useful for getting an idea of how many sentences of the text are devoted to discussing books (or some other arbitrary topic).

```grep -c book non-fiction/OUP/Abernathy/ch1.txt```

```
5
```

Example 2:

Count number of lines that mention book for each file of ```non-fiction/OUP/Abernathy/```

Finds the number of lines in the given files that contain the string ```"book"```. 
This is useful for getting an idea of which files in this directory are more focused on discussing books (or some other arbitrary topic).

```grep -c book non-fiction/OUP/Abernathy/*```

```
non-fiction/OUP/Abernathy/ch1.txt:5
non-fiction/OUP/Abernathy/ch14.txt:1
non-fiction/OUP/Abernathy/ch15.txt:4
non-fiction/OUP/Abernathy/ch2.txt:1
non-fiction/OUP/Abernathy/ch3.txt:0
non-fiction/OUP/Abernathy/ch6.txt:0
non-fiction/OUP/Abernathy/ch7.txt:0
non-fiction/OUP/Abernathy/ch8.txt:0
non-fiction/OUP/Abernathy/ch9.txt:0
```

## Filenames only

Example 1:

Print the names of the file ```non-fiction/OUP/Abernathy/ch1.txt``` if it mentions book at all

Prints the name of the file if it contains the string ```"book"```. 
This is useful for checking if this file talks about books (or some other arbitrary topic).

```grep -l book non-fiction/OUP/Abernathy/ch1.txt```

```
non-fiction/OUP/Abernathy/ch1.txt
```

Example 2:

Print the names of the files that mention book at all in ```non-fiction/OUP/Abernathy/```

Finds the names of the files that contain the string ```"book"```. 
This is useful for getting an idea of which files talk about books (or some other arbitrary topic).

```grep -c book non-fiction/OUP/Abernathy/*```

```
non-fiction/OUP/Abernathy/ch1.txt
non-fiction/OUP/Abernathy/ch14.txt
non-fiction/OUP/Abernathy/ch15.txt
non-fiction/OUP/Abernathy/ch2.txt
```

## Line number included

Example 1:

Print the lines in ```non-fiction/OUP/Abernathy/ch2.txt``` that mention book and their corresponding line numbers

Finds the lines in the given file that contain the string ```"book"``` and their line numbers. 
This is useful for finding which lines of the text are devoted to discussing books (or some other arbitrary topic) and navigating to them easily.

```grep -c book non-fiction/OUP/Abernathy/ch2.txt```

```
10:Alfred Chandler described the last industrial transformation in his well-known book The Visible Hand. The use of everything from railroads to an 
improved postal service, according to Chandler, created enterprises with internal administrative structures that coordinated the flow of goods from many 
individual producers to many more consumers. This administrative coordination reduced “the number of transactions involved in the flow of goods, 
increased the speed and regularity of that flow, and so lowered costs and improved the productivity of the American distribution system.”4
```

Example 2:

Print the lines in ```non-fiction/OUP/Abernathy/ch14.txt``` that mention book and their corresponding line numbers

Finds the lines in the given file that contain the string ```"book"``` and their line numbers. 
This is useful for finding which lines of the text are devoted to discussing books (or some other arbitrary topic) and navigating to them easily.

```grep -c book non-fiction/OUP/Abernathy/ch14.txt```

```
75:The implications of these changes do not end here. An economy consisting of lean retailing and corresponding “lean” suppliers operates in a 
fundamentally different manner from one based on traditional retailing and supply practices. The industrial transformation currently in progress 
encompasses international trade issues, competitiveness, labor regulation, and macroeconomic policies. Accordingly, the last chapter of this book is 
devoted to our reflections on the impact of channel integration on certain public policy issues.
```

## Context

Print the lines in ```non-fiction/OUP/Abernathy/ch2.txt``` that mention book and 1 line before.

Finds the lines in the given file that contain the string ```"book"``` and 1 line before.
This is useful for finding which lines of the text are devoted to discussing books (or some other arbitrary topic) and getting more context for them.

```grep -B 1 book non-fiction/OUP/Abernathy/ch2.txt```

```
In this chapter, we will concentrate on the past hundred years, outlining major changes in American retail, apparel, and textiles that occurred before the 1980s. The industrial transformation of this earlier period, which affected far more than these three industries, echoes today’s enormous shifts in supplier relations, manufacturing operations, and human resource practices. The changes now going on have their analog in the last century, when technological innovations of the day like railroads, telegraph, and steam power—developed for purposes far afield of retail, apparel, or textiles—helped transform the mass distri-bution of goods and information.

Alfred Chandler described the last industrial transformation in his well-known book The Visible Hand. The use of everything from railroads to an improved postal service, according to Chandler, created enterprises with internal administrative structures that coordinated the flow of goods from many individual producers to many more consumers. This administrative coordination reduced “the number of transactions involved in the flow of goods, increased the speed and regularity of that flow, and so lowered costs and improved the productivity of the American distribution system.”4
```

Example 2:

Print the lines in ```non-fiction/OUP/Abernathy/ch14.txt``` that mention book and 1 line before.

Finds the lines in the given file that contain the string ```"book"``` and 1 line before.
This is useful for finding which lines of the text are devoted to discussing books (or some other arbitrary topic) and getting more context for them.

```grep -B 1 book non-fiction/OUP/Abernathy/ch14.txt```

```
In fact, companies in myriad sectors are grappling with the same managerial challenges and opportunities of those in the American apparel and textile industries. Rethinking how to service stringent retail replenishment requirements for ever broadening product lines in more selling seasons has become a central business challenge.

The implications of these changes do not end here. An economy consisting of lean retailing and corresponding “lean” suppliers operates in a fundamentally different manner from one based on traditional retailing and supply practices. The industrial transformation currently in progress encompasses international trade issues, competitiveness, labor regulation, and macroeconomic policies. Accordingly, the last chapter of this book is devoted to our reflections on the impact of channel integration on certain public policy issues.
```
