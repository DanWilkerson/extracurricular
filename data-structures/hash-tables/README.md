# [Hash Tables: Ransom Note (hackerrank.com)](https://www.hackerrank.com/challenges/ctci-ransom-note/problem) 

## Challenge Text
A kidnapper wrote a ransom note but is worried it will be traced back to him. He found a magazine and wants to know if he can cut out whole words from it and use them to create an untraceable replica of his ransom note. The words in his note are case-sensitive and he must use whole words available in the magazine, meaning he cannot use substrings or concatenation to create the words he needs.

Given the words in the magazine and the words in the ransom note, print Yes if he can replicate his ransom note exactly using whole words from the magazine; otherwise, print No

## Solution

```java
import java.util.*;

public class Solution {
    
    private Map<String, Integer> magazineMap = new HashMap<String, Integer>();
    private Map<String, Integer> noteMap = new HashMap<String, Integer>();;

    public Solution(String[] magazine, String[] note) {

        Integer count;
                
        for (String word : magazine) {
            
            count = magazineMap.get(word);
            
            if (count == null) {
                
                count = 0;
                
            }
            
            magazineMap.put(word, count + 1);
            
        }
     
        for (String word : note) {
            
            count = noteMap.get(word);
            
            if (count == null) {
                
                count = 0;
                
            }
            
            noteMap.put(word, count + 1);

        }
                
    }
    
    public boolean solve() {
        
        Set<String> noteWords = noteMap.keySet();
        Integer match;
        
        for (String word : noteWords) {
 
            match = magazineMap.get(word);
            
            if (match == null || match < noteMap.get(word)) {
                
                return false;
                
            }
            
        }
        
        return true;
        
    }
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int m = scanner.nextInt();
        int n = scanner.nextInt();

        boolean answer;
        
        // Eat whitespace to beginning of next line
        scanner.nextLine();
        
        String[] magazine = scanner.nextLine().split("\\s");
        String[] note = scanner.nextLine().split("\\s");
        scanner.close();

        if (note.length > magazine.length) {
            
            System.out.println("No");
            return;
            
        }
        
        Solution s = new Solution(magazine, note);
        answer = s.solve();

        if(answer)
            System.out.println("Yes");
        else System.out.println("No");
      
    }
}
```
