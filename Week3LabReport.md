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
### Using `/add-message`
1. <img width="711" alt="image" src="https://user-images.githubusercontent.com/110417501/215378128-894f2c07-c8d4-4312-8aa2-fa6181f699b0.png">


