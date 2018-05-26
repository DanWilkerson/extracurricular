# [Strings: Making Anagrams (hackerrank.com)](https://www.hackerrank.com/challenges/ctci-making-anagrams/problem) 

## Challenge Text
Alice is taking a cryptography class and finding anagrams to be very useful. We consider two strings to be anagrams of each other if the first string's letters can be rearranged to form the second string. In other words, both strings must contain the same exact letters in the same exact frequency For example, bacdc and dcbac are anagrams, but bacdc and dcbad are not.

Alice decides on an encryption scheme involving two large strings where encryption is dependent on the minimum number of character deletions required to make the two strings anagrams. Can you help her find this number?

Given two strings,  and , that may or may not be of the same length, determine the minimum number of character deletions required to make  and  anagrams. Any characters can be deleted from either of the strings.

## Solution

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;
public class Solution {
    public static int numberNeeded(String first, String second) {
        
        StringBuilder stringOne = new StringBuilder(first);
        StringBuilder stringTwo = new StringBuilder(second);

        int fullLen = first.length() + second.length();
        char c;
        String s;
        int i;

        // Option 1: sort, then take longer string and count deletions per character
        //   -- What about characters in string 2 but not one?
        // Option 2: combine the strings and count odds to equals?
        // Option 3: iterate through string one and delete matches, sum remainders
        for (i = stringOne.length() - 1; i >= 0; i--) {

            c = stringOne.charAt(i);
            s = c + "";
            // System.out.println(s);
            // System.out.println(stringTwo.indexOf(s));
            // System.out.println(i);
            if (stringTwo.indexOf(s) > -1) {

                stringOne.deleteCharAt(i);
                stringTwo.deleteCharAt(stringTwo.indexOf(s));

            }

        }

        return stringOne.length() + stringTwo.length();

    }
  
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        String a = in.next();
        String b = in.next();
        System.out.println(numberNeeded(b, a));
    }
}
```
