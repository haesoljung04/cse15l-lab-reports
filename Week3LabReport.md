# Week 2 Lab Report
*Servers and Bugs(Week 3)*
## Part 1. Writing a web server called `StringServer`
My code for `StringServer`:
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class StringServerHandler implements URLHandler {
    ArrayList<String> messages = new ArrayList<String>();
    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            messages.add(parameters[1]);
            return String.join("\n", messages); 
        }
        else {
            return "404 not Found";
        }
    }
}
class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new StringServerHandler());
    }
}
```
> NOTE: `Server.java` is a file that was provided to us in Week 2
### Using `/add-message`
1. <img width="711" alt="image" src="https://user-images.githubusercontent.com/110417501/215378128-894f2c07-c8d4-4312-8aa2-fa6181f699b0.png">
- The methods in my code that are called are as follows:
```
public String handleRequest(URI url) 
url.getPath()
equals()
url.getQuery()
split()
add()
String.join()
```
- The relevant argument is the URI url which is the full path of the url\(in this\
case that is `http://localhost:4325/add-message?s=sick`).\
and the values of the query(the part of the url after the "?") are "live",\
"4365," and "sick." These are all stored in the ArrayList called `messages`.
- Every request changes the value of the query and therfore appends an element\
to the ArrayList `messages`. 

2. <img width="707" alt="Screenshot 2023-01-29 at 7 24 30 PM" src="https://user-images.githubusercontent.com/110417501/215380950-aebe90fc-e7c8-4893-9e1c-6b4f2986d5db.png">
- The methods in my code that are called are as follows:
```
public String handleRequest(URI url)
url.getPath()
equals()
getQuery()
split()
add()
```
- The relevant argument is the URI url which is the full path of the url which is\
`http://localhost:4325/add-messages?s=` There are no relevant values because there\
is a lack of an input string which outputs the error:\
`java.lang.ArrayIndexOutOfBoundsException: Index 1 out of bounds for length 1`
- No values get changed because without a string it is impossible to `add` something\
that does not exist.

## Part 2. Analyzing a bug from Lab 3
The buggy program I will be analyzing is shown below:
```
// Changes the input array to be in reversed order
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
  arr[i] = arr[arr.length - i - 1];
  }
}
```
- A failure inducing input for the buggy program:
```
@Test
public void manualTestReverseInPlace() {
  int[] input2 = {1,2,3,4,5,6};
  ArrayExamples.reverseInPlace(input2);
  assertArrayEquals(new int[] {6,5,4,3,2,1}, input2);
}
```
- An input that doesn't induce a failure:
```
@Test 
public void testReverseInPlace() {
  int[] input1 = { 100 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 100 }, input1);
}
```
- The symptom, as the output of running the tests:
<img width="680" alt="image" src="https://user-images.githubusercontent.com/110417501/215382393-f73b287b-5f5d-48b3-abbe-ac031e594860.png">
- The code with the bug(before):
```static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
  arr[i] = arr[arr.length - i - 1];
  }
}```
- The fixed code(after):
```
static void reverseInPlace(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[i] = arr[arr.length - i - 1];
  }
  for(int j = 0; j < arr.length; j++) {
    arr[j] = newArray[j];
  }
}
```
The bug was that the original code used the same array to initialize itself\
which meant that when the index got past the middle of the array, it would\
inevitably initialize itself with the values not in reverse but from the values\
it already had. To fix this code I simply created a new array object and reversed\
the elementw into that array and then deep-copied it back into the input array.


