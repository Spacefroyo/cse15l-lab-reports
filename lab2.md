# Lab Report 2

## Part 2: Bug

I chose the bug in the filter method.

Failure inducing input:
```
@Test
public void testFilter() {
    List<String> input1 = Arrays.asList("a", "b");
    StringChecker input2 = new StringChecker() {
        public boolean checkString(String s) { return true; }
    };

    assertArrayEquals(new String[]{"a", "b"}, ListExamples.filter(input1, input2).toArray());
}
```

Non-failure inducing input:
```
@Test
public void testFilter2() {
    List<String> input1 = Arrays.asList("a", "a");
    StringChecker input2 = new StringChecker() {
        public boolean checkString(String s) { return true; }
    };

    assertArrayEquals(new String[]{"a", "a"}, ListExamples.filter(input1, input2).toArray());
}
```


<img width="1032" alt="Screenshot 2023-01-27 at 8 47 00 AM" src="https://user-images.githubusercontent.com/44252902/215144707-42599cb1-c96a-4744-b404-1f203530b054.png">

## Part 1: Simplest Search Engine

Code:
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    ArrayList<String> arr = new ArrayList<>();

    public String handleRequest(URI url) {
        String query = url.getQuery();
        if (query == null || !query.startsWith("s=")) return "Invalid Query!";
        query = query.substring(2);
        if (url.getPath().equals("/add")) {
            if (arr.contains(query)) return "String already in list";
            arr.add(query);
            return String.format("Added %s to list", query);
        } else if (url.getPath().equals("/search")) {
            StringBuilder ret = new StringBuilder("Superstrings in list: ");
            for (String s : arr) {
                if (s.contains(query)) ret.append(s + ", ");
            }
            return ret.length() == 22 ? ret.toString() + "None" : ret.toString().substring(0, ret.length()-2);
        } else {
            return "Unknown Command! Try /add or /search instead";
        }
    }
}

class SearchEngine {
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

*The string ```"apple"``` was added beforehand to show that multiple elements can be returned by the ```search``` operation*
### Add: ```http://localhost:4001/add?s=apples```

<img width="651" alt="Screenshot 2023-01-24 at 10 47 41 AM" src="https://user-images.githubusercontent.com/44252902/214381644-ec6b9b02-c2f5-4fcd-b1cf-18357ea9a59b.png">

When this ```URI``` is entered, the ```handleRequest()``` method of a ```Handler``` is called.

The ```URI```, with ```path="/add"``` and ```query="s=apples"```, is passed in as an argument, and the method recognizes this as an ```add``` operation, 
adding the query substring ```"apples"``` to the instance variable ```arr```

Through this operation, the value of ```arr``` changes from ```{"apple"}``` to ```{"apple", "apples"}```



### Invalid Query: ```http://localhost:4001/add?a=apples```

<img width="645" alt="Screenshot 2023-01-24 at 10 48 33 AM" src="https://user-images.githubusercontent.com/44252902/214381811-fdb35b7b-d13f-4162-b461-09d96b6b9aa8.png">

When this ```URI``` is entered, the ```handleRequest()``` method of a ```Handler``` is called.

The ```URI```, with ```path="/add"``` and ```query="a=apples"```, is passed in as an argument, and the method realizes that the query string is 
invalid because it doesn't start with ```"s="```

This causes the method to return ```"Invalid Query!"``` as the string to display without changing the value of any instance variables.



### Search: ```http://localhost:4001/search?s=ple```

<img width="638" alt="Screenshot 2023-01-24 at 10 50 10 AM" src="https://user-images.githubusercontent.com/44252902/214382172-65e1a293-cc48-4fd8-9701-ecc7979250b5.png">

When this ```URI``` is entered, the ```handleRequest()``` method of a ```Handler``` is called.

The ```URI```, with ```path="/search"``` and ```query="s=ple"```, is passed in as an argument, and the method recognizes this as an 
```search``` operation, searching through the instance variable ```arr``` to find and concatenate any strings containing the string ```"ple"```

The method then returns the concatenated string, without changing the value of any instance variables.
