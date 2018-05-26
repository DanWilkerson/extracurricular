# [Tries: Contacts (hackerrank.com)](https://www.hackerrank.com/challenges/ctci-contacts/problem) 

## Challenge Text

We're going to make our own Contacts application! The application must perform two types of operations:

add name, where  is a string denoting a contact name. This must store  as a new contact in the application.
find partial, where  is a string denoting a partial name to search the application for. It must count the number of contacts starting with  and print the count on a new line.
Given  sequential add and find operations, perform each operation in order.

## Solution

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

class Node {
        
    public Map<Character, Node> children = new HashMap<>();
    public int count = 1;
    
    // constructor
    public Node() {}
    
}

class Trie {
    
    private Node root = new Node();

    public void add(String str) {
        
        Node node = root;
        char l;
        
        for (int i = 0; i < str.length(); i++) {
            
            l = str.charAt(i);

            if (node.children.containsKey(l)) {

                node = node.children.get(l);
                node.count++;

            } else {

                node.children.put(l, new Node());
                node = node.children.get(l);

            }
            
        }

    }
    
    public int getCount(String str) {
           
        Node node = root;
        char l;
        
        for (int i = 0; i < str.length(); i++) {
            
            l = str.charAt(i);
            if (node.children.containsKey(l)) {

                node = node.children.get(l);

            } else {

                return 0;

            }
            
        }
        
        return node.count;
        
    }

}

public class Solution {

    
    public static void main(String[] args) {
        Trie trie = new Trie();
        
        Scanner in = new Scanner(System.in);
        int n = in.nextInt();
        for(int a0 = 0; a0 < n; a0++){
            String op = in.next();
            String contact = in.next();

            switch(op) {
                case "add":
                    trie.add(contact);
                    break;
                case "find":
                    System.out.println(trie.getCount(contact));
                    break;
                default:
                    break;
            }
            
        }
    }
}
```

