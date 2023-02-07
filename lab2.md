# Lab Report 2

## Part 1: Web Server

Code:

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String s = "";

    public String handleRequest(URI url) {
        if (!url.getPath().equals("/add-message")) {
            return "Invalid command: try /add-message";
        } 

        if (!url.getQuery().startsWith("s=")) {
            return "Invalid query: try ?s={STRING_TO_ADD}";
        }

        s += "\n" + url.getQuery().substring(2);
        return s.substring(1);
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

Example 1:

<img width="768" alt="Screenshot 2023-01-27 at 3 58 04 PM" src="https://user-images.githubusercontent.com/44252902/215227482-d7c0883d-d4b3-4aab-adf0-3ee91ff75737.png">

When I entered the url http://localhost:4002/add-message?s=first_stuff_added into my browser, the ```handleRequest()``` method of the ```Handler``` was called with the argument ```new URI("http://localhost:4002/add-message?s=first_stuff_added")```, which is essentially just the url I entered but formatted as a java ```URI```. This argument is named ```url``` within the scope of the ```handleRequest()``` method.

When the ```handleRequest()``` method is called, it first checks whether the ```path``` string of ```url``` is ```"/add-message"```. If it isn't, the error message ```"Invalid command: try /add-message"``` will be returned to signal that the input command is invalid. If it is, as is the case with this input, the method will continue executing.

Next, the method checks whether the ```query``` string of ```url``` starts with ```"s="```. If it doesn't, the error message ```"Invalid query: try ?s={STRING_TO_ADD}"``` will be returned to signal that the query must start with ```"s="```. If it does, as is the case with this input, the method will continue executing.

Finally, after the method has verified that both the ```path``` and ```query``` of ```url``` are valid, it will concatenate the given ```query``` substring. In effect, this just means concatenating a new line character (```"\n"```) and the part of the ```query``` string that comes after the ```"s="``` to the end of the instance variable ```s``` of the ```Handler```, which stores the concatenation of all input strings. In this case, since ```"first_stuff_added"``` was the part of the ```query``` string that came after the ```"s="```, the value of ```s``` goes from ```""``` (the value that it was assigned when the ```Handler``` was instantiated) to ```"\nfirst_stuff_added"```. The method will finally return the part of ```s``` that comes after the first character (the extraneous new line character), in this case ```"first_stuff_added"```.

Example 2:

<img width="744" alt="Screenshot 2023-01-27 at 3 58 36 PM" src="https://user-images.githubusercontent.com/44252902/215227525-01e4f4c0-c703-4919-9768-1041f80e9fbc.png">

When I entered the url http://localhost:4002/add-message?s=more_adding into my browser, the ```handleRequest()``` method of the ```Handler``` was called with the argument ```new URI("http://localhost:4002/add-message?s=more_adding")```, which is essentially just the url I entered but formatted as a java ```URI```. This argument is named ```url``` within the scope of the ```handleRequest()``` method.

When the ```handleRequest()``` method is called, it first checks whether the ```path``` string of ```url``` is ```"/add-message"```. If it isn't, the error message ```"Invalid command: try /add-message"``` will be returned to signal that the input command is invalid. If it is, as is the case with this input, the method will continue executing.

Next, the method checks whether the ```query``` string of ```url``` starts with ```"s="```. If it doesn't, the error message ```"Invalid query: try ?s={STRING_TO_ADD}"``` will be returned to signal that the query must start with ```"s="```. If it does, as is the case with this input, the method will continue executing.

Finally, after the method has verified that both the ```path``` and ```query``` of ```url``` are valid, it will concatenate the given ```query``` substring. In effect, this just means concatenating a new line character (```"\n"```) and the part of the ```query``` string that comes after the ```"s="``` to the end of the instance variable ```s``` of the ```Handler```, which stores the concatenation of all input strings. In this case, since ```"more_adding"``` was the part of the ```query``` string that came after the ```"s="```, the value of ```s``` goes from ```"\nfirst_stuff_added"``` (the value that it had after the previous request was processed) to ```"\nfirst_stuff_added\nmore_adding"```. The method will finally return the part of ```s``` that comes after the first character (the extraneous new line character), in this case ```"first_stuff_added\nmore_adding"```.

## Part 2: Bug

I chose the bug in the filter method.

Failure inducing input:
```
@Test
public void testFilter() {
    List<String> input1 = Arrays.asList("a", "b", "ab", "bcb");
    StringChecker input2 = new PalindromeChecker();

    assertArrayEquals(new String[]{"a", "b", "bcb"}, ListExamples.filter(input1, input2).toArray());
}
```

Non-failure inducing input:
```
@Test
public void testFilter2() {
    List<String> input1 = Arrays.asList("a", "ba", "aba", "ca", "a");
    StringChecker input2 = new PalindromeChecker();
    assertArrayEquals(new String[]{"a", "aba", "a"}, ListExamples.filter(input1, input2).toArray());
}
```

Symptom:

The output list had the right elements, but in reverse order.

<img width="1034" alt="Screenshot 2023-02-07 at 1 13 31 PM" src="https://user-images.githubusercontent.com/44252902/217366855-9bbd5278-b962-4117-bd4d-64429d979edc.png">

<img width="822" alt="Screenshot 2023-02-07 at 1 14 05 PM" src="https://user-images.githubusercontent.com/44252902/217366955-5071dd53-3f84-4024-92c9-bf0c9f0b86bf.png">

Bug:

The list prepended the elements that passed the filter, rather than appending them as intended.

Before

```
result.add(0, s);
```

After

```
result.add(s);
```

Using append rather than prepend fixes the error because since we loop through the original array in the forwards direction, we will encounter earlier elements before later elements, meaning any element that we want to add should come after all previously added elements.

## Part 3: Something I learned

One thing that I learned in lab 2 was that each port could only host 1 server on a machine. This means that a different port number must be used if someone wanted to host 2 different servers at once. It also means that using a port number that is currently in use will not successfully run the server as intended. I learned about this when we had conflicts because everyone tried to use port:4000.
