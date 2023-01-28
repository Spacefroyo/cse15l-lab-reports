# Lab Report 2

## Part 1: Web Server

Example 1:

<img width="768" alt="Screenshot 2023-01-27 at 3 58 04 PM" src="https://user-images.githubusercontent.com/44252902/215227482-d7c0883d-d4b3-4aab-adf0-3ee91ff75737.png">

Method called:

```
handleRequest()
```

Arguments:

```
url = new URI("http://localhost:4002/add-message?s=first_stuff_added")
```

Values changed:

The value of ```s``` changed from ```""``` to ```"first_stuff_added"```

Example 2:

<img width="744" alt="Screenshot 2023-01-27 at 3 58 36 PM" src="https://user-images.githubusercontent.com/44252902/215227525-01e4f4c0-c703-4919-9768-1041f80e9fbc.png">

Method called:

```
handleRequest()
```

Arguments:

```
url = new URI("http://localhost:4002/add-message?s=more_adding")
```

Values changed:

The value of ```s``` changed from ```"first_stuff_added"``` to ```"first_stuff_added\nmore_adding"```

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

Symptom:

The output list had the right elements, but in reverse order.

<img width="1033" alt="Screenshot 2023-01-27 at 4 07 20 PM" src="https://user-images.githubusercontent.com/44252902/215228242-ab559fe2-b973-4850-b691-f5971c1b4bb6.png">

<img width="1030" alt="Screenshot 2023-01-27 at 4 07 40 PM" src="https://user-images.githubusercontent.com/44252902/215228274-e0d741b2-5e76-4ae4-bd84-f9fbf94a65d3.png">

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

One thing that I learned in lab 2 was that each port could only host 1 server on a machine and a different port number must be used if someone wanted to host 2 different servers at once.
