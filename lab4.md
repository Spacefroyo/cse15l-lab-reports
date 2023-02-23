# Lab Report 4

Remotely modifying a GitHub repository

## Step 4

<img width="535" alt="Screenshot 2023-02-23 at 11 12 27 AM" src="https://user-images.githubusercontent.com/44252902/221006898-997f7f0d-c2ba-4ebc-8d58-761f5a0ee67b.png">

Keys pressed: ```<up><enter>```

The ```ssh cs15lwi23abm@ieng6.ucsd.edu``` command was the last locally executed command, so I used up arrow to access it.

This command signed me into my ieng6 account.

## Step 5

<img width="554" alt="Screenshot 2023-02-23 at 11 16 32 AM" src="https://user-images.githubusercontent.com/44252902/221008044-2e725080-0821-47c5-b176-2670259ae704.png">

Keys pressed: ```git clone <Cmd-V><enter>```

I had previously copied the ssh key of my repository, so ```<Cmd-V>``` pasted it into my terminal.

The ```git clone git@github.com:pygao-cse15l/lab7.git``` command cloned my repository into my ieng6 home directory in a folder called ```lab7```

## Step 6

<img width="965" alt="Screenshot 2023-02-23 at 11 20 21 AM" src="https://user-images.githubusercontent.com/44252902/221008770-32baa1c9-66a8-4342-ad70-afcc1570a970.png">

Keys pressed: ```cd l<tab>7<enter>```, ```<up><up><up><up><up><up><up><up><up><enter>```, ```<up><up><up><up><up><up><up><up><up><enter>```

The only folders in my ieng6 home directory that started with ```l``` were ones that began with ```lab```, so ```<tab>``` autofilled to ```lab```. 
I had to manually input the last character because there were multiple folders with that prefix.

The ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java``` command, which compiled my ```.java``` files, was 9 up in the search history, so I used up arrow to access it. 

Then the ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples``` command, which ran my tester file, was 9 up in the history, so I accessed and ran it in the same way.

## Step 7 (2 parts)

### Part 1

<img width="405" alt="Screenshot 2023-02-23 at 11 28 50 AM" src="https://user-images.githubusercontent.com/44252902/221010512-3e89ec51-8a0a-4618-98b9-cf39e9eb2876.png">
<img width="1458" alt="Screenshot 2023-02-23 at 11 29 07 AM" src="https://user-images.githubusercontent.com/44252902/221010556-ca6ae4a4-b4f8-4dd5-8203-64e8297d9d94.png">

Keys pressed: ```nano L<tab>j<tab><enter>```

The only folders in ```lab7``` that started with ```L``` were ```ListExamples.java``` and ```ListExamples.class```, so the first ```<tab>``` 
autofilled to ```ListExamples.```, their common prefix. The second ```<tab>``` completed to ```ListExamples.java```, since it was the only one that
started with ```ListExamples.j```. 

The ```nano``` command which took this as an input allowed me to edit ```ListExamples.java``` in ```nano```.

### Part 2

<img width="1454" alt="Screenshot 2023-02-23 at 11 34 50 AM" src="https://user-images.githubusercontent.com/44252902/221011656-310a9000-8920-4590-895b-02cb92911482.png">

Keys pressed: ```<Ctrl-W>0, s<enter>```, ```<right><right><right><delete><delete><delete>```, 
```<Ctrl-W>e(index2<enter>```, ```<down><down><right><right><right><right><delete>2```, 
```<Ctrl-W><enter>```, ```<Ctrl-X>```

The first error was prepending instead of appending ```s``` to ```result``` in the ```filter``` method. 
I found the location of the prepend by searching for ```0, s``` using the ```Where Is``` command operated by ```<Ctrl-W>```.
I then deleted the ```0, ``` part to make it add to the end rather than the start of ```result```.

The second error was incrementing ```index1``` rather than ```index2``` when adding the remaining elements of ```list2``` to ```result``` in the ```merge``` method.
I found the location of the loop by searching for ```e(index2``` using the ```Where Is``` command operated by ```<Ctrl-W>```.
I then navigated to the end of the incorrect ```index1``` in that loop by using ```<down><down><right><right><right><right>```,
and replaced the ```1``` with a ```2``` to correct the variable being incremented to ```index2```.

Lastly, I saved the new edits with ```<Ctrl-W><enter>``` and exited ```nano``` with ```<Ctrl-X>```.

## Step 8

<img width="958" alt="Screenshot 2023-02-23 at 11 42 16 AM" src="https://user-images.githubusercontent.com/44252902/221013104-439a1326-b99f-4b28-bc3f-5aaaa9e77940.png">

Keys pressed: ```<up><up><enter>```, ```<up><up><enter>```

The ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java``` command, which compiled my ```.java``` files, was 2 up in the search history, so I used up arrow to access it. 

Then the ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples``` command, which ran my tester file,  was 2 up in the history, so I accessed and ran it in the same way.

## Step 9

<img width="498" alt="Screenshot 2023-02-23 at 11 48 24 AM" src="https://user-images.githubusercontent.com/44252902/221014336-f5b0a08a-d276-4079-babc-09a96b7fa1d8.png">

Keys pressed: ```git add L<tab>j<tab><enter>```, ```git commit -m "a"<enter>```, ```git push origin main<enter>```

The only folders in ```lab7``` that started with ```L``` were ```ListExamples.java``` and ```ListExamples.class```, so the first ```<tab>``` 
autofilled to ```ListExamples.```, their common prefix. The second ```<tab>``` completed to ```ListExamples.java```, since it was the only one that
started with ```ListExamples.j```.

The ```add``` command added ```ListExamples.java``` to the list of files whose edits to keep.

The ```commit``` command saved these changes on my ieng6 clone of the repository.

The ```push``` command pushed these changes to the GitHub repository itself.

I typed in the ```commit``` and ```push``` commands by hand because I kept missing them with up arrow during practice and found this to be faster.
